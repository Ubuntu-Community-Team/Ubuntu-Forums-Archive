---
title: "No fonts in flash"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by phido on 2006-02-17
When I browse this [url[IMG]chrome://targetalert/content/skin/new.png[/IMG]]("http://www.pocketmod.com/app/index.html") for example i have no fonts, but flash is working. 
The swf settings menu has also no fonts in it, seems like something is missing.

---

### Post by gord on 2006-02-17
have you tryed [installing some extra fonts](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-fonts) such as the win32 fonts? sounds like the fonts it wants to use arn't there

---

### Post by phido on 2006-02-17
[quote=gord]have you tryed [installing some extra fonts[IMG]chrome://targetalert/content/skin/new.png[/IMG]]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-fonts") such as the win32 fonts? sounds like the fonts it wants to use arn't there[/quote]

I've copied my windows fonts to ubuntu, in openoffice they are available, and did now install some of suggested fonts but nothing changed.

After *sudo fc-cache -f -v *i get this

[I]fc-cache: "/usr/share/fonts": caching, 0 fonts, 3 dirs
fc-cache: "/usr/share/fonts/truetype": caching, 0 fonts, 21 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-devanagari-fonts": caching, 2 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-bitstream-vera": caching, 10 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/freefont": caching, 12 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/openoffice": caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-arabeyes": caching, 39 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/arphic": caching, 4 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/baekmuk": caching, 4 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-bengali-fonts": caching, 7 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-gujarati-fonts": caching, 5 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-kannada-fonts": caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-malayalam-fonts": caching, 2 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-oriya-fonts": caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-punjabi-fonts": caching, 2 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-tamil-fonts": caching, 9 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-telugu-fonts": caching, 2 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/kochi": caching, 4 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-mgopen": caching, 16 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/msttcorefonts": caching, 60 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-ubuntu-title": caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-dejavu": caching, 20 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/thryomanes": caching, 4 fonts, 0 dirs
fc-cache: "/usr/share/fonts/type1": caching, 0 fonts, 1 dirs
fc-cache: "/usr/share/fonts/type1/gsfonts": caching, 35 fonts, 0 dirs
fc-cache: "/usr/share/fonts/wine": caching, 50 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts": caching, 0 fonts, 5 dirs
fc-cache: "/usr/share/X11/fonts/encodings": caching, 0 fonts, 1 dirs
fc-cache: "/usr/share/X11/fonts/encodings/large": caching, 0 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts/100dpi": caching, 397 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts/75dpi": caching, 397 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts/misc": caching, 55 fonts, 1 dirs
fc-cache: "/usr/share/X11/fonts/misc/misc": caching, 0 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts/Type1": caching, 44 fonts, 0 dirs
fc-cache: "/usr/local/share/fonts": caching, 433 fonts, 0 dirs
fc-cache: "/home/stylesp/.fonts": caching, 0 fonts, 0 dirs
fc-cache: succeeded
[/I]

---

