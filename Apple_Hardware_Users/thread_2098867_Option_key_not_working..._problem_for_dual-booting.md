---
title: "Option key not working... problem for dual-booting"
date: 2012-12-27
forum: Apple Hardware Users
---

### Post by canhoto on 2012-12-27
Hi.

I'm about to use my second Mac (a Macbook) with Ubuntu (or Kubuntu) as my main OS, keeping Mac OS just for the (very few and rare) things that I can only do with a Mac.

I'll use Boot Camp to do it. But I'm facing a problem:

My option key stopped working when I boot and I try to use it (for  instance, to choose another startup disk or to reset the PRAM). It works  normally when I'm using the computer afterwords (after signing in).  Also, when my login screen appears, there are a bunch of dots filling in  the password field, like if the computer was filling in the password  itself (but it doesn't, I have to delete the chain of dots and enter my  password). But this doesn't happen when I try (without success) to use  the option key on boot.

The same happens when I press "C" to choose a CD as startup disk. The only way I have to startup from another disk is to go to Mac OS System Settings and choose a CD as the startup disk. With this I made a clean install of Mac OS, which led to nothing, since the option and other boot keys keep not working on boot. 

But I could just boot from an Ubuntu installation CD using Mac OS Startup Disk settings and install Ubuntu. Then I just would have to choose the Boot Camp Ubuntu partition as a Startup Disk and it would always boot from Ubuntu. The problem is: how would I come back to Mac OS when needed? Is there any way of choosing a startup disk from within Ubuntu or Kubuntu? Or is there an alternative way of choosing the boot partition? Or a way to fix the option key problem?

Any help would be welcome.

Thanks

---

### Post by canhoto on 2012-12-27
Well, I partially solved the problem by installing rEFIT on the Mac. I don't need the option key. 
But if someome as a clue about how to solve the key problem, I would still appreciate it.

---

### Post by iMac71 on 2012-12-28
I've found a couple of links which might indicate how to solve your problem:
[http://reviews.cnet.com/8301-13727_7-10423838-263.html](http://reviews.cnet.com/8301-13727_7-10423838-263.html) (especially the part relative to Plist corruption)
[http://forums.macrumors.com/showthread.php?t=1175823](http://forums.macrumors.com/showthread.php?t=1175823) (especially posts #2 and #3, even if they're relative to Apple's aluminium keyboard).
Hope they're somehow helpful for you.

---

### Post by canhoto on 2013-05-03
I solved it by installing Refit on the Mac and booting with it. I don't need the Alt key for that.

---

