---
title: "Laptops and Ubuntu"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Astatine on 2007-06-15
I haven't been able to get Ubuntu to work reliably on my laptop (Gateway M275 Tablet).  I've tried Ubuntu 7.04 , Xubuntu 7.04, and Ubuntu 6.10.  Is there a laptop specific version out there?

My problem lies in booting.  Ubuntu 7.04 worked intermittently (if I restarted it 10 or so times it will usually load).  I am not doing a dual boot.  In each case I simply downloaded the Live CD and installed.

Can anyone suggest a release that works well on laptops?

---

### Post by drs305 on 2007-06-15
> **Astatine said:**
> Can anyone suggest a release that works well on laptops?

I've installed ubuntu (edgy and feisty) on 3 laptops using the alternate CD without any problems. One was a really old laptop and the other 2 were fairly new. Never had a problem with the installation, and when I was first testing ubuntu I installed different versions many, many times.  Getting wireless to work was originally an issue, but the basic installation always went off without a hitch.

---

### Post by overdrank on 2007-06-15
> **Astatine said:**
> I haven't been able to get Ubuntu to work reliably on my laptop (Gateway M275 Tablet).  I've tried Ubuntu 7.04 , Xubuntu 7.04, and Ubuntu 6.10.  Is there a laptop specific version out there?

My problem lies in booting.  Ubuntu 7.04 worked intermittently (if I restarted it 10 or so times it will usually load).  I am not doing a dual boot.  In each case I simply downloaded the Live CD and installed.

Can anyone suggest a release that works well on laptops?

Hi I look at the specs on your system and it should be no problem running ubuntu. I have edgy and feisty running on two different laptops ( Micron and Dell). I assume you have enough ram and you have the intel graphics chipset?

---

### Post by scrooge_74 on 2007-06-15
This is old, but as you can see it works  [http://justlinux.com/forum/showthread.php?t=143956](http://justlinux.com/forum/showthread.php?t=143956)
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=353310](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=353310)
[http://www.linuxforums.org/forum/suse-linux-help/65054-sled-10-gateway-m275-tablet-enabling-wacom-tablet.html](http://www.linuxforums.org/forum/suse-linux-help/65054-sled-10-gateway-m275-tablet-enabling-wacom-tablet.html)

Keep googling around and you may find the solution you need....
you probably need to make some changes to config files

---

### Post by eoghanmurray on 2007-06-15
Laptops don't have any different ways of computing than desktops - there must be a problem with your hardware or your BIOS. Try hitting F2 or Delete at boot time (it usually tells you which one to enter setup), and restore to default settings. I had that problem a while back on an UMPC (Ultra Mobile Personal Computer) and that did the trick.

---

### Post by Astatine on 2007-06-15
Ok, problem solved.

A search through the archives (which I'm a bit embarrassed I didn't do first) shows that my problem is apparently fairly common with the Gateway M275.

To fix it, simply press "Fn+F3".

I'll tell my friends that this is an extra security feature.  You can't even *see* the log in screen if you don't know the "secret" keyboard code!

Just for the record, Ubuntu v. 7.04 works great on the Gateway M275.

Thanks for the help,
C.

---

