---
title: "Font questions when creating websites with NVU?"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-03-17
I have font questions when creating websites with NVU especially under Linux?
I've noticed that Ubuntu doesn't have those usual fonts like you're used to as Windows user.  Besides the usual suspects like Times, Arial and Courier.

I'm just starting to learn how to build websites so my skills aren't that good yet.  But when I try to format texts and use the fonts that comes with Ubuntu, exotic looking fonts like "Lohit Punjabi" which looks something like Egyptian and Arabic.  It won't work in NVU even if I can choose it.

Then my second question if I the webdesigner can't see the fonts offered by Ubuntu when using NVU how are Windows users supposed to see the Linux like fonts on their PCs?

PS.
NVU crashes when you try to format to the font "Hershey Gothic".

---

### Post by mcduck on 2007-03-17
> **jingo811 said:**
> I have font questions when creating websites with NVU especially under Linux?
I've noticed that Ubuntu doesn't have those usual fonts like you're used to as Windows user.  Besides the usual suspects like Times, Arial and Courier.

I'm just starting to learn how to build websites so my skills aren't that good yet.  But when I try to format texts and use the fonts that comes with Ubuntu, exotic looking fonts like "Lohit Punjabi" which looks something like Egyptian and Arabic.  It won't work in NVU even if I can choose it.

Then my second question if I the webdesigner can't see the fonts offered by Ubuntu when using NVU how are Windows users supposed to see the Linux like fonts on their PCs?

PS.
NVU crashes when you try to format to the font "Hershey Gothic".

Basically you should just stick to using fonts that everybody has. (You can get windows fonts in Ubuntu too, the package is called msttcorefonts). Fonts are not anyhow submitted with the web page, so if the person viewing the page doesn't have the font you are using  he won't see it.

Best bet is to stick to using 3 basic fonts, Verdana, Arial and Times New Roman (although the last one isn't very good for on-screen publishing). Of course, if you are using CSS, you can define many fonts for your page. I usually use 'font-family: bitstream vera sans, verdana, sans-serif;" which will first try if the viewer has Bitstream Vera Sans font, if he doesn't the browser tries Verdana, and if even that isn't found then it uses the default sans-serif font as configured in the viewer's browser settings.

---

### Post by jingo811 on 2007-03-18
tnx I'm gonna do it like you do :KS

---

### Post by Pelekophori on 2007-03-18
There's a useful guide to what fonts are likely to be available in each of the most common operating systems (Windows, Mac and Linux) [[COLOR="Red"]here[/COLOR]]("http://www.webspaceworks.com/resources/fonts-web-typography/48/").

---

