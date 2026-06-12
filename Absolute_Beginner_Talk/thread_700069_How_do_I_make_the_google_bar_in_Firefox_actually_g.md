---
title: "How do I make the google bar in Firefox actually go to Google?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2008-02-18
Heres the deal.  I'm using Linux Mint, and I updated Firefox yesterday.  Now, when I google search through the bar, I go to a customized linux mint google page, which I don't want to do because it doesn't have google images or google video as links, and there are ads (which regular google doesn't.)  How can I make it go to just regular google?

---

### Post by amohanty on 2008-02-18
I am on Hardy/ff3 so this may be different on gutsy. Look for a file called google.xml on your filesystem. In my case it is in /usr/lib/firefox-addons/searchplugins.

In there look for the Url and SearchForm tags and put the following in there (this is the default) instead of what is in it:

<Url type="application/x-suggestions+json" method="GET" template="http://suggestqueries.google.com/complete/search?output=firefox&amp;client=firefox&amp;hl={moz:locale}&amp;q={searchTerms}"/>
<Url type="text/html" method="GET" template="http://www.google.com/search">
  <Param name="q" value="{searchTerms}"/>
  <Param name="ie" value="utf-8"/>
  <Param name="oe" value="utf-8"/>
  <Param name="aq" value="t"/>
  <!-- Dynamic parameters -->
  <Param name="rls" value="{moz:distributionID}:{moz:locale}:{moz:official}"/>
  <MozParam name="client" condition="defaultEngine" trueValue="firefox-a" falseValue="firefox"/>
</Url>
<SearchForm>http://www.google.com/firefox</SearchForm>


HTH
AM

---

### Post by TheOrangePeanut on 2008-02-18
Okay, I changed the file but no dice.  Now google isn't even on the toolbar, and "restore defaults" doesn't fix it.  I have a feeling it is because of this error that I get when I open the .xml file itself in Firefox.

XML Parsing Error: junk after document element
Location: file:///usr/lib/firefox/searchplugins/google.xml
Line Number 2, Column 1:<Url type="text/html" method="GET" template="http://www.google.com/search">
^

Here is what I put into the XML file.

<Url type="application/x-suggestions+json" method="GET" template="http://suggestqueries.google.com/complete/search?output=firefox&amp;client=firefox&amp;hl={moz:locale}&amp;q={searchTerms}"/>
<Url type="text/html" method="GET" template="http://www.google.com/search">
  <Param name="q" value="{searchTerms}"/>
  <Param name="ie" value="utf-8"/>
  <Param name="oe" value="utf-8"/>
  <Param name="aq" value="t"/>
  <!-- Dynamic parameters -->
  <Param name="rls" value="{moz:distributionID}:{moz:locale}:{moz:official}"/>
  <MozParam name="client" condition="defaultEngine" trueValue="firefox-a" falseValue="firefox"/>
</Url>
<SearchForm>http://www.google.com/firefox</SearchForm>

---

### Post by amohanty on 2008-02-18
Ok did you replace the entire file with the snippet I gave you?

Can you by any chance post the original? If you lost it no-worries just do a (in a terminal)
sudo apt-get --reinstall install firefox

AM

PS: you wont lose your settings

---

### Post by Xavieran on 2008-02-18
> **TheOrangePeanut said:**
> Okay, I changed the file but no dice.  Now google isn't even on the toolbar, and "restore defaults" doesn't fix it.  I have a feeling it is because of this error that I get when I open the .xml file itself in Firefox.

XML Parsing Error: junk after document element
Location: file:///usr/lib/firefox/searchplugins/google.xml
Line Number 2, Column 1:<Url type="text/html" method="GET" template="http://www.google.com/search">
^

Here is what I put into the XML file.

<Url type="application/x-suggestions+json" method="GET" template="http://suggestqueries.google.com/complete/search?output=firefox&amp;client=firefox&amp;hl={moz:locale}&amp;q={searchTerms}"/>
[COLOR="Red"]<Url type="text/html" method="GET" template="http://www.google.com/search">[/COLOR]
  <Param name="q" value="{searchTerms}"/>
  <Param name="ie" value="utf-8"/>
  <Param name="oe" value="utf-8"/>
  <Param name="aq" value="t"/>
  <!-- Dynamic parameters -->
  <Param name="rls" value="{moz:distributionID}:{moz:locale}:{moz:official}"/>
  <MozParam name="client" condition="defaultEngine" trueValue="firefox-a" falseValue="firefox"/>
</Url>
<SearchForm>http://www.google.com/firefox</SearchForm>

You need to replace the line in red with```
<Url type="text/html" method="GET" template="http://www.google.com/search"/>
```

---

### Post by amohanty on 2008-02-18
Umm the </Url> tag at the bottom closes it out, so probably not, I think its the first line being split up into two. 

My fault - I simply copy pasted it from my editor.The first <Url.... all the way to the end of the second line is a single line.

Sorry about that.

AM

PS: maybe not maybe its the editor here. If the first one is a complete line in the file, the problem lies elswhere.

---

### Post by TheOrangePeanut on 2008-02-18
I reinstalled so now I have the current file.  Here is what it looks like.

<SearchPlugin xmlns="http://www.mozilla.org/2006/browser/search/">
<ShortName>Google</ShortName>
<Description>Google Search</Description>
<InputEncoding>UTF-8</InputEncoding>
<Image width="16" height="16">data:image/x-icon;base64,R0lGODlhEAAQAPfLAAATVikwdA8SnxUfgAsWpAAilholjxw4jBc7kwAlvQQ2sRMsoBUqqhMzuhY/vxw4tSgmiyM1mSUztiQ6sTE3sQ4qyxMxxRoyxiAuxR1CtBxJsBxasSJuuTFguBte0Rlf2xVc9h9W9xVjzxVr0gdj6BRh4R1o5yBcyiZbyydT1i9b2Ddb1iFY6CJg2Vpor1dzvEJu20Z0yi23QDy1REi2OUy0O1WzOVC4PU+tVUe5Sk2xQU2zRUO4UE21Ula2SmKEqWWF2HyPx2+a6X6e6Xqk1m+s78sUDs4UGdEQB9YfDdwaANEfHd0YEscjAM4mAM0qANIoD9IkGdslGswuItYgL4aP0ImP2YGZ36Opzaq2wq/S+rzX/7/e8MrS1MLO/sTb48rT8snX/83c89PZ+crq+cH1/9Dl/9Ln/93r/9fy/+Hf7P/42eDm/O7u/+T29uX2/eT2/+f4/+f5/+j/9u//8+3/9u7/9ur5/+j//+n//+v//u3//+7//e7//+////b66/T/6vX/6/f/7f/07fj/4fv/4Pj/5v/45v7/4/r+7/3/6fDw+Pfx//D/9/X/8fT/8/f/8ff/8/D///H///L8/fL///P///X7//b6/ff/+/T///b9//f///v19//w9v/09P/29v/x+f/y///z///1+v/1///2///3//j79P/58/z/8/z99/z/9v7/9P7/9vn7//v6//j9//n9//j///n///v//vv////4+v/5+//6+P/4///6/P/6/v/6///7///9+P/8+v/9+v7/+Pz////8/f/9/f79///8///9//7//////////wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACH5BAEAAMsALAAAAAAQABAAAAj/AEn4oIFjBw8bOnrMuJGjhowZM1T8UdYJUZ5ZcNRYWjSrVK5QU0DMmtUnzRAXEy4o6FCEy6NDTkQIq1MmRgM0eZTlCXMgQJtRSE4gmgUkwh1EiZTNUiamy6NUUExcuoJgDCdDjQg9KgVL2SNFT1hwEvKglLBWuixZ+jSrlSBdRlL04bBBkTBdpZTpIqWsFaBcTEr0QaEhl6dWlswKW6poDRUPlmAUQKWMkTJLc76QMQNGUZMWgIgkCFJnlq5WXigwkFClVZQQyuRgELAlk7JBymCZGYAF0ZEPrQixgUDAihxVdPpoAZAFUZIRfThxgvPCwAILDipk+OFG2ZIVoxApERtPfvwlvZ+kQFzPvv0MJQEBADs=</Image>
<Url type="application/x-suggestions+json" method="GET" template="http://suggestqueries.google.com/complete/search?output=firefox&amp;client=firefox&amp;qu={searchTerms}"/>
<Url type="text/html" method="GET" template="http://www.google.com/cse">
  <Param name="cx" value="002683415331144861350%3Atsq8didf9x0"/>
  <Param name="q" value="{searchTerms}"/>
  <Param name="ie" value="utf-8"/>
  <Param name="oe" value="utf-8"/>
  <Param name="cof" value="FORID%3A1"/>
  <Param name="sa" value="Search"/>    
</Url>
<SearchForm>http://www.linuxmint.com/start</SearchForm>
</SearchPlugin>

I'm editing it with gksudo gedit "the file name"

---

### Post by amohanty on 2008-02-18
Ok change the following:

[http://www.google.com/cse](http://www.google.com/cse)

to 

[http://www.google.com/search](http://www.google.com/search)

Delete the following lines:
<Param name="cof" value="FORID%3A1"/>
<Param name="sa" value="Search"/> 

And add the following:

<Param name="aq" value="t"/>
<!-- Dynamic parameters -->
<Param name="rls" value="{moz:distributionID}:{moz:locale}:{mozffi cial}"/>
<MozParam name="client" condition="defaultEngine" trueValue="firefox-a" falseValue="firefox"/>

after the following line:
<Param name="oe" value="utf-8"/>

HTH
AM

PS: google.com/cse is custom search engine for vendors and others.

---

### Post by MaxxJ on 2008-06-19
I found a very easy solution to this... You just have to download the firefox software from the official website, get the google.xml file from it and replace the one in your system with the new one you just got.

---

### Post by Bubba64 on 2008-06-19
Even easier just go to the Google page that you want FF to open with click on edit-preferences-main-use current page.

---

### Post by MaxxJ on 2008-06-19
> **Bubba64 said:**
> Even easier just go to the Google page that you want FF to open with click on edit-preferences-main-use current page.

It's not about the start page, it's about the page used by the quick search box (the top right box with a little google logo, or yahoo.. or whatever you use). When a vendor changes it for some less practical custom google page, it's not so obvious to change it back to normal. My last message is how I finally did it successfully.

---

### Post by lonoy on 2008-06-22
You could also go to this page:

[http://mycroft.mozdev.org/search-engines.html?name=google&sherlock=yes&opensearch=yes&submitform=Search]("http://mycroft.mozdev.org/search-engines.html?name=google&sherlock=yes&opensearch=yes&submitform=Search")

Select the Google search/s that tickle your fancy.

Then,via the Manage Search Engines drop down on the Search box, simply remove the Google Mint search option.

If you add the Mycroft Project to your list of search engine via this page:

[https://addons.mozilla.org/en-US/firefox/addon/6887]("https://addons.mozilla.org/en-US/firefox/addon/6887")

You will find a easy access to millions (well lots anyway) of search engines.

Cheers

---

