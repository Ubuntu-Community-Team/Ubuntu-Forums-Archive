---
title: "Internet wont work only in Ubuntu"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Aussie on 2008-01-24
Hello all,

I did a fresh install 7.10 last night and now the internet wont work through firefox.  It sort of works through the terminal.  The modem is hooked up to a netgear wireless router, however the ubuntu box is hooked up wired from the router.  

I'm able to ping [www.google.com](www.google.com) and get pings back however when i try wget [www.google.com](www.google.com) it says it cannot find connection to host.  I've got an ip when i run ifconfig and enabled my network card eth0 and set it to DHCP in the system settings.

The strange thing is, when i disconnect the network cable and plug the same cable into my macbook, I am able to access the internet, which makes me think that it's not the router settings.  I also don't have firestarter installed so it can't be that.

I'm at a loss.  Any thoughts would be great.

Thanks.

---

### Post by mmb1 on 2008-01-24
What kind of hardware did you install on?

---

### Post by Aussie on 2008-01-24
An old AMD Athlon 1800xp with 512mb ram.  I got it back in 2002 so i can't remember the motherboad specs.  The network card is not part of the motherboard, it was a PCI card that i installed.  I'm at work at the moment so I can't give more speciffic details...sorry.

It is quite strange as the net used to work with Breezy and Dapper straight away.

-Thanks.

---

### Post by jingo811 on 2008-01-24
Do you have a dual boot on this PC so that you can test the Web browser connectivity with Windows XP?  If it fails in Windows also then I'm suspecting your wired NIC is bad.

Also maybe you just burned your Ubuntu 7.10 disc poorly since you made Breezy and Dapper work previously.

---

### Post by Aussie on 2008-01-24
Sorry I'm running a full install of Ubuntu.  Could you explain what the wired NIC means please?  Does that mean my network card?

Thanks.

Edit: Quite possible on the dodgy disc burn as the CD's i'm using aren't the greatest, however that's all i had lying around.

---

### Post by jingo811 on 2008-01-24
wired NIC = wired Network Interface Card ; in your case the PCI card you mentioned but it doesn't seem to be the main problem at this stage.  I'm suspecthing this:
> 
Also maybe you just burned your Ubuntu 7.10 disc poorly since you made Breezy and Dapper work previously.

Follow this guide next time you burn your 7.10 disc.  md5 check the .iso file and burn at the rate of 4x that speed has worked for me before.  Around 30 minutes waiting time.
[https://help.ubuntu.com/community/BurningIsoHowto/](https://help.ubuntu.com/community/BurningIsoHowto/)

---

### Post by Aussie on 2008-01-24
> **jingo811 said:**
> wired NIC = wired Network Interface Card ; in your case the PCI card you mentioned but it doesn't seem to be the main problem at this stage.  I'm suspecthing this:


Follow this guide next time you burn your 7.10 disc.  md5 check the .iso file and burn at the rate of 4x that speed has worked for me before.  Around 30 minutes waiting time.
[https://help.ubuntu.com/community/BurningIsoHowto/](https://help.ubuntu.com/community/BurningIsoHowto/)

Cool, I'll give that a shot.  I burned it using disk utility in osx, and the first time had an error.  So i'll get some better disks, read the guide and give it a go.

Thanks for your help.

---

### Post by jingo811 on 2008-01-25
Just remember to md5 check the .iso file before you burn it to a disc.

---

