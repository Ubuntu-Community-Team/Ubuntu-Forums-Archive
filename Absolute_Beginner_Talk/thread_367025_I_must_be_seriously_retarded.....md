---
title: "I must be seriously retarded...."
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by butterball on 2007-02-21
okay. so i was thinking i could just mount my spare hard drive from the Graphical Interface but something tells me I was WRONG. It seems like using the terminal should be easy... but I really don't know any of the code. Is there a site or anyone out there who has a list of the basic code? I know I could understand it, the problem is finding it.

---

### Post by kerry_s on 2007-02-21
-> [http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by teaker1s on 2007-02-21
not sure about previous ubuntu versions but desktop panel, right click and add to panel, select disc mounter-with this I see windows partition in edgy and feisty

---

### Post by annda on 2007-02-21
is the drive formatted? under windows or linux?

sudo fdisk -l

will tell you a lot.

basically you need the mount command (type man mount in the terminal) but it can be complicated for new users.

the easiest (sic!) way is to modify a system file /etc/fstab.

but copy and paste the output of fdisk first, so we help you along in your linux adventure.

---

### Post by butterball on 2007-02-21
it tells me that the command is invalid and gives me a basic command list (which i don't yet understand) i would copy and paste but it's running on a different computer at the moment

---

### Post by butterball on 2007-02-21
> **teaker1s said:**
> not sure about previous ubuntu versions but desktop panel, right click and add to panel, select disc mounter-with this I see windows partition in edgy and feisty

did that and it shows up that there are two floppy drives that could be mounted. that's really messed up cuz i only have one.

---

### Post by teaker1s on 2007-02-21
okay, seems to work on some hardware.

look here for mounting commands and howto
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows")

---

