---
title: "how to delete my linux partition"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by patchido on 2007-11-25
well the strot goes like this.... my dad finds out i am running linux... he doesnt like having 2 operating systems (windows xp) so i have to take it away...

but dont worry i am getting an external drive so i can do linux :D so.. i dont havee a windows xp cd so how can i delete everything related with ubuntu??

---

### Post by jken146 on 2007-11-25
You can use a Ubuntu live cd (and the Partition Manager app gparted therein) to format/delete partitions.

---

### Post by patchido on 2007-11-25
but that wont make windows stop working??? someone told me that i am not sure

---

### Post by fineas on 2007-11-25
Check this: [http://www.computing.net/linux/wwwboard/forum/28579.html](http://www.computing.net/linux/wwwboard/forum/28579.html)
espesially response number 4.This is what I had in mind when I installed linux at first time, in case I did not like linux.Hope it helps

---

### Post by Vadi on 2007-11-25
Skin your Ubuntu to look like windows XP!

Otherwise, the link above looks good.

---

### Post by The Cog on 2007-11-25
Simply deleting the Ubuntu partition will leave the PC unable to boot, because the GRUB bootloader that Ubuntu installs reliex on some files that live on the Ubuntu partition. 

So you must replace the bootloader first. You used to be able to do this from DOS with the command:
fdisk /mbr
but I don't know if the windows command prompt still allows this command. I don't think it would hurt to try it. If it works, you won't get the GRUB choice of OSs nect time you reboot. Once it boots straight to windows, you can use any partition editing tool you like to simply delete the Ubuntu partitions.

---

### Post by overdrank on 2007-11-25
> **patchido said:**
> but that wont make windows stop working??? someone told me that i am not sure

You may want to have a look at this 
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Good luck!

---

### Post by Bigbird999 on 2007-11-25
Or just tell you Dad that it can't be removed!!!:)  And then boot to Linux and next time his Win installation is borked.  

BB

---

