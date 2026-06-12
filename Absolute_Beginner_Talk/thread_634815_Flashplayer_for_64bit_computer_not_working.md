---
title: "Flashplayer for 64bit computer not working"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by planet-reptile on 2007-12-08
Hi.
How do i get Flashplayer working for 64bit computer?

---

### Post by roaldz on 2007-12-08
> **planet-reptile said:**
> Hi.
How do i get Flashplayer working for 64bit computer?

Well, I suggest you first look in the 64 Bit forums, you´re not the first one with this question.

Okay... I assume you´re using Ubuntu 7.10 Gutsy and Mozilla Firefox. Then just go to synaptic and search for ¨flashplugin-nonfree¨. If you install that, it should install it properly.

---

### Post by Johnny3 on 2007-12-08
Go to system/administration/ Synaptic Package manager Search for flashplugin-nofree. Install.
If it is installed and not working try completely uninstall then restart and install again.
Hope this helps
Johnny3
Gainesville Fl

---

### Post by KhaaL on 2007-12-08
Since flashplayer only exist for 32 architecture, I think you also need the 32 bit firefox. look in [the 64bit forums]("http://ubuntuforums.org/forumdisplay.php?f=134")

---

### Post by roaldz on 2007-12-09
> **KhaaL said:**
> Since flashplayer only exist for 32 architecture, I think you also need the 32 bit firefox. look in [the 64bit forums]("http://ubuntuforums.org/forumdisplay.php?f=134")

That true for the flashplayer part. You can use the 32bit flashplayer in a 64bit firefox. You need NSpluginWrapper. In gutsy, if you install flashplugin-nonfree, it automagically configures nspluginwrapper. 

You only have to sudo apt-get install flashplugin-nonfree, or install flashplugin-nonfree with synaptic.

Roald

---

