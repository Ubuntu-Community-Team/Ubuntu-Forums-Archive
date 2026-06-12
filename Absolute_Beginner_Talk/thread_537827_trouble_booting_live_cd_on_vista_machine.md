---
title: "trouble booting live cd on vista machine"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by billysensible on 2007-08-29
Hey ubuntunites

I'm trying to give ubuntu a test drive on my laptop. please bear with me as i have a pretty limited knowledge of computers (relatively speaking), and frankly, this question is kind of embarrassing. 

How do you boot from a live cd? I burned the iso of a ubuntu 7.04 (or whichever the most recent one is) and my understanding is that you just restart your computer with the live cd in. And yet every time i try this, Vista starts up automatically like i've done nothing different. Is there some crucial step i'm missing?

Any help would be appreciated.

---

### Post by kellemes on 2007-08-29
Just to be sure you better check you burned the iso like it should..
[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

When it's burned correct it should be bootable.. when it does not boot it will probably have to do with the bootorder of devices in your BIOS.
You need to first start your pc and tap your "enter-BIOS key".. often this is DEL or F2 I believe.. This will give you access to the BIOS-settings. See to it the cd/dvd-drive is first in the bootorder, so at boot the Ubuntu-Livesystem will be booted before other devices (like harddisk).

---

### Post by jclmusic on 2007-08-29
when the computer first boots up, press the key it tells u to in order to get into the BIOS settings (usually either delete or F1). then change the boot order to boot from CD first. 

hope this helps. if u want a more step by step howto do a search and it should come up, it's a common problem for newbies, so don't worry about it :)

---

### Post by jclmusic on 2007-08-29
lol beat me to it! we must have been typing at the same time...

---

### Post by cubeist on 2007-08-29
Sometimes we ubuntunites are just too supportive! :)
> **jclmusic said:**
> lol beat me to it! we must have been typing at the same time...

---

