---
title: "Uninstalling Ubuntu &amp; fixing XP MBR"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by beaulanger on 2007-02-18
I don't know if you good folks can help me, seeing as this is a hardware problem.
My homebuilt PC has had a boot problem for a couple of years now that apparently isn't solvable without a new motherboard. When I boot the screen is almost always scrambled. It is not a video card or monitor problem. Rarely can I see the BIOS screen nor a boot CD.  When it goes into GRUB I just know to either hit <enter> for WinXP or arrow down for Ubuntu, the way I have the sequence set up in menu.lst. Once either operating system loads everything is fine. Seeing as most of my hardware does not work with Ubuntu I want to uninstall it and reclaim the 2 GB + I have allocated to it.

I can't see the screen with my WinXP CD to get into Recovery Mode to change back the MBR. If I could I do have GParted on a boot CD to delete the Ubuntu partition.

Maybe if I knew the sequence of WinXP Recovery Mode at least I might be able to blindly fix the MBR without visualizing it on my screen. I guess I am out of luck with GParted. 

Any ideas? I'm open to anything. Thank you.

Beau

---

### Post by solar george on 2007-02-18
[re-installing-windows-xp-boot-loader.html]("http://www.linuxforums.org/forum/redhat-fedora-linux-help/50847-removing-fedora-re-installing-windows-xp-boot-loader.html")

This might help.

Try the smart boot manager.

---

### Post by OBnascar on 2007-02-18
> **beaulanger said:**
> Any ideas? I'm open to anything. Thank you.
Beau

Or you could try the Super Grub  Disk live CD, it can deal with Lilo, Grub, or the MBR:
[COLOR="Blue"]**_[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")_**[/COLOR]

and download it here:
[COLOR="Blue"]**_[http://forjamari.linex.org/frs/?group_id=61&release_id=414](http://forjamari.linex.org/frs/?group_id=61&release_id=414)_**[/COLOR]

---

### Post by beaulanger on 2007-02-18
Thanks. I booted with the Ubuntu CD and did anotehr install so I could use the GParted there and shrink my Ubuntu 21GB partition down to 3GB. Somehow it trashed my WinXP partition.
I just went out and bought a new computer. Thanks.

---

