---
layout: default
---

{% assign redirects = site.pages | where_exp: "item", "item.redirect_to != nil" | sort: 'category' %}
{% assign lc = "" %}
{% for page in redirects %}
{% if lc == page.category %}
{% else %}
## {{ page.category }}
{% assign lc = page.category %}
{% endif %}
  [{{ page.url }}]({{ page.url | relative_url }}) 🔀 `{{ page.redirect_to }}`

  > {{ page.title | escape }}

  ---
{% endfor %}
