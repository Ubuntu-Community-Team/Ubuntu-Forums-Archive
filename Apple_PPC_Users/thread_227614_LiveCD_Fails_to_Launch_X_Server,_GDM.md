---
title: "LiveCD Fails to Launch X Server, GDM"
date: 2006-08-02
forum: Apple PPC Users
---

### Post by PopeZaphod on 2006-08-02
I'm running a PowerMac G5 Dual 2.0Ghz with 2GB of RAM and an ATI Radeon 9800 XT connected to a Apple Studio Display CRT 17" monitor.  When I boot off of the 6.06 LTS CD I received in the mail, I press Enter at the boot: prompt, it goes through the boot process, but at the end I get a blue text screen with a notice saying that the X Server did not start properly and that GDM therefore will not run.

Has anyone see something similar?  I'd really like to take a look at Ubuntu.

---

### Post by avtolle on 2006-08-02
This thread may be helpful, if you have not seen it already: [http://www.ubuntuforums.org/showthread.php?t=225897](http://www.ubuntuforums.org/showthread.php?t=225897). Hope that helps.

---

### Post by PopeZaphod on 2006-08-03
Perhaps I'll give it a shot.  It does kind of sour the whole "Boot from the CD and it just works!" thing that I expected from Ubuntu, though.

---

### Post by avtolle on 2006-08-03
There is (was) an issue with the kernel on the live CD for ppc; there exist several threads dealing with various problems the posters have had. Since you specifically called out that you had the 17" display, I earlier posted the thread where at least some folks had had success. I suspect you will eventually need to edit the xorg.conf file, again several threads about this. I do not know, but at least one or two posters have implied, that once they are able to overcome the initial problem w/the screen, and download updates, that some of the later kernels have taken care of some of the problems. A commonly occurring problem w/ the G5 is the lack of fan control, but again, some have had that resolved by updates. Good luck.

---

### Post by Tofu on 2006-08-16
I too have a G5 with the same specifications... and the same ATI 9800 XT card. I can't install Ubuntu.

When using the latest install CD, I see the initial yaboot text screen, but then everything goes blank and the G5's fans go crazy fast.

It's all too hard for me :(

---

