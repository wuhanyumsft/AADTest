# AADTest
Sample code to use Azure Active Directory for authentication, Dotnet Core / Dotnet Framework

## .Net Core (AADTest2)
For .Net Core, the AAD authentication is built in.
All we need is to add:
```
            services.AddAuthentication(AzureADDefaults.AuthenticationScheme)
                .AddAzureAD(options => Configuration.Bind("AzureAd", options));
```

And realted configuration:
```
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "Domain": "microsoft.onmicrosoft.com",
    "TenantId": "72f988bf-86f1-41af-91ab-2d7cd011db47",
    "ClientId": "6d9eed82-e7e2-4c9a-8480-08aeb84c3ddc",
    "CallbackPath": "/.auth/login/aad/callback"
  }
```

Note: the callback path needs to be configurated in the `Authentication` Section of AAD in Azure Portal.

## .Net Framework (AADTest4)

.Net Framework is using Owin Open Id authentication, See Startup.Auth.cs.

And it would requite allowing an application to request a token directly from the authorization endpoint. Enable "ID tokens" in Authentication > Advanced settings > Implicit grant
