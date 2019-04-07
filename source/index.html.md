---
title: TCG Hub - API Reference

# language_tabs: # must be one of https://git.io/vQNgJ
#   - shell
#   - ruby
#   - python
#   - javascript

toc_footers:
  # - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the TCG Hub API! You can use our API to access the TCG Hub API endpoints, which can get sets, cards, prices from our database.

# Authentication

<!-- > To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key. -->

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Sets

> The above command returns JSON structured like this:

```json
{
  "sets": [
    {
      "code": "base1",
      "ptcgoCode": "BS",
      "name": "Base",
      "series": "Base",
      "totalCards": 102,
      "standardLegal": false,
      "expandedLegal": false,
      "releaseDate": "01/09/1999",
      "symbolUrl": "https://images.pokemontcg.io/base1/symbol.png",
      "logoUrl": "https://images.pokemontcg.io/base1/logo.png",
      "setUpdatedAt": "01/03/2019 01:00:00",
      "updatedAt": "13/01/2019 21:42:00",
      "tcgPlayerGroupId":"604",
      "section":"main",
      "order":1
    }
  ]
}
```

This endpoint retrieves all Sets stored in the database.

### HTTP Request

`GET http://api.tcghub.co.uk/sets`


# Cards

> The above command returns JSON structured like this:

```json
[
    {
        "id": "sm9-1",
        "name": "Celebi & Venusaur-GX",
        "imageUrl": "https://images.pokemontcg.io/sm9/1.png",
        "subtype": "GX",
        "supertype": "Pokémon",
        "hp": "270",
        "retreatCost": [
            "Colorless",
            "Colorless",
            "Colorless",
            "Colorless"
        ],
        ...
        "resistances": [],
        "imageUrlHiRes": "https://images.pokemontcg.io/sm9/1_hires.png",
        "nationalPokedexNumber": 251
    }
]
```

This endpoint retrieves all cards from a specified set.

### HTTP Request

`GET http://api.tcghub.co.uk/cards?set=<SET>`

### Query Parameters

Parameter |  Description
--------- | -----------
set | Full set name split with a space, '%20' or '_'

# Prices

> The above command returns JSON structured like this:

```json
{
  "prices":[
    {
      "id":"base1-1",
      "number":1,
      "productId":"42346",
      "productUrl":"base-set/alakazam",
      "prices":[
        {
          "lowPrice":5.0,
          "midPrice":11.35,
          "highPrice":20.0,
          "marketPrice":11.73,
          "variant":"Holofoil"
        }
      ]
    }
  ]
}
```

This endpoint retrieves all the latest prices from TCG Player. These prices are updated daily automatically on the server, to be retreived via this call.

### HTTP Request

`GET http://api.tcghub.co.uk/prices`

# Card of the Day

> The above command returns JSON structured like this:

```json
{
  "id": "ex12-20",
  "name": "Lunatone",
  "imageUrl": "https://images.pokemontcg.io/ex12/20.png",
  "subtype": "Basic",
  "supertype": "Pokémon",
  "ability": {
    "name": "Sol Shade",
    "text": "As long as you have Solrock in play, each player's Fire Pokémon (excluding Pokémon-ex) can't use any Poké-Powers.",
    "type": "Poké-Body"
  },
  ...
  "imageUrlHiRes": "https://images.pokemontcg.io/ex12/20_hires.png",
  "nationalPokedexNumber": 337
}
```

This endpoint retrieves all the Card of the Day. This is automatically updated on Azure daily, ready to be retrieved via this call.

### HTTP Request

`GET http://api.tcghub.co.uk/cotd`

<!-- <aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside> -->
