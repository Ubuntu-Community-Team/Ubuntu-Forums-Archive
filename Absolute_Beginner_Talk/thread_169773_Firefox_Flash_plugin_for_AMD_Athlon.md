---
title: "Firefox Flash plugin for AMD Athlon"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by cls1chuck on 2006-05-03
Hi,
I have the release of Firefox that came w/BB (5.10) - I think it's 1.0.8.  I run a 32-bit AMD (Athlon XP).  I cannot get the Flash plugin to work.  I saw in one thread or somewhere that the linux version only works for Intel.  Is that true?  I've tried everything I've found in the online resources.
ANY HELP would be appreciated!

---

### Post by Qrk on 2006-05-03
The Athlon XP is an intell class cpu, so flash will work with it. Have you tried the non-free flash plugin in the repositories? Have you tried automatix?

---

### Post by cls1chuck on 2006-05-03
Not sure what you mean by 'non-free flash plugin' - what category is it in in the Pkg Mgr?
Also, have not tried Automatix - looks like it installs a LOT of stuff besides that?
FYI, if I go to about:plugins, I show Shockwave Flash (libflashplayer.so), but every web site I go to that requires the plugin tells me it's not installed.

---

### Post by Qrk on 2006-05-03
Once you've enabled the extra repositories, there should be a plugin for non-free flash in muliverse.
  ```
sudo apt-get install flashplayer-mozilla
```

Note that this is the Flash Player, not shockwave. Shockwave isn't released for Linux.

---

### Post by cls1chuck on 2006-05-03
that's how I initially installed it, I believe.  I will try again though.  Is it ok to do so if I've already done this?  And what should my Firefox plugin info show?

Thanks!

---

### Post by dcstar on 2006-05-04
[QUOTE=cls1chuck]that's how I initially installed it, I believe.  I will try again though.  Is it ok to do so if I've already done this?  And what should my Firefox plugin info show?

Thanks![/QUOTE]
```
Shockwave Flash

    File name: **libflash-mozplugin.so**
    Flash Movie player Version 0.4.12 compatible with Shockwave Flash 4.0

    Shockwave is a trademark of Macromedia®

    GPLFLash homepage : gplflash.sf.net

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Flash Plugin 	swf 	Yes
application/x-futuresplash 	Future Splash 	spl 	Yes
```
and/or
```
Shockwave Flash

    File name: **libflashplayer.so**
    Shockwave Flash 7.0 r61

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```
Those files (or links to them) should be in your Firefox Plugins directory.

BTW, an Athlon optimised version of Firefox 1.5.0.3 (Swiftfox) is available.

---

