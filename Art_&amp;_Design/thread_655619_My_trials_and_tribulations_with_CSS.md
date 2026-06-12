---
title: "My trials and tribulations with CSS"
date: 2008-01-01
forum: Art &amp; Design
---

### Post by Darkstar286 on 2008-01-01
Hey, I was wondering what fonts are available to CSS that would look like Ubuntu's defaults. I'm trying to make my Myspace look like Ubuntu. I've got a few keys for te colors and all, but the thing that's holding me up is these darn fonts, I can't find one that looks close enough for me.
halpplzthx?

---

### Post by Merk42 on 2008-01-01
Unless it's a font in one of the default families, the other people viewing your site most likely get the same look you do.

Bascially if you find some 'perfectUbuntufont.tff' and use that for you myspace, anyone viewing your page that doesn't have 'perfectUbuntufont.tff' installed will have the text default to some other font.

---

### Post by Darkstar286 on 2008-01-01
yeah exactly, that's why I wanted to know if there were any generic fonts that looked a bit like Ubuntu's standard one.

---

### Post by King_Critter on 2008-01-01
To install the official Ubuntu font, simply sudo apt-get install ttf-ubuntu-title.

Of course, as Merk mentioned above, they'll only see it if they have it installed as well. But you can, of course, us it in whatever images you have.

---

### Post by mcduck on 2008-01-02
There is no specific 'CSS fonts'. You can define any fonts you wish, and the browser will then see which one it can find from the system when people are browsing the web page.

The fonts are not included in the browser, or the web page, in any way.

In the end the only thing you can do is to specify couple of fonts you could expect people to have installed, and as the last entry use either 'sans' or 'sans-serif' so the browser at least knows what type of font you want the page to have.

Sadly, this limits pretty much what you can do whit fonts on web pages. The only way you can be sure that text is printed with the exact font you wanted is to make it into image instead of real text. I'd be really happy if there was some way to include fonts into web pages but there isn't..

Anyway, the Windows fonts included in msttcorefonts package are available on most desktop machines, and from those the ones closest to Ubutnu's default application fonts would be Arial and Verdana. (There really isn't much options to choose from..)

---

