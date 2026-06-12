---
title: "Installing Ubuntu 16.04 on macbook pro mid 2012 13&quot;"
date: 2017-01-23
forum: Apple Hardware Users
---

### Post by ellevy12 on 2017-01-23
Hello

I would like to ask for help from anyone who installed ubuntu on this type of macbook (pro, mid 2012 13") , as i'd like to install on my own mac on the following weeks. i managed to understand mostly the entire procedure  , however i have 2 major questions:

1. is it possible to solely install ubuntu on my mac hard drive? if so - how?

2. in case of removing mac os x entirely - is it possible to recover it using a USB drive with mac os x on it OR internet recovery using cmd+R key? 

Thanks

---

### Post by &amp;KyT$0P# on 2017-01-23
1) Don't do that.  You will find you just can't get some things to work without using Mac OS - for example, [setting up graphics]("https://ubuntuforums.org/showthread.php?t=2335586&page=2&p=13539492&viewfull=1#post13539492").

2) I think it would erase Ubuntu in that case.  I know I've lost partitions that way.

It should be possible in theory to install Mac OS directly to an external disk, but I've never actually tried to do that.

---

### Post by g33zr on 2017-01-23
You have 3 options to install Ubuntu on your MacBook:

1. Download the ISO and then install it in VirtualBox
2. Dual boot using [rEFInd]("http://www.rodsbooks.com/refind/installing.html#osx")
3. Wipe OSX and install Ubuntu

If you haven't installed Linux on you MacBook yet, then I suggest trying Ubuntu in VirtualBox first. If that works for you, try dual-booting. If you have experience in dual-booting Linux and feel comfortable with re-installing Mac OSX, you can try option 3. 

FWIW, I've run only Linux on an old--now retired--MacBook and on a 2009 iMac and never missed OSX. Everything worked fine, depending on the Linux distro. You should have no problem with Ubuntu.

---

### Post by ellevy12 on 2017-01-24
Hi,  and thanks for replying.  


I have some experience with Ubuntu on older late 2006 MacBook and I am feeling very comfortable with switching.  So I guess a good route would be to install Mac OS x and Ubuntu using dual boot and just use Ubuntu?

---

### Post by g33zr on 2017-01-24
Installing MacOS and just using Ubuntu is a good choice if you want to continue firmware updates on the Mac side. You could, for example, give the Mac and restore partitions a combined total of 100 GB and the rest to Ubuntu. Good luck.

---

### Post by &amp;KyT$0P# on 2017-01-24
> **ellevy12 said:**
> So I guess a good route would be to install Mac OS x and Ubuntu using dual boot and just use Ubuntu?
Yes.  That's how I did and it works well.  Your MacBook Pro being similar age as mine, this should work well for you too.

Happy Ubuntu-ing. :)

---

### Post by jeromio on 2017-02-02
FYI, 16.10 on a 2010 7,1 is not working very well :(
X randomly dies (either black screen + dead keyboard or just dead keyboard - unrecoverable). Coupled with WiFi randomly not working on boot (also unrecoverable - only known soln. is just to keep rebooting until it magically works).

---

