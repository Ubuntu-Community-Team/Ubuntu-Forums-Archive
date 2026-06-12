---
title: "Ubuntu emulation without rebooting macbook"
date: 2007-02-16
forum: Apple Intel Users
---

### Post by zugvogel on 2007-02-16
Hello. I recently got a macbook (before this I used linux at work and at home for 2 years). The mac has a lot of things that just didn't work in ubuntu, but for everything that works there is something else that I find I can only do in linux. Therefore, I really need to install linux on my macbook too.

My question is if there is software that will allow me to run ubuntu in a window without needing to re-boot the computer. This would really help me a lot. Whether it's commercial or free software it doesn't matter. As long as it works! I looked around on the internet for a bit but can't find anything.

Thanks!

ps, If I get time I will try to write up what I found by switching from linux to mac. There's not so much information on the internet (mainly only Windows->mac, Windows->Linux and Mac->Linux)

---

### Post by grazie on 2007-02-16
Hi zugvogel,

Although you have an Apple Mac this is a PPC forum, so your chances of getting the answer you're after are slim. However, I also know a little about x86, so you are in luck (this time).

You have the choice of qemu (in the repos), virtualbox (not in the repos) and vmware which is commercial software. VMWare do a free player and other products which you can demo for free. There are others, but they're probably not worth considering. I just tried virtualbox yesterday for the first time and was very impressed. I wouldn't bother with the other choices unless you get specific problems with virtualbox.

Wouldn't it be great if virtualbox could support PPC!

---

### Post by grazie on 2007-02-16
There's now a new forum, [Apple Intel Users]("http://www.ubuntuforums.org/forumdisplay.php?f=211"), for all topics regarding Apples Macs with Intel processors :)

---

### Post by incubus on 2007-02-16
I just got a Macbook.  I tried VMware Fusion (still beta, but public) and Parallels.  VMware works fine, but Parallels is much faster.  I suspect it's because VMware is logging all the debug messages to help their own testing.  It's got potential.  

Parallels takes full advantage of VT, so it runs close to native speed.  If money is not an issue, I would recommend it.  Once you get used to Ubuntu, you may think of switching completely.

incubus

---

### Post by grazie on 2007-02-16
Yeah, I didn't mention Parrallels as I think it's been designed to run Windows (guest) on OS X (host). Whether it will support Linux as a guest I don't know, but it would be very silly if it didn't IMHO. You didn't exactly state it, but on re-reading your post it seems that you may want to run Ubuntu as a guest on OS X host. There's no Virtualbox for this config. However, if you use Ubuntu as the host and Windows or Ubuntu as the guest, I wouldn't see any problems with that.

NOTE OF CAUTION

It appears that installing Virtualbox (outside apt) may be breaking apt on Ubuntu for some. I installed VirtualBox on a different distro and I've had no apt probelms at all myself.

---

### Post by incubus on 2007-02-17
grazie,

You're right, I forgot to mention that.  Parallels is optimized for windows, but it will run Linux.  There are some issues with Ubuntu, but I think you can get it running.  It will give you some options like Fedora, Debian, etc, so Debian is our closest relative.

But in short, the OP has lots of options to choose from.

incubus

---

### Post by zugvogel on 2007-02-18
Hello. Thanks for your replies. I downloaded Parallels (on their free trial). It seems to work really well - ubuntu is as quick as it used to be on my old computer. I also found and tried "Q" based on "Qemu" but had a lot of problems so eventually gave up on that.

So it seems I might go the parallels route and take advantage of the good exchange rate on the dollar at the moment...

Thanks for your help.

---

