---
title: "Display's native res not recognized?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by irskep on 2007-05-23
(Since I'm on a PPC machine, I first posted this in that forum, but didn't get any responses, and it's really annoying having work in 1024x768, so I came over here.)

I'm on a clunky-looking 1 gHz eMac. Ubuntu refuses to recognize any resolution besides 1024x768, even though my display's native resolution is 1280x960. I tried adding the text below to /etc/X11/xorg.conf in the appropriate place, but it didn't do a thing. Only 1024x768 shows up in Screen Resolution. What am I missing?

```
	SubSection "Display"
		Depth		24
		Modes		"1280x960"
	EndSubSection
```

(Just installed Ubuntu the other day, but I write Mac games in my spare time, so I'm not entirely clueless. I at least got dual booting to work with no hassle.)

---

### Post by tanguyr on 2007-05-23
Hello irskep,

What kind of video card does an eMac have? You may need to install a driver for your specific card to enable higher resolutions. 

Regs,
/t

---

### Post by irskep on 2007-05-23
Thanks for the response. I should have thought to post that, too.

It's a Radeon 7500.

---

### Post by tanguyr on 2007-05-24
Which driver are you using now?

Check your /etc/X11/xorg.conf file - should be "radeon" or "ati", not "vesa"

Regs,
/t

---

### Post by irskep on 2007-05-24
Ati.

---

### Post by tanguyr on 2007-05-24
maybe try using the "radeon" driver instead of the "ati" driver (whoever names these needs some help or better imagination).

[http://www.thinkwiki.org/wiki/Radeon](http://www.thinkwiki.org/wiki/Radeon) 

I'm going to blindly assume that you are comfortable using the console just in case this leaves your machine incapable of starting x... (it's also a good idea to install a text mode browser like elinks... just in case)

Regs,
/t

---

