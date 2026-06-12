---
title: "setting up a home network (Gutsy + Vista)"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by zachthejones on 2008-01-03
Okay, long story short, my wife got a new laptop with Vista on it, and I got her old laptop, installed Gutsy on it, no problems. I want to have a home network where I can access my HP printer/scanner which is on my Gutsy Desktop (it's actually a dual boot, but XP has so much dust on it now...:mrgreen:).  I want my wife and I to be able to print remotely on the printer. I also want us to be able to back up our essential files on it. And I'd like to have some sort of synch program to synch/backup certain files files which I modify regularly.  So my goals are three-fold:

1) everybody uses the desktop's printer (Gutsy)
2) File sharing between two gutsy installs (desktop and laptop) and one Vista laptop
3) file synchronization at least between the two gutsy installations, if not also on the Vista one.

I've heard of a program called iFolder, but i"m not so sure this is exactly what I need for synchronization (can I change files on either machine, which will automatically synch with the other?).

If anyone knows some great resources on setting up this home network I'd be extremely grateful - the community docs had me a little confused, they mentioned all these programs, but I had no idea what they did!

---

### Post by oskarloko on 2008-01-03
SAMBA can help you a lot.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Go step-by-step, first install SAMBA: with it you can share printers and folders.

For synchronization question, I don't know...
I think desktop would be the master, so try by ftp for example...

---

### Post by ikus060 on 2008-01-06
I'm not sure tu understand well how many computer you have. (2 laptops, 1 desktop ??)

Any way, if your desktop are Ubuntu, I suggest to share you files with samba it' simple and work very well with windows.

If you printer are on Ubuntu, I suggest to share it via CUPS. So it can be access via TCP/IP protocol.

Syncing is a bigger problem. iFolder can be a good solution for you but it's complicated and you need some advance knowledge to setup this. The better way to do this for your Ubuntu laptop is using unison but the GUI are ugly and I refuse to use it my self for this reason. To sync you Windows, I'm sure you can find a really good tool to sync you file via the samba share (better than that it's possible to use the same application under Ubuntu using wine)

---

### Post by zachthejones on 2008-01-07
I think I read about CUPS on some thread or documentation, but I'm not sure where to get it or how to access it.

I did set up samba shares on my desktop, but it won't let me add/delete files on my desktop from my laptop (both ubuntu gutsy). I'm not sure if I screwed up some share option, but I thought I had it setup so there were read/write permissions for the shared folders.

Really, what I'd like to get to is using my desktop mainly for backup and media stuff (I do like to edit videos and stuff, and my laptop doesn't have a huge hard drive on it).  Maybe there's a backup program I can use to backup my laptop to...that might be a better solution.

I had considered ifolder, but it seems to be a little complicated...

Any suggestions on a backup program which will work with a wireless network (I use wireless on my laptop)?

---

