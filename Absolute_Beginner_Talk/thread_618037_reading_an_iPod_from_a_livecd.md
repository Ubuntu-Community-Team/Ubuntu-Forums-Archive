---
title: "reading an iPod from a livecd"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by aanderse on 2007-11-20
alright, here's the situation:
- friends ipod does NOT have usb, it's firewire (last version of ipod BEFORE usb ipods came out)
- friends ipod has ALL their pictures (including wedding), music, resume, etc... on it -> with NO backup (it is the backup, and the source is gone -_-)
- friends computer (intel based mac osx) decided that it wants to upgrade the ipod to a new bios which will WIPE THE ENTIRE CONTENTS of the ipods hard drive
- friend can't hook ipod up to an untrusted box (windows or mac) or else it's probably gonna try and wipe the ipod

the problem is:
- i don't have firewire port installed on my box
- i'd have to fish out that hardware from the closet, take apart my box, install it, load the drivers, etc ...

so i need a pc WITH firewire hardware installed and a livecd which can interact with firewire + read ipods

so i'm going to use my (windows) company laptop (which i believe has firewire but i'll check when i get into work tomorrow...) to boot up a livecd, hope it can read ipods (if not, hope that i can apt-get install laptop reading software while still on the livecd...) and then read the ipod and transfer all the data to a usb mass storage device


any advice? opinions? something i might be missing? all appreciated
thanks

---

### Post by jackflap on 2007-11-20
this should be perfectly doable. You can apt-get install anything u want using the live cd. 

If it asks for a reboot (i.e. like installing nvidia drivers), use ctrl+alt+backspace to restart X, and the installed packages will remain as long as u havent restarted the system.

Let us know how it goes.
Alex

---

### Post by aanderse on 2007-11-22
just wanted to post a success story:

so i used the ubuntu gutsy livecd to boot up the friends computer and right out of the box it read the ipod as a file system! it was so easy to rescue all of my friends data, she was so impressed that i could rescue all her data so easily. i explained to her free software and the difference between mac osx/windows versus gnu/linux. i left the ubuntu livecd with her so she can check it out some more :)

---

