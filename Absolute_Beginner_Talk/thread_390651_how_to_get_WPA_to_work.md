---
title: "how to get WPA to work"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by metalucard on 2007-03-22
hi, I am trying to convert to ubuntu from windows xp. so I installed ubuntu 6.10, all my hardware seem to be recognized and working fine. also I have a D-link 520+ pci wireless card, which should be supported by ubuntu out of the box.
Now here is the deal:

we have a WPA encrypted wirless network at home. now I understand I should have network manger that deals with this stuff (kind like the one windows has), which is all good, except I can't get it to work, and I have been trying for a week.

-so, if I go to Add/remove, and try to check netowrk manager, it says it can't cos my system is i386

-if I go to the terminal and do
sudo apt-get install network-manger-gnome
I get E: coulnd't find package (or something like that)
(yes, after editing etc/network/sources.list for all repisotories, and calling sudo apt-get update)

-I also tried to download a tar application, which I extracted, and then tried to ./configure, which result in an error saying: couln't build the binaries or somehing like that.

well, I am really desperate, and I admit that I was spoiled by windows, but I really need to get my internet working before I can get rid of windows.

ps: my computer is a dell, and is not connected to anything (no lan, ethernet...)
ps: vista SUCKS \\:D/

---

### Post by Bias on 2007-03-22
Had a similar issue, found I could only use WEP within ubuntu, far from the ideal solution but have gone to it as a temporary measure so I could get other things working, mail, web etc. Figured I would go back to it at a later date to improve the security.

---

### Post by Falados on 2007-03-22
Your going to have to look into a little program called 'wpasupplicant'
Try searching the forums for it and you'll be knee-deep in threads.

---

### Post by gameman12 on 2007-03-22
i started with this problem, i suggest taking a day and p.o. ing the ppl in ur house. connect ur laptop directly to your highspeed modem and download all the updates for ubuntu. then try and apt-get network manager again. that's what i did, but i had to use ndiswrapper as well.

btw. wpa supplicant is installed by default in ubuntu 6.10 edgy

---

