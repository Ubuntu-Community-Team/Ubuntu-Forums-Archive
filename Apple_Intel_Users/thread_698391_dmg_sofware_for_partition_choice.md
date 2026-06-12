---
title: "dmg sofware for partition choice"
date: 2008-02-16
forum: Apple Intel Users
---

### Post by lex1 on 2008-02-16
what is the name of the sofware for mac that gives a choice of partitions or os'es on starup?


lex1:popcorn:

---

### Post by zanak on 2008-02-16
rEFIt i gess

---

### Post by cyberdork33 on 2008-02-16
you can also just hold the option key on startup

---

### Post by lex1 on 2008-02-16
thanks for that

but i am having difficulty installing ubuntu

i have three partitions

one has OS X tiger 10.4.10

the other two one is unix one is fat

i am trying to install ubuntu on one and windows on the other

bootcamp is not available for tiger.

thanks for any feed back.

lex1

---

### Post by cyberdork33 on 2008-02-16
What is the goal you have? what do you plan to use the FAT partition for? 

Basically all you need to do is 
[LIST]
[*]boot the Ubuntu LiveCD.
[*]Start the "Partition Editor" (Gparted) from the menus
[*]Select the partition you want to use for Ubuntu and delete it.
[*]Exit the Partition Editor
[*]Start the Ubuntu Installer
[*]When given the option, choose to "Install to Free Space"[/LIST]

---

### Post by lex1 on 2008-02-16
Thanks for your post

well my son from time to time needs a windows box so that fat partition would be for xp it can be 
ntfs.

lex1:popcorn:

---

### Post by cyberdork33 on 2008-02-16
> **lex1 said:**
> Thanks for your post

well my son from time to time needs a windows box so that fat partition would be for xp it can be 
ntfs.

lex1:popcorn:In that case, you would probably be better off reading one of the "triple-boot" guides in the forums. There are considerations that need to be made for windows because of the limitations of the BIOS emulation.

---

### Post by lex1 on 2008-02-17
an alternative would be to place vmware in unbuntu or mac partition but that defats the object i will look around for triple booting

lex1

ps

saw this i am runnunig 10.4.8 also you can see the next thread one gey did it on a imac i do not have bootcamp but i have the drivers that xp needs
[http://ubuntuforums.org/showthread.php?t=187465&highlight=MacBook+triple+boot+success](http://ubuntuforums.org/showthread.php?t=187465&highlight=MacBook+triple+boot+success)

---

