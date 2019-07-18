---
layout: page
title: Books
permalink: /books/
books:
  -
    title:
      - en: 'Redesigning Psychiatry #2'
      - nl: 'Samen innoveren voor het welzijn van toekomstige generaties'
        en: 'Collaborative innovation for the well-being of future generations'
    about: >-
      Report (Dutch, 102 pages).
      With Femke de Boer et al.
      Amsterdam: Redesigning Psychiatry, 2018.    
    image: rpcover02.png
    pdf: rp2.pdf
  -
    title:
      - en: 'Redesigning Psychiatry #1'
      - nl: 'Innoveren voor psychisch welzijn in de 21e eeuw'
        en: 'Innovating for mental well-being in the 21st century'
    about: >-
      Report (Dutch, 76 pages).
      With Femke de Boer et al.
      Amsterdam: Redesigning Psychiatry, 2016.
    image: rpcover01.png
    pdf: rp1.pdf
  -
    title:
      - en: 'The Normative Will'
      - en: 'Practical Judgment as Volitional Interpretation'
    about: >-
      PhD thesis (354 pages).
      Tilburg: Tilburg University, 2012.
    image: nwcover.png
    pdf: tnw.pdf
  -
    title:
      - nl: 'Vrije wil'
        en: 'Free will'
      - nl: 'Discussies over verantwoordelijkheid, zelfverwerkelijking en bewustzijn'
        en: 'Discussions on responsibility, self-realization and consciousness'
    about: >-
      Textbook (Dutch, 216 pages).
      With Tjeerd van de Laar.
      Rotterdam: Lemniscaat, 2011.
    image: rpcover01.png
    link: https://www.lemniscaat.nl/boeken/vrije-wil-discussies-over-verantwoordelijkheid-zelfverwerkelijking-en-bewustzijn/
---

{% for book in page.books %}
  {%- capture image -%}/assets/img/{{- book.image -}}{%- endcapture -%}

  {%- if book.pdf -%}
    {%- capture link -%}/assets/pdf/{{- book.pdf -}}{%- endcapture -%}
  {%- else -%}
    {%- assign link = book.link -%}
  {%- endif -%}

  {%- if book.title.first.nl -%}
    {%- assign alt = book.title.first.nl -%}
    {%- capture title %}{{ book.title.first.nl }}: {{ book.title.last.nl }}{:lang="nl"}{% endcapture -%}
    {%- capture translation %}({{ book.title.first.en }}: {{ book.title.last.en }}). {% endcapture -%}

  {%- elsif book.title.last.nl -%}
    {%- assign alt = book.title.first.en -%}
    {%- capture title %}{{ book.title.first.en }}: {::}{{ book.title.last.nl }}{:lang="nl"}{% endcapture -%}
    {%- capture translation %}({{ book.title.last.en }}). {% endcapture -%}

  {%- else -%}
    {%- assign alt = book.title.first.en -%}
    {%- capture title -%}{{- book.title.first.en -}}: {{- book.title.last.en -}}{%- endcapture -%}
    {%- assign translation = '' -%}

  {%- endif -%}

[![{{ alt }}]({{ image }}){:style="width: 100px"}]({{ link }})

[{{ title }}]({{ link }})

{{ translation }}{{ book.about }}

{% endfor %}
