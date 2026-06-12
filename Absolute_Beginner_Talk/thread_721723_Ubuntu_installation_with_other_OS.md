---
title: "Ubuntu installation with other OS"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by DaHiA on 2008-03-11
Hello,
I'm completely newbie to Ubuntu and Linux world but i believe it's my time to get out from MS cave.

Well, i plan to install Ubuntu 7 on my laptop side to side with MS vista till i get learn about Ubuntu.
But, i don't like to create separate partition on my HDD for Ubuntu. in other words, i'd like to have both Ubuntu and Vista on both partition C: -15GB free-
How to perform such installation without losing Vista or any of my stored data on C:
P.S: I'm afraid Ubuntu would format the partition prior to installing itself into, right?

Thank you

---

### Post by SunnyRabbiera on 2008-03-11
well you can actually try Ubuntu without even installing it with the use of the Live CD.
The live CD is sort of like a trial, ubuntu will not install on your system unless you want it to.
With the live CD you can evaluate the system, learn about how linux works without even touching your hard drive.
and then when you want to you can set ubuntu to dual boot, make sure to do some reading on dual booting before committing to it.

---

### Post by neurostu on 2008-03-11
So, as far as I know, you can't install ubuntu on the same partition as Vista.

Ubuntu and Vista use two completely different file systems  and they aren't compatbile with each other.

Why are you worried about creating another parition. There are plenty of tutorials on how to create the 2nd partition and people almost always get it working without any major problems.

If you want to keep one partition it will have either Windows of Ubuntu, if you want both OSes you are going to need 2 partitions.

---

### Post by kamitsukai on 2008-03-11
Why not try wubi? ([http://wubi-installer.org/](http://wubi-installer.org/))

---

### Post by bumanie on 2008-03-11
Wubi is your best bet if you want to avoid partitioning your drive. In fact if you wait 6-7 weeks for hardy heron's release, wubi is going to be supported at the kernel level (I believe).

---

### Post by DaHiA on 2008-03-16
Thank you everybody :)
> **kamitsukai said:**
> Why not try wubi? ([http://wubi-installer.org/](http://wubi-installer.org/))
Why does Wubi try to download ubuntu with no other options to use local CD?
and why its downloading ubuntu 7.04 not the latest !

Did i miss something?

---

### Post by theRightNee on 2008-03-16
7.04 is not extremely different from 7.10 and will give you a good feel for ubuntu...and as for why not the latest, perhaps at the time wubi was written 7.04 was the latest? no idea

---

### Post by sandysandy on 2008-03-16
do not worry about partitioning ur drive. with gparted live CD its pretty OK.

here are some links for dual booting Vista and Ubuntu

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

[http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux)

here is link to thread on same issue

[http://ubuntuforums.org/showthread.php?t=207870](http://ubuntuforums.org/showthread.php?t=207870)

regards

---

### Post by DaHiA on 2008-03-16
Thank you 
> **DaHiA said:**
> Why does Wubi try to download ubuntu with no other options to use local CD?
any idea how to use Live CD with Wubi instead of downloading  the whole ubuntu ?

---

### Post by DaHiA on 2008-03-16
> **theRightNee said:**
> 7.04 is not extremely different from 7.10 and will give you a good feel for ubuntu...and as for why not the latest, perhaps at the time wubi was written 7.04 was the latest? no idea
Actually there is another versions for 7.10 and 8.04
[http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)

---

### Post by sandysandy on 2008-03-16
> **DaHiA said:**
> Thank you 

any idea how to use Live CD with Wubi instead of downloading  the whole ubuntu ?

have a look at this link

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

it talks of CD approach but says it will work with Alternate Ubuntu install CD.

some other links

[http://howtoforge.com/wubi_ubuntu_on_windows](http://howtoforge.com/wubi_ubuntu_on_windows)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

hope these help

regards

---

### Post by jediscout on 2008-03-16
So long as Microsoft has been loaded first, it's pretty easy.. Although you did mention something about only 15 gigs. Is that all you have or just what you got left? You'll need at least 30 gigs for a dual-boot like I use. I only have 38 gigs available to me on this old laptop I have and allow 25 gigs for XP and 12  for Ubuntu. Way things are going lately, I may just have to reverse that. lol  :)

---

