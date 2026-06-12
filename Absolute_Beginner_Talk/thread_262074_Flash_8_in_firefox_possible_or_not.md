---
title: "Flash 8 in firefox possible or not?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by uncreative on 2006-09-21
OK, I went through automatix and installed the flash stuff that is in there, but I don't think that is Flash 8

Is getting Flash 8 possible?

I am trying to get to this website [http://www.texaschainsawmovie.com](http://www.texaschainsawmovie.com) and it keeps booting me back to [http://www.texaschainsawmovie.com/noflash.html](http://www.texaschainsawmovie.com/noflash.html)

I know, hi-brow stuff I'm trying to view ;)

---

### Post by CarpKing on 2006-09-21
Flash 7 is the highest version of flash for which a Linux plugin was released.  They are currently working on a Flash 9 plugin, but it isn't expected out until early next year.  A workaround would be to install Firefox for Windows and its plugins through Wine and use it whenever you need to view a webpage such as this.

---

### Post by hyper_ch on 2006-09-21
Automatix does a flash player install but I can't tell what version it is...

---

### Post by bswilson on 2006-09-21
> **sjau said:**
> Automatix does a flash player install but I can't tell what version it is...

It is the version 7 plugin previously mentioned.

---

### Post by Marsolin on 2006-09-21
As another possibility, you could try [Gnash]("http://linuxappfinder.com/package/gnash"). It's a free, open source flash player for GNU/Linux. It mostly support Flash version 7 so far, but some version 8 features are supported already so it might allow you to access the site.

---

### Post by jordanmthomas on 2006-09-21
You can edit 
~/.mozilla/firefox/pluginr&#8203;eg.dat
and change 
```
Shockwave Flash 7.0 r63:$
```
to
```
Shockwave Flash 9.0 r63:$
```

It works for everything flash 9 I've tried!  Don't be surprised if Firefox crashes or something though if a site really needs flash 8 / 9 instead of just saying it does.

---

### Post by aysiu on 2006-09-21
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by uncreative on 2006-09-21
Hey thanks for the great responses!

---

