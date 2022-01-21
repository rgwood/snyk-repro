# Snyk .NET repro

TestProject1 was created using the default XUnit test project template in Visual Studio 2022.

The only change I've made to it is adding  `<TargetLatestRuntimePatch>true</TargetLatestRuntimePatch>` to TestProject1.csproj, [as suggested by the Snyk docs](https://docs.snyk.io/products/snyk-open-source/language-and-package-manager-support/snyk-for-.net#tackling-vulnerabilities-from-runtime-dependencies).

### Steps to reproduce

1. `dotnet restore`
2. `snyk test --file=SnykRepro.sln`

```
Tested 93 dependencies for known issues, found 6 issues, 35 vulnerable paths.


Issues with no direct upgrade or patch:
  ✗ Denial of Service (DoS) [High Severity][https://snyk.io/vuln/SNYK-DOTNET-SYSTEMNETHTTP-60045] in System.Net.Http@4.3.0
    introduced by xunit@2.4.1 > xunit.assert@2.4.1 > NETStandard.Library@1.6.1 > System.Net.Http@4.3.0 and 3 other path(s)
  This issue was fixed in versions: 4.1.2, 4.3.2
  ✗ Improper Certificate Validation [High Severity][https://snyk.io/vuln/SNYK-DOTNET-SYSTEMNETHTTP-60046] in System.Net.Http@4.3.0
    introduced by xunit@2.4.1 > xunit.assert@2.4.1 > NETStandard.Library@1.6.1 > System.Net.Http@4.3.0 and 3 other path(s)
  This issue was fixed in versions: 4.1.2, 4.3.2
  ✗ Privilege Escalation [High Severity][https://snyk.io/vuln/SNYK-DOTNET-SYSTEMNETHTTP-60047] in System.Net.Http@4.3.0
    introduced by xunit@2.4.1 > xunit.assert@2.4.1 > NETStandard.Library@1.6.1 > System.Net.Http@4.3.0 and 3 other path(s)
  This issue was fixed in versions: 4.1.2, 4.3.2
  ✗ Authentication Bypass [Medium Severity][https://snyk.io/vuln/SNYK-DOTNET-SYSTEMNETHTTP-60048] in System.Net.Http@4.3.0
    introduced by xunit@2.4.1 > xunit.assert@2.4.1 > NETStandard.Library@1.6.1 > System.Net.Http@4.3.0 and 3 other path(s)
  This issue was fixed in versions: 4.1.2, 4.3.2
  ✗ Information Exposure [High Severity][https://snyk.io/vuln/SNYK-DOTNET-SYSTEMNETHTTP-72439] in System.Net.Http@4.3.0
    introduced by xunit@2.4.1 > xunit.assert@2.4.1 > NETStandard.Library@1.6.1 > System.Net.Http@4.3.0 and 3 other path(s)
  This issue was fixed in versions: 2.0.20710, 4.0.1-beta-23225, 4.1.4, 4.3.4
  ✗ Regular Expression Denial of Service (ReDoS) [High Severity][https://snyk.io/vuln/SNYK-DOTNET-SYSTEMTEXTREGULAREXPRESSIONS-174708] in System.Text.RegularExpressions@4.3.0
    introduced by Microsoft.NET.Test.Sdk@16.11.0 > Microsoft.TestPlatform.TestHost@16.11.0 > Newtonsoft.Json@9.0.1 > System.Text.RegularExpressions@4.3.0 and 14 other path(s)
  This issue was fixed in versions: 4.3.1
```