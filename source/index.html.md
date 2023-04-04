---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - shell

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Rocket API
---

# Introduction

Welcome to theRocket API! You can use our API to access Rocket API endpoints.

We have language bindings in Shell! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

<aside class="notice">
Set <code>export BASE_URL="localhost:3000"</code> for curl requests in order to set the desired request url.
<ul>
<li><code>http://localhost:3000</code> for local server usage</li>
<li><code>https://api-test.pocket-rocket.io</code> for the api test server</li>
<li><code>https://api.pocket-rocket.io</code> for the api production server</li>
</ul>
</aside>

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl -X POST -d '{"email": "info@pocket-rocket.io", "password": "ABC"}' $BASE_URL/v1/auth -v -H Content-Type:application/json |jq '.'
```

Rocket API uses JWT tokens for authorization. The auth endpoint return a jwt token which is valid for 24 hours. It has to be attached in each request of the private api endpoints.

<aside class="notice">
You must replace <code>$JWT_TOKEN</code> in all following requests with the JWT token received from the auth process.
</aside>

# Organizations

## Get All Organizations

```shell
curl "$BASE_URL/v1/organizations/" -v -H Content-Type:application/json -H "Authorization: Bearer $JWT_TOKEN" |jq '.'
```

<!-- > The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
] -->

This endpoint retrieves all organizations.

### HTTP Request

`GET /v1/organizations`

<!-- ### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted. -->

## Get a Specific Organization

```shell
curl "$BASE_URL/v1/organizations/1" \ -v -H Content-Type:application/json \ -H "Authorization: Bearer $JWT_TOKEN" |jq '.'

```

This endpoint retrieves a specific organization.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`GET /v1/organizations/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the organization to retrieve

## Delete a Specific Organization

```shell
curl -X DELETE "$BASE_URL/v1/organizations/1" \ -v -H Content-Type:application/json \ -H "Authorization: Bearer $JWT_TOKEN" |jq '.'
```
This endpoint deletes a specific organization.

### HTTP Request

`DELETE /v1/organizations/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the organization to delete

