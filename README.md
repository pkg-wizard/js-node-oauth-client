# `oauth-client`

Helper for exchanging authentication credentials

## Config

| Name                                        | Description                                                           |
| ------------------------------------------- | --------------------------------------------------------------------- |
| OAuthUrl                                    | OAuth Url for exchanging credentils                                   |

For logger configuration properties see the
[logger documentation]

For resilient executor configuration properties see the
[resilient executor documentation]


## Usage

```typescript
/** init oauthclient instance (should use 1 instance per app) */
import { OAuthClient } from 'js-node-oauth-client';

const loggerConfig = : { logLevel: 'cli', logStyle: 'debug', appName: 'nodejs-commons', moduleName: 'ResilientExecutor' }, // logger configuration

const oauthClient = new OAuthClient('https://auth.dummy.test.url/oauth2/token', loggerconfig);

await oauthClient.exchangeCredentialsForToken({
        username: 'test',
        password: 'test',
      });


/** with resilient executor */

/** init oauthclient instance (should use 1 instance per app) */
import { OAuthClient } from 'js-node-oauth-client';
import { ResilientExecutor } from 'http-resilient-executor';

const resilientConfig = {
  logger: { logLevel: 'cli', logStyle: 'debug', appName: 'nodejs-commons', moduleName: 'ResilientExecutor' }, // logger configuration
  httpResilienceCBHalfOpenAfterMS: 10 * 1000,
  httpResilienceCBConsecutiveThreshold: 5,
  httpResilienceRetryCount: 3,
};

const resilientExec = new ResilientExecutor(resilientConfig);

const oauthClient = new OAuthClient('https://auth.dummy.test.url/oauth2/token', loggerconfig, resilientExec);

await oauthClient.exchangeCredentialsForToken({
        username: 'test',
        password: 'test',
      });
```
