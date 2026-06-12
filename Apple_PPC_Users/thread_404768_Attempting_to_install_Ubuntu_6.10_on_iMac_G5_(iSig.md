---
title: "Attempting to install Ubuntu 6.10 on iMac G5 (iSight)"
date: 2007-04-08
forum: Apple PPC Users
---

### Post by konigindestraum on 2007-04-08
I have been attempting to do this for weeks now. PLEASE help me.

Here is as far as I've gotten:
I've followed the directions on the wiki here: [https://wiki.ubuntu.com/iMacG5revc]("http://wiki.ubuntu.com/iMacG5revC") to the 'T'

I don't know if there is some implied editing of the first yaboot.conf file, or what. I cannot get past the yaboot screen. I finally got it to recognize the 'CD' command, but it kept failing, and then I had to shut it down.

PLEASE help me.

---

### Post by stmiller on 2007-04-09
That wiki is WAY out of date and wrong. Also you should be aware that thermal support for isight iMac G5s did not ever work with Ubuntu 6.10. Fans would remain on 100%, and there were additional issues getting video to work right.

Get the latest Feisty beta release, and try that install disc. It has lots of the iMac thermal modules (windfarm) fixed. But no promises for the isight iMac G5- it's a different beast from the other G5 machines. 

Anyways, get the Feisty disc.

[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)

EDIT: Here is that infamous bug report:
[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34723](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34723)

---

### Post by konigindestraum on 2007-04-09
That's all fine and dandy, but when I burn it, HOW am I going to get it to run? Will this one ACTUALLY start up, or will it just pop up with a black screen after I boot the "live" option? Do I use the info on the WIKI to do it or what?

---

### Post by ZoiaGuyver on 2007-04-09
It should work straight off

A lot of work has been put into Feisty to out do all the other Ubuntu's.

I would recommend searching around see if anyone has had issues (i had a quick look and cant find anyone saying they have had problems with the iMac G5).

I havnt got a iMac G5 to test it on sorry so i cant help that much (only G5 PowerMac, G4 PowerMac's/G3 iMac's) i know feisty is fine on my G5 havnt had any real issues with it.

---

### Post by stmiller on 2007-04-09
> **konigindestraum said:**
> That's all fine and dandy, but when I burn it, HOW am I going to get it to run? Will this one ACTUALLY start up, or will it just pop up with a black screen after I boot the "live" option? Do I use the info on the WIKI to do it or what?

Well, neither of us have a G5 iMac iSight. I have a powermac G5. So I have no idea! But ubuntu needs more people to try on the isight imac model. So try it!

Forget that wiki! It is old and was never correct in the first place! Broadcom support is included in the new Feisty, if you have wireless. And try the 'safe video' live option (Whatever it's called) on that disc.

If none of this works, you may have to use the alternative CD and install with that.

---

