---
title: "[SOLVED] HELP!! Ubuntu + Black screen = hell"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by madsmeg on 2007-08-14
ok, so i have just formated my whole hard drive, i boot up ubuntu, it goes through all the motions, finnishes up the loading bar, then goes to a black screen, but i hear sound, so i presume i card isnt supported (Nvidia 7300GT), but here it gets worse, my motherboard has nowhere to put amonitor into, so what do i do? i know the disk isnt fualty, and i read someone else here mention somthing about video drivers, ive tried booting in all resolutions (all show load bar Etc fine) and nothing changes (except the resolution ofc).

Please help!!
:confused::confused::confused:

P.S. i have access to my GF's computer which is what i am posting with. Will be on here (forum) until fixed or die of sleep deprivation.

---

### Post by madsmeg on 2007-08-14
ok got it up, had to remove my second card, and ust the alternate monitor output

so... just ignore post, i will see what i can do on my own from hre

---

### Post by yellowband on 2007-08-14
hello madsmeg

what kind of monitor are you using?

i had this problem when trying to use my dell 24 inch with edgy.  it may not be your graphics card but a configuration thing.  kindof hard to change things when you cant see the screen though :).  perhaps you have another monitor lying around you could try?  or maybe put in your install ed and try load in safe graphics mode, or better yet, from the command line

if you can get there, scope out your /etc/X11/xorg.conf file to make changes to your monitor settings.  look around the forum for more help with that file.

---

### Post by madsmeg on 2007-08-14
thank you for thae fast response, but i am now installing (great having 2 PC's side by side:) ) as i mentioned above i needed to remove a card (had 2 in SLi) and use the second monitor adapter, wierd but it works and i can mess round with it from there :)

again thanks for your time, it is really appreciated(?)

---

