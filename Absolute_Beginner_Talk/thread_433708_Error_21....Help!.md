---
title: "Error 21....Help!"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by TheWuse on 2007-05-05
I am a complete beginner to Ubuntu and had received Feisty Fawn Live CD from a friend to play around with. Well i wanted to install Ubuntu onto a compact flash SanDisk 8gb. So i went into the install and clicked the first bubble "full hard drive" (i think thats the first bubble of the install) anyways after clicking a second bubble i chose my SanDisk and installed it without any errors. Then it asked for me to restart and so i removed my live CD and the compact flash and restarted the computer to try and enter windows xp. It didn't work?! All i got was an error saying GRUB Loading... GRUB loading. please wait... Error 21 and now i have no idea how to fix this problem and am scared that i just ruined my laptop please help!

---

### Post by drowner on 2007-05-05
You havent ruined your laptop.

Maybe GRUB is looking for the USB disk?

edit: yes it is, the list of OS's  is written in the /boot/grub directory. Which is on your sandisk, at the moment.

I cant help more than that, i dont know enough....

---

### Post by confused57 on 2007-05-05
> **TheWuse said:**
> I am a complete beginner to Ubuntu and had received Feisty Fawn Live CD from a friend to play around with. Well i wanted to install Ubuntu onto a compact flash SanDisk 8gb. So i went into the install and clicked the first bubble "full hard drive" (i think thats the first bubble of the install) anyways after clicking a second bubble i chose my SanDisk and installed it without any errors. Then it asked for me to restart and so i removed my live CD and the compact flash and restarted the computer to try and enter windows xp. It didn't work?! All i got was an error saying GRUB Loading... GRUB loading. please wait... Error 21 and now i have no idea how to fix this problem and am scared that i just ruined my laptop please help!

Grub was installed to your internal hard drive mbr, you'll need to restore your Window's IPL code to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
see the link...you can use a Window's install cd(not a recovery cd) or use a Win98SE oem boot floppy.

the Super Grub Disk can also do this:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

