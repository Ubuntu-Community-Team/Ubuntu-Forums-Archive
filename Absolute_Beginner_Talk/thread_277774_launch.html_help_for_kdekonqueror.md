---
title: "launch.html help for kde/konqueror"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by kerry_s on 2006-10-15
I was wondering if some one could help me with a little customizing?
I'm trying to change my /usr/share/apps/konqueror/about/launch.html , i have it to where it has "google search" but would like to have the "google "i'm feeling lucky" search" below that. I'm not good at html at all, i'm just winging it for now. Can any one help me do this faster?

```
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <meta name="generator" content=
  "HTML Tidy for Linux/x86 (vers 1st August 2004), see www.w3.org" />

  <style type="text/css">
  /*<![CDATA[*/
    @import "%1"; /* kde_infopage.css */
    %1 /* maybe @import "kde_infopage_rtl.css"; */
    @import "konq.css";
  /*]]>*/
  </style>

  <title>%1</title>
</head>

<body>
  <div id="header">
    <div id="headerL"/>
    <div id="headerR"/>

    <div id="title">
      %1 <!-- Konqueror -->
    </div>

    <div id="tagline">
      %1 <!-- Conquer your Desktop -->
    </div>
  </div>

  <!-- the bar -->
  <div id="bar">
    <div id="barT"><div id="barTL"/><div id="barTR"/><div id="barTC"/></div>
    <div id="barL">
      <div id="barR">
        <div id="barCenter" class="bar_text">
          %1<br />


  </div>

  <!-- the main text box -->
  <div id="box">
    <div id="boxT"><div id="boxTL"/><div id="boxTR"/><div id="boxTC"/></div>
    <div id="boxL">
      <div id="boxR">
        <div id="boxCenter">

	<table border="0" align="center">
<!--search bar argument replacement is performed between the "search bar splitter" lines-->
<!--search bar splitter-->

        <tr>
        <form action="about:konqueror">
        <td colspan="2" style="text-align:right;"><label id="searchbarlabel" for="searchbarinput">%2: </label></td>
        <td colspan="2"><input id="searchbarinput" name="%3" type="text"></td>
        </form>
        </tr>
        <tr>
        <td colspan="4"><div style="width:%1px; height:%1px;"/></td>
        </tr>


<!--search bar splitter-->		     


	    </table>


			<!-- Continue --></a></p>

        </div>
      </div>
    </div>
    <div id="boxB"><div id="boxBL"/><div id="boxBR"/><div id="boxBC"/></div>
  </div>

  <div id="footer"><div id="footerL"/><div id="footerR"/></div>
</body>
</html>
<!-- vim:set sw=2 et nocindent smartindent: -->

```

---

### Post by kerry_s on 2006-10-15
Change of plan, i snag the look from the google.com site and just need to get the search buttons working. Can any one help?

```
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <meta name="generator" content=
  "HTML Tidy for Linux/x86 (vers 1st August 2004), see www.w3.org" />

  <style type="text/css">
  /*<![CDATA[*/
    @import "%1"; /* kde_infopage.css */
    %1 /* maybe @import "kde_infopage_rtl.css"; */
    @import "konq.css";
  /*]]>*/
  </style>

  <title>%1</title>
</head>

<body>
  <div id="header">
    <div id="headerL"/>
    <div id="headerR"/>

    <div id="title">
      %1 <!-- Konqueror -->
    </div>

    <div id="tagline">
      %1 <!-- Conquer your Desktop -->
    </div>
  </div>

  <!-- the bar -->
  <div id="bar">
    <div id="barT"><div id="barTL"/><div id="barTR"/><div id="barTC"/></div>
    <div id="barL">
      <div id="barR">
        <div id="barCenter" class="bar_text">
          %1<br />


  </div>

  <!-- the main text box -->
  <div id="box">
    <div id="boxT"><div id="boxTL"/><div id="boxTR"/><div id="boxTC"/></div>
    <div id="boxL">
      <div id="boxR">
        <div id="boxCenter">

	<table border="0" align="center">
<!--search bar argument replacement is performed between the "search bar splitter" lines-->
<!--search bar splitter-->


        <tr>
        <form action="about:konqueror">
        <td align=center><input maxlength=2048 size=55<value=" " title="Google Search"><br><input type=submit value="Google Search" name=btnG><input type=submit value="I'm Feeling Lucky"
        </form>
        </tr>
        <tr>
        <td colspan="4"><div style="width:4%1px; height:3%1px;"/></td>
        </tr>


<!--search bar splitter-->		     


	    </table>


			<!-- Continue --></a></p>

        </div>
      </div>
    </div>
    <div id="boxB"><div id="boxBL"/><div id="boxBR"/><div id="boxBC"/></div>
  </div>

  <div id="footer"><div id="footerL"/><div id="footerR"/></div>
</body>
</html>
<!-- vim:set sw=2 et nocindent smartindent: -->

```

---

### Post by Arevos on 2006-10-15
Try changing the <form action="about:konqueror"> to <form action="http://www.google.com/search"> and change the various input tags to have the same value as those on the Google homepage (view source and take a look through the HTML).

---

### Post by kerry_s on 2006-10-15
Hey thanks for the reply. I tried what you suggested but it didn't work. I even tried copying the whole google html, but that didn't work either. I think i'll just live with how i got it now, it still loads a hell of alot faster than setting google as my home page, i'm on wireless so depending on my signal the google.com can take time to load, but the modified html loads instantly.

---

