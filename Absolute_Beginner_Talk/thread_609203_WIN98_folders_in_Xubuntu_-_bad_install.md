---
title: "WIN98 folders in Xubuntu - bad install?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by ringsofsaturn on 2007-11-10
Hello,
Having recently (2 days ago) installed Xubuntu 7.10 Gutsy Gibbon on my old P3 450mz PC I've discovered that by clicking on AAA icon I can view folders/files from my previous WIN98 installation. Have I messed up install? I'm NOT a "tech head" and having little understanding of PC's but found the install very simple, a lot more so than installing WIN 98SE. Configuring wireless network was simple but my printer won't work. 
I would be grateful for any feedback.

---

### Post by Tux.Ice on 2007-11-10
no idea about win98 thing (possibly linux is too good for microsoft lol) umm printers hardly ever work in linux:popcorn:

---

### Post by geirha on 2007-11-10
When you install dual boot, as you probably have done, ubuntu will look for other operating systems, and mount the partitions, giving you access to read and write to them. In Gnome they show up on the desktop as icons (probably does in xubuntu too, haven't tried it yet), usually named after the label of the filesystem, so your windows drive is possibly labeled "AAA"?

Anyway, it sounds like you haven't done anything wrong :)

As for your printer, search for it here: [http://www.openprinting.org/printer_list.cgi](http://www.openprinting.org/printer_list.cgi) . It should give you a clue of how well your printer works in linux, and possibly what tweaks you need to do to get it working.

---

### Post by ringsofsaturn on 2007-11-10
Hello Geira,
Thanks for the reply (and you too Tux.Ice). When I installed Xubuntu it asked me to create a partition (which I did) but I had previosly removed WIN98 so don't understand why folders are still showing. Still it's not a problem if you think it won't affect Xubuntu. Have been to the site you recommended re printers (mine's a HP 710C Deskjet) prior to your answer but havn't managed to install it yet,  despite all the advice on that particular site.  To be quite frank, so much of it was almost a different language, (to me at least). I don't know how they expect a normal "simple" PC user to understand it without going on a Unix programming course! Sorry to sound off, just frustrated. After all Xubuntu didn't exactly break the bank did it?  I really appreciate all the people out there that put time and effort into  Linux. Having Googled  "Xubuntu  Gutsy Gibbon - printers" it seems others more tech competent than me (that must be MOST of the populas of this planet!) are having problems with their printers in Gutsy Gibbon 7.10. Should I install a previous version of Xubuntu that didn't have a printer problem or what? I don't want to go back to WIN98, not that I have a problem with it, just that it sems a backwards step and I like the Linux philosophy. I am stubborn (pig headed?) about this, just don't want to be defeated!!. I NEED the printer to work .
Many thanks for your time.

---

### Post by oilchangeguy on 2007-11-10
how did you remove 98? you don't say. and as operating systems go. 98 is still a very good os, it one was of microsofts better operating systems. i still use it on an older toshiba lappy. for biz, no internet. ( it could if i wanted to, but what's the point of putting a pent 1, 40mb ram, 1.3gb hd computer on the internet)

---

### Post by geirha on 2007-11-10
Ideally, you should Add Printer, and specify the model as HP Deskjet 710C (as you probably have done), and it should work. But of course, it doesn't, so it's a bug in ubuntu, and it has been reported here [https://bugs.launchpad.net/ubuntu/+source/cdebconf/+bug/52814](https://bugs.launchpad.net/ubuntu/+source/cdebconf/+bug/52814)

Chances are a fix will be made sooner or later, and your problem will be solved that way. Seems some people have gotten it working and posted their fix there, so you could either try what they did, or wait for the fix to come through the update-manager.

Edit: And that bug was fixed last year, so that can't be the one. Perhaps you should file a new bug report.

---

### Post by ringsofsaturn on 2007-11-11
I appreciate  your replies oilchangeguy and geira. I uninstalled WIn98 in "add remove programs". If I remember correctly I got a message somewhere asking if I wanted to go back to a previous version of windows. I certainly didn't install dual boot (at least not deliberately) and the PC won't boot into another OS anyway despite when booting up it asks me if I want to do so (apart from Xubuntu and Xubuntu safe mode it asks me if I want to boot into WIN95, 98, ME. Only 98 has ever been installed on that machine). On that subject (as I need the printer to work as mentioned previously) is re - installing WIN98 so I CAN dual boot a simple task or not? Bear in mind I'm not PC savy as all of you out there! And yes geira I did go thro' the install printer process as you described.
Thanks once again.

---

