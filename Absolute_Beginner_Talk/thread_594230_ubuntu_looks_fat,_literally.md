---
title: "ubuntu looks fat, literally"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by em11488 on 2007-10-27
I have ubuntu 7.04 installed on my computer and it looks rather fat. The font and everything takes up way more space than xp ever did. How can I make the font and nearly everything else compressed to have the efficient screen space of M$'s only good OS.

---

### Post by ed-koala on 2007-10-27
Go into *System - Preferences - Appearance* and you can set the fonts and sizes to your liking.  Enjoy!

---

### Post by LaRoza on 2007-10-27
> **em11488 said:**
> I have ubuntu 7.04 installed on my computer and it looks rather fat. The font and everything takes up way more space than xp ever did. How can I make the font and nearly everything else compressed to have the efficient screen space of M$'s only good OS.

Is your resolution up to your monitors abilities? If you do not have the video driver installed, the resolution will be 800x600.

---

### Post by em11488 on 2007-10-27
but which font looks the best or most like xp.

---

### Post by por100pre1 on 2007-10-27
**Appearance** is NOT present in Feisty. Use **System> Preferences> Font**:

```
gnome-font-properties
```

---

### Post by por100pre1 on 2007-10-27
> **em11488 said:**
> but which font looks the best or most like xp.

I use FreeSans. It is not like xp fonts, but it looks nice.
[COLOR="Red"][B]
EDIT: Sorry for two contiguous posts! :([/B][/COLOR]
**EDIT: I'll post again here to compensate for double posting:**

You can create a .fonts folder in your user folder:

```
mkdir ~/.fonts
```

put in there any ttf fonts you want, log out and log back in. :)

---

### Post by ed-koala on 2007-10-27
I believe XP and other microsoft default font is Ariel.  Didn't see that in my font choices, but Sans, which is the font I'm using, looks good to me.

If you really want Microsoft fonts, use Synaptic Package Manager to install the msttcorefonts package, that has all the XP fonts for you to use.

---

### Post by kristjans on 2007-10-27
I thought MS used Tahoma? It's really a quite nice font. Personally, however, I use 7 point Bitstream Vera Sans.

e: [Confirmed](http://en.wikipedia.org/wiki/Tahoma_(typeface)) that MS uses Tahoma
[quote=Wikipedia]It is also the default screen font used by Windows 2000, Windows XP, and Windows Server 2003 (replacing MS Sans Serif) and is also used for Sega's Dreamcast. Bundled for inclusion in the font library of Windows, the typeface is widely used as an alternative to Arial.[/quote]

---

