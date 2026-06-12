---
title: "Wireless trouble, unsure of what could be the problem."
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by WhoSimplex on 2008-01-13
Hey all,

I finally decided to give Ubuntu a shot after looking at it for awhile because I'm bored with Windows, I guess is how I could put it.

I tried a Live CD last night, but since I have a GeForce 8600GT, it'd go black screen and just sit there. So I installed with the text installer or whatever, and now I'm booting in recovery mode (I think is what it's called) to go into Ubuntu. And also, I'm dual booting Windows XP if it makes a difference.

Once in recovery mode and I get to where I can type, I go sudo /etc/init.d/gdm restart, and it loads up Ubuntu. I guess that makes it use the bad nVidia drivers rather than the accelerated ones, because the accelerated ones are on the restricted drivers list and are disabled. Okay, so I don't get to use all the fancy desktop animations until I get internet and can get Envy. That works for me.

So then I follow all the instructions I've seen on google to get my Netgear WG111T to work. I installed ndiswrapper and ndiswrapperutil's from Synaptic and tried doing it text based. Didn't work. I downloaded new versions of them and got ndisgtk, still doesn't work. Although I found out that at first that the drivers I was using were too old, so I upgraded to 1.2 which some other people were using and it still doesn't work; but hey, at least it says that my device is there for one of them. If I boot up my computer and don't mess with the card, the device is active on netwg11t.inf. If I unplug it and plug it back in, it's active on athfmwdl.inf. But it never starts flashing its blue light, and I never get anything on my Networking configurator, and ifconfig doesn't show Wlan0 like it supposedly should.

I don't know what else to do. I've been messing with it for 8-9 hours now and still haven't found a solution. So I guess I've finally decided to come here for some help, lol.

System specs are as follows.
AMD Athlon64 x2 3800+
ASUS M2N-E SLI nForce 500 Chipset
2GB OCZ Platinum Revision 2 DDR2-800 RAM
80GB WD SATA HD, pretty basic
Netgear WG111T Wireless USB thingy
eVGA GeForce 8600GT
Windows XP Professional on one partition, Ubuntu 7.10 on the other.

Did I do everything right? Should I do anything else? I'm at a loss here. I guess I could try downgrading to 7.4, but I'm not sure how to uninstall Ubuntu. (lol)

Thanks for your time!

---

### Post by WhoSimplex on 2008-01-13
Bump.

Guess I'll try downloading 7.4 tonight.

---

### Post by WhoSimplex on 2008-01-13
One last bump before I go to sleep.

Anyone know? :(

---

### Post by Jake90 on 2008-01-14
Uninstalling gutsy... this is a little tricky but I think the best way would be to delete the whole drive. Go to run and type in compmgmt. On the left panel click on disk management.Here is where it gets tricky, One drive is for windows and you can't delete that from windows even if you wanted to. I don't know how nay other drives you have but one of them has linux on it. Right click on that one and select delete volume. That should put the drive back into the unallocated state and you can install feisty on it.

---

### Post by syn` on 2008-01-14
I don't think he's on a laptop.

---

### Post by syn` on 2008-01-14
Anyone know anything to help him out? :\

---

### Post by WhoSimplex on 2008-01-16
Bump because I'd still like to get it working. :)

Edit: Forgot to say, still having the problem even after downgrading to Feisty Fawn (7.04).

---

### Post by WhoSimplex on 2008-01-17
Bump.

I guess if no one can help me out in the next couple days, I'll go buy an ethernet cable so I can wire myself up. Was just hoping I could keep my wireless going; I like not having cables all over the floor.:lolflag:

---

