# discord-notify-pr-review-request

Github Actions to notify discord when requesting PR review

## Usage

1. Set a secret named 'DISCORD_WEBHOOK' for `Actions`.

> Settings > Secrets and variables > Actions > New repository secret

ex) `https://discord.com/api/webhooks/xxx.../xxx...`

2. Create a file `.github/workflow/notify-pr-review.yml`:

```yml
name: discord-notify-pr-review-request

on:
  pull_request:
    types: [review_requested]

jobs:
  notify:
    runs-on: [ubuntu-latest]
    steps:
      - name: discord-notify-pr-review-request
        uses: captos/discord-notify-pr-review-request@v1.0.8
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          discordWebhookUrl: ${{ secrets.DISCORD_WEBHOOK }}
```

## Inputs

- `token`(**Required**): GitHub Token
- `discordWebhookUrl`(**Required**): Webhook Url for Discord  
  ex) `https://discord.com/api/webhooks/xxx.../xxx...`

## License

```
Copyright (c) 2022-present Captos Co,. Ltd.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
