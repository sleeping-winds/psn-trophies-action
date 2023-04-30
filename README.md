# psn-trophies-action

Add PlayStation trophies to your profile README.

### Setup

1. You need to update the README file with 2 comments. 

```
<!--START_SECTION:psn-->
<!--END_SECTION:psn-->
```

This action will populate this section with the PlayStation trophies.

2. You will need to get an authentication token from PlayStation. Sign into [PlayStation's homepage](https://www.playstation.com/en-us/). Then visit [here](https://ca.account.sony.com/api/v1/ssocookie) to get your SSO cookie.

3. Create a [secret](https://docs.github.com/en/actions/security-guides/encrypted-secrets) so that this action can use it.

### Example

```
name: Update PlayStation Trophies

on:
  schedule:
    # Runs at 0am UTC every day
    - cron: "0 0 * * *"

jobs:
  update-ps-trophies:
    name: Update Readme with PlayStation Trophies
    runs-on: ubuntu-22.04
    steps:
      - name: Checkout source
        uses: actions/checkout@v3

      - name: Add ps trophies
        uses: sleeping-winds/psn-trophies-action@v0.1.3
        with:
          NPSSO: ${{ secrets.NPSSO }}

      - name: Check in updated README
        uses: EndBug/add-and-commit@v9
```
