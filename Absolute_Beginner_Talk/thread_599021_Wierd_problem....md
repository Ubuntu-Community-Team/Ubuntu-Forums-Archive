---
title: "Wierd problem..."
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by terjeloe on 2007-10-31
Ok.. Ive tried to install for 4 days now.. First I had the problem with the desktop.i386.iso that It stoped at 94%, the install window just closed down with no error msg.. and the installation didnt make a grub folder inn /boot.. and it could obiously not load grub at boot.. just a blank screen.. 

I downloaded the alternative.i386.iso and it halts at the "select and install" step.. just before it halts it asks me about screen resolution so I guess its something about installing x/gnome? but this time Im able to install the grub loader.. 

 but when I boot it only start into text mode.. then I try to do "sudo apt-get install gdm", it starts installation, but promt me to insert the gutsy install cd and hit enter.. I do that but nothing happens.. it tries to read it, but it obiously cant find it.. the cdrom is mounted to /cdrom aswell..

Anyone have an idea of how I can make the installation pase the select and install screen or how I can make the gdm installation work?

---

### Post by overdrank on 2007-10-31
> **terjeloe said:**
> Ok.. Ive tried to install for 4 days now.. First I had the problem with the desktop.i386.iso that It stoped at 94%, the install window just closed down with no error msg.. and the installation didnt make a grub folder inn /boot.. and it could obiously not load grub at boot.. just a blank screen.. 

I downloaded the alternative.i386.iso and it halts at the "select and install" step.. just before it halts it asks me about screen resolution so I guess its something about installing x/gnome? but this time Im able to install the grub loader.. 

 but when I boot it only start into text mode.. then I try to do "sudo apt-get install gdm", it starts installation, but promt me to insert the gutsy install cd and hit enter.. I do that but nothing happens.. it tries to read it, but it obiously cant find it.. the cdrom is mounted to /cdrom aswell..

Anyone have an idea of how I can make the installation pase the select and install screen or how I can make the gdm installation work?

Hi and I have to ask, have you checked the cd for errors and Then you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by terjeloe on 2007-11-01
Ive checked the cd for errors.. but havent done the checksum thing.. I will try this when I get home!

---

### Post by terjeloe on 2007-11-01
ok.. check sum was ok.. the cd is ok.. same problem.. Ive been trying for 5 days now.. could there be something about my hardware? I got a fujitsu siemens c1320 laptop.. pleas.. can someone help me or do I need to install windows again? :( :(

---

### Post by hoges on 2007-11-01
Are you installing with an internet connection? I had problems when I was installing with the alternative cd with lan. I pulled out the cable and it worked.

Not much help, I know, but it's a start.

---

### Post by terjeloe on 2007-11-01
Ive tried both with and without.. no luck :/

---

### Post by overdrank on 2007-11-01
> **terjeloe said:**
> Ive tried both with and without.. no luck :/

Ok the live cd works correct? The install is what fails and you have checked the cd, then you could have errors on the hard drive. So if you are partitioning to use the full drive then you may try a smaller partition. Also if you are using 7.10 you may choose to drop back and try 7.04 feisty. Good luck!

---

### Post by terjeloe on 2007-11-01
hum.. yeah.. maybe its the hardrive since its messing up all the time.. hum.. when I make the partitions.. do I have to make the / partition early on the disk or could I put it at the end of it and have the /home one at the beginning? or even have some free space on the beginning? does it matter?

---

### Post by hoges on 2007-11-01
It shouldn't really matter. It is preferable to have it as a "primary" partition, though.

Are you putting anything else on the hdd - ie xp?

---

### Post by terjeloe on 2007-11-02
Tried it, but no luck.. :(  gonna try 7.04.. if that doesnt work Im giving up.. can I update to 7.10 easy if I get 7.04 installed?

---

### Post by terjeloe on 2007-11-02
That worked! Happy days!! :) Running the update manager to 7.10 now.. hopefully that works.. :)  sweet ***.. I can return to real life now.. :) been completly locked up to this **** now..

---

