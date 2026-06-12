---
title: "Swiftfox search bar redirect"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by detroit/zero on 2007-12-08
Here's an odd one. I know it's not exactly Linux related, but the people at the FF forums are clueless, and there is no info to be found that I can find. Also, my ignorance in such matters most likely contributes to my problem.

I am an American Citizen (please don't hold that against me) who has recently settled in Poland. I use Google in the search box up next to the address bar more times in a day than I can count. Since my move to Europe, whenever I search for something using Google, rather than going to Google.us, I'm redirected to Google.pl  This would be fine, except for the fact that I'm not well versed in the language and navigating the menus is a bit tricky. Typing "google.us" into the address bar takes me to the familiar (English) interface.

What I want to do is make the google search plugin in the search box point to Google.us instead of being defaulted to Google.pl

It should be easy, but as I said, I'm a little ignorant as to the inner workings of FF/SF.

I'm using:
Feisty
Latest Swiftfox (2.0.0.4)

Thanks for any help.

---

### Post by Stirling on 2007-12-08
Hello, check the file swiftfox/searchplugins/google.xml in a text editor.  Specifically looking for this line: ```
<Url type="text/html" method="GET" template="http://www.google.com/search">
```  Try changing it to: ```
<Url type="text/html" method="GET" template="http://www.google.us/search">
```  Then restart Swiftfox.

---

### Post by detroit/zero on 2007-12-08
That was a good start. More than anything I wanted to know where that file was located.

Still, though, after making the edit you suggested I'm still being sent to google.pl  In the status bar I see it start to connect to google.us, then goes to google.com, and then is redirected to google.pl

I changed the generic "google.com" everywhere it appears in that file to "google.us", but I'm still being redirected.

Here's the contents of my "google.xml" file. Did I miss something?
```
<SearchPlugin xmlns="http://www.mozilla.org/2006/browser/search/">
<ShortName>Google</ShortName>
<Description>Google Search</Description>
<InputEncoding>UTF-8</InputEncoding>
<Image width="16" height="16">data:image/x-icon;base64,R0lGODlhEAAQAPfLAAATVikwdA8SnxUfgAsWpAAilholjxw4jBc7kwAlvQQ2sRMsoBUqqhMzuhY/vxw4tSgmiyM1mSUztiQ6sTE3sQ4qyxMxxRoyxiAuxR1CtBxJsBxasSJuuTFguBte0Rlf2xVc9h9W9xVjzxVr0gdj6BRh4R1o5yBcyiZbyydT1i9b2Ddb1iFY6CJg2Vpor1dzvEJu20Z0yi23QDy1REi2OUy0O1WzOVC4PU+tVUe5Sk2xQU2zRUO4UE21Ula2SmKEqWWF2HyPx2+a6X6e6Xqk1m+s78sUDs4UGdEQB9YfDdwaANEfHd0YEscjAM4mAM0qANIoD9IkGdslGswuItYgL4aP0ImP2YGZ36Opzaq2wq/S+rzX/7/e8MrS1MLO/sTb48rT8snX/83c89PZ+crq+cH1/9Dl/9Ln/93r/9fy/+Hf7P/42eDm/O7u/+T29uX2/eT2/+f4/+f5/+j/9u//8+3/9u7/9ur5/+j//+n//+v//u3//+7//e7//+////b66/T/6vX/6/f/7f/07fj/4fv/4Pj/5v/45v7/4/r+7/3/6fDw+Pfx//D/9/X/8fT/8/f/8ff/8/D///H///L8/fL///P///X7//b6/ff/+/T///b9//f///v19//w9v/09P/29v/x+f/y///z///1+v/1///2///3//j79P/58/z/8/z99/z/9v7/9P7/9vn7//v6//j9//n9//j///n///v//vv////4+v/5+//6+P/4///6/P/6/v/6///7///9+P/8+v/9+v7/+Pz////8/f/9/f79///8///9//7//////////wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACH5BAEAAMsALAAAAAAQABAAAAj/AEn4oIFjBw8bOnrMuJGjhowZM1T8UdYJUZ5ZcNRYWjSrVK5QU0DMmtUnzRAXEy4o6FCEy6NDTkQIq1MmRgM0eZTlCXMgQJtRSE4gmgUkwh1EiZTNUiamy6NUUExcuoJgDCdDjQg9KgVL2SNFT1hwEvKglLBWuixZ+jSrlSBdRlL04bBBkTBdpZTpIqWsFaBcTEr0QaEhl6dWlswKW6poDRUPlmAUQKWMkTJLc76QMQNGUZMWgIgkCFJnlq5WXigwkFClVZQQyuRgELAlk7JBymCZGYAF0ZEPrQixgUDAihxVdPpoAZAFUZIRfThxgvPCwAILDipk+OFG2ZIVoxApERtPfvwlvZ+kQFzPvv0MJQEBADs=</Image>
<Url type="application/x-suggestions+json" method="GET" template="http://suggestqueries.google.us/complete/search?output=firefox&amp;client=firefox&amp;qu={searchTerms}"/>
<Url type="text/html" method="GET" template="http://www.google.us/search">
  <Param name="q" value="{searchTerms}"/>
  <Param name="ie" value="utf-8"/>
  <Param name="oe" value="utf-8"/>
  <Param name="aq" value="t"/>
  <!-- Dynamic parameters -->
  <Param name="rls" value="{moz:distributionID}:{moz:locale}:{moz:official}"/>
  <MozParam name="client" condition="defaultEngine" trueValue="firefox-a" falseValue="firefox"/>
</Url>
<SearchForm>http://www.google.us/firefox</SearchForm>
</SearchPlugin>

```

---

### Post by detroit/zero on 2007-12-08
Quick update: I notice that when I type "google.us" into the address bar, when I'm taken to google's main page, it's added "webhp" to the end of the address, as such:

```
http://www.google.com/webhp
```I tried adding that to the address in the google.xml file. Now, when I type in the search bar, I'm taken to the main google page with my query already entered into the box. When I hit enter, I'm still being redirected to google.pl, but my results are in English (which is my main goal here).

Any ideas on how to cut out that middle step of going to the main Google page? I know it has something to do with the "/webhp" at the end of the URL, but without it my results (and menus) remain in Polish.



Quick side note: None of the other search engines I use do this. Not Yahoo, Google Maps, Google Linux, Ask.. none but The Google itself.

---

### Post by Stirling on 2007-12-08
Try this workaround:
[LIST=1]
[*]go to google.pl
[*]click on "Ustawienia"
[*]for "J&#281;zyk interfejsu" choose "angielski" from the drop down menu
[*]for "Szukaj w innym j&#281;zyku"  select "Szukaj tylko w tym wybranym j&#281;zyku(ach):" and check the box for "angielski"
[*]click on "zapisz ustawienia"
[/LIST]
You will still default to google.pl but now everything will be in English.  You can then change the google.xml file back to the default.

---

### Post by detroit/zero on 2007-12-08
I suppose that's as good as anything.

I'll call it "problem solved".

Thanks for the help, guys.

---

