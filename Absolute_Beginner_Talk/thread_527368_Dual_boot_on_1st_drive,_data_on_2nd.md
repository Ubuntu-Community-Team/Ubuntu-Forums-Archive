---
title: "Dual boot on 1st drive, data on 2nd?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by y10 on 2007-08-16
I have two 250GB SATA hard drives. I want to dual boot XP/Ubuntu on the first drive. I want my 2nd drive to be a data storage drive for all my Windows stuff (a lot of stuff). Windows would be my main OS for the time being as I'd be experimenting with Ubuntu. Is this kind of setup possible? Thanks for any help?

---

### Post by alienexplorers on 2007-08-16
Yes it is.  Just load windows first leaving room for ubuntu and then load ubuntu.  You will have to adjust grub to let you boot windows as your primary os.

---

### Post by fumduck on 2007-08-16
[http://apcmag.com/5162/the_definitive_dual_booting_guide_linux_vista_and_xp]("http://apcmag.com/5162/the_definitive_dual_booting_guide_linux_vista_and_xp")


try that link for a dual booting guide it worked well for me.. I basically have the set up you want.. two sata drives..  except my spare does   /home and shared directory for windows and ubuntu. I ahve the spare drive formatted to ext 3  only because I know I will be not using windows as my primary and hope to be soon without it. But you might want to look up what  how you can partition your spare drive and  what to format it.  Only advice from me doing it is read.   I reformatted a few times until ( ithink) I got it the way I wanted.  and windows a can read and write to ext 3 .. with a little program. Thiough I think I read somewhere that either ext 2 or ext 3 might be an issue for corruption with windows????  probably google that I could be starting a myth. I am a newbie been at this for a few months, but with a little reading this shouldn't be so difficult.  Good luck  .

and here is the ubuntu wiki
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by y10 on 2007-08-16
Thanks very much for the speedy reply!

I've been told that when I have two hard drives, XP has to be on one and Ubuntu on the other. Is that right? It doesn't sound right to me. While I'm an Ubuntu newbie, I've used other distros for several years. I've dual booted XP and Fedora, SuSE, etc. and had my Windows data on a 2nd hard drive.

Anyway, what I'm being told is that I must have XP on one drive and Ubuntu on another. I'm being told that I can't set things up the way I want, i.e. XP and Ubuntu on my 1st hard drive with Windows data on the 2nd.

If you can give me any more clarification, that would be great.

---

### Post by y10 on 2007-08-16
Fumduck,
Thanks for the link and info on your own setup. Yeah, I plan to do some more research and experimenting.

---

### Post by fumduck on 2007-08-16
My set up is 1st drive       ubuntu/Xp/Pclinux/ spare partition       2nd drive   /home/ shared

[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")
another guide

---

### Post by MQMike on 2007-08-16
You can have XP and Linux on the same drive, no problem at all.
To make life easy on yourself, try to install Windows first, on the first (bootable) hard drive, the first partition (called (hd0,0) in GRUB-talk).
Then install Ubuntu and specify to the installer to put GRUB in the MBR (and so overwriting the XP MBR).  Ubuntu will then handle your dual booting with ease.

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

