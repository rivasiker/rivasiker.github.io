---
layout: page
permalink: /news/
title: news
nav: true
nav_order: 3
---

<div class="news">
  {% if site.news != blank -%} 
  {%- assign news_size = site.news | size -%}
  <div class="table">
    <table class="table table-sm table-borderless">
      <colgroup>
        <col span="1" style="width: 15%;">
        <col span="1" style="width: 85%;">
      </colgroup>
    {%- assign news = site.news | reverse -%}
    {% for item in news limit: news_limit %} 
      <tr>
        <th scope="row">{{ item.date | date: "%b %-d, %Y" }}</th>
        <td>
          {% if item.inline -%} 
            {{ item.content | remove: '<p>' | remove: '</p>' | emojify }}
          {%- else -%} 
            <a class="news-title" href="{{ item.url | relative_url }}">{{ item.title }}</a>
          {%- endif %} 
        </td>
      </tr>
    {%- endfor %} 
    </table>
  </div>
{%- else -%} 
  <p>No news so far...</p>
{%- endif %} 
</div>