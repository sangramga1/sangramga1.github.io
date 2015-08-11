---
layout: page
title: Archive
---

<div>
  {% for post in site.posts %}
    {% capture post_year %}{{ post.date | date: '%Y' }}{% endcapture %}
    {% if forloop.first %}
      <h3>{{ post_year }}</h3><div>
    {% endif %}

    {% if forloop.first == false %}
      {% assign previous_index = forloop.index0 | minus: 1 %}
      {% capture previous_post_year %}{{ site.posts[previous_index].date | date: '%Y' }}{% endcapture %}
      {% if post_year != previous_post_year %}
        </div><h3>{{ post_year }}</h3><div>
      {% endif %}
    {% endif %}

    {{ post.date | date: site.archive_date_format }}: <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a><br />

    {% if forloop.last %}
      </div>
    {% endif %}
  {% endfor %}
</div>
