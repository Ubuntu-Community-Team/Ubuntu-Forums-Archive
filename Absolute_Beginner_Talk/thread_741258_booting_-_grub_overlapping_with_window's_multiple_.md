---
title: "booting - grub overlapping with window's multiple OS thingy"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by antemon on 2008-03-31
hello all

new here and to linux overall and I don't know if what I'm experiencing is normal, even thought of a workaround for it but wanted to ask if it were safe to do it.

anywho...
winxp
seagate hdd - master1
maxtor hdd - master2
ubuntu 7.10 gutsy

popped in the CD while in windows, closed the autorun thing. I initially wanted to install ubuntu within windows so that I could evaluate it beforehand. I read somewhere that Wubi would be best and when I found a yellow ubuntu logo in the CD, I ran it. 
installation proceeds, nothing notable. selected my maxtor HDD and used all of it. (to my surprise, formatted the old fat32 drive, bleh good thing I happened to back up all those family pictures...but anyways)

reboot

since I set up my PC to boot on cd-rom first, the livecd selection popped up, selected boot from hard disk and had two choices: winxp and ubuntu-somethingsomehting... selected the second one.
install continues and gets done.

but now, everytime I boot up I get two sets of OS choices
one is the GRUB, I presume, with the normal run, safe graphics, memtest and boot from HDD. But when selecting boot from HDD, I still have two OS choices, the two that appeared when I installed.

and, when I get to windows, the ubuntu uninstall from wubi runs when windows loads. Minor inconvenience and since I was trying out ubuntu I didn't pay much attention to it.


1. now, I know I can edit out ubuntu's selection on the second windows-based OS selection via system properties and save 15seconds when loading. Is this safe?
2. This goes for the ubuntu uninstall running when windows loads, just take it out from the startup folder in Start. Is doing that safe as well?


more backstory:
figured I try out the lighter ubuntus as well, so I uninstalled via the window that pops up on start.
But, GRUB is still there with the OS choices for ubuntu (I havent started to install xubuntu yet)
selecting ubuntu would yield an error of course, and after GRUB I still have windows XP and ubuntu thingamajig on the windows OS selection. On to more Qs...

3. WTH!?

installed once more, through liveCD and all those things before uninstall still happens:
2 OS selection with ubuntu on windows' still, uninstall window/program when I start windows.
going through the work arounds I stated earlier, everything should be doable... but

4. can I have GRUB select 'boot from hardisk' as default since I'm the only one using ubuntu in the household (well, GF is interested now. interestingly enough, due to the games <_<) and how do I do it?

thanks in advance to anyone who answers :)

---

### Post by NR1224 on 2008-03-31
it sounds like u tried to use wubi to install 7.10, did u use the 7.10 cd? because, if so, it didn't work properly, because the wubi that came with 7.10 was for some reason i cant remember not working. You have to download the beta for 7.10

---

### Post by antemon on 2008-03-31
downloaded ubuntu 7.10, from which server I don't remember though...

---

### Post by antemon on 2008-04-01
*bump*

---

### Post by antemon on 2008-04-04
*bump*

---

