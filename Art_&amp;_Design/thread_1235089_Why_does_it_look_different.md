---
title: "Why does it look different?"
date: 2009-08-08
forum: Art &amp; Design
---

### Post by lnvisible on 2009-08-08
First of all, I don't know if this is the correct section to ask this, if it is not I hope someone will move the post or at least tell me where to repost it.

I want to know why the characters in ubuntu look so nice, more precisely in the terminal emulator that I've been using in xubuntu, but I think this is the forum for xubuntu. I am using debian now, and even if the font and the program used are the same, it looks different. Specifically I am using monospace as my font, I have tryied with dejavu sans mono and it is exactly the same.

How is that done, should I install a package or something?

Thank you very much.

---

### Post by Newfoundlander on 2009-08-09
Could you post a screenshot of your terminal(s) so we can see what you mean?

The font size may be different and this can either improve or lessen the rendering of the characters.  Are the "Appearance Preferences" the same on your Xbuntu setup (the smoothness of the font rendering)?

---

### Post by kiddo on 2009-08-09
The reason is that since Ubuntu 9.04, subpixel hinting with "slight" hinting is activated by default. This in Appearance, in the advanced font properties.

The fact that the font hinting is "slight" makes it much more conform to the real shape of the font, compared to "full" hinting.

---

### Post by lnvisible on 2009-08-09
Yes, that's it, thanks! I'm uploading the screen captures just in case someone is interested.

these are debian12, ubuntu12, debian10, ubuntu10 (the number is the font size)

[[IMG]http://img12.imageshack.us/img12/2992/debian.th.png[/IMG]]("http://img12.imageshack.us/i/debian.png/")[[IMG]http://img7.imageshack.us/img7/268/ubuntus.th.png[/IMG]]("http://img7.imageshack.us/i/ubuntus.png/")[[IMG]http://img17.imageshack.us/img17/9589/debian10.th.png[/IMG]]("http://img17.imageshack.us/i/debian10.png/")[[IMG]http://img524.imageshack.us/img524/8913/ubuntu10.th.png[/IMG]]("http://img524.imageshack.us/i/ubuntu10.png/")

---

### Post by Newfoundlander on 2009-08-09
I've noticed that rounded parts of characters sometimes look flattened or squished when they are smoothed by rendering.  I usually increase them by a point size or two and they look much better.

Glad you have your fonts looking better now.

---

### Post by alex.rayu on 2009-08-10
You are right! Characters in Ubuntu do look VERY sexy. I am in Windows 7 right now, and feel hurt by the blurred fonts morally =) Ubuntu does something to them that they look so good.

---

