---
title: "More Fonts for GIMP"
date: 2007-03-10
forum: Art &amp; Design
---

### Post by KYhillbilly2006 on 2007-03-10
Where can I find more fonts?  And how do I install?  I don't even have any script fonts and trying to come up with different web graphics is getting hard especially since I don't have what I want.

---

### Post by Madpilot on 2007-03-11
There are tonnes of free good-quality fonts on the web; the problem I find isn't lack of fonts, but too many of the things!

I especially like [Dafont]("http://www.dafont.com/"), which is well organized, easy to search, and links to the font author's websites & other works. Dafont also makes it easy to check how complete a font is - does it have numerals, most punctuation, etc.

There are also lots and lots of paid fonts out there, many of them are very, very good quality. Professional-grade fonts are not cheap, however.

---

### Post by Hishgraphics on 2007-03-12
And I put all my required .ttf fonts I got from dafont in:

```
usr/share/fonts/truetype/myfonts
```

..."myfonts" is a directory I created for that purpose.

Then I open up terminal to refresh the font cache:

```
sudo fc-cache -f -v
```

And you should be good to go with GIMP.

---

