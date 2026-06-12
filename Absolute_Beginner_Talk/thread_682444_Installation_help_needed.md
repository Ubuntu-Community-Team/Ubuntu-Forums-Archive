---
title: "Installation help needed"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Linwe on 2008-01-30
I am trying to dual boot Ubuntu with windows Xp

I used Partition Magic to set up my partitions before trying to install Ubuntu

Everything goes fine until I get to the partitioning stage

Partitioner starts and loads the first page with the options to choose partitioning method
I chose guided first and was writing the changes to disk when Ubuntu froze  I hard booted and started the reinstall process again. Now when i reach the partitioning stage and choose the first guided option I get a red screen that tells me the resize operation is impossible
Check /var/log/syslog or see virtual console 4 for details (it then sends me back to the partitioning methods options dialog)

If i choose the manual option it shows me this information:
IDE1 master (hda) - 120.1 GB Samsung SV1204H
#2 primary 4.8 GB B K fat32  /media/hda2
#1 primary 115.3 GB   K ntfs /media/hda1
      pri/log 7.7 MB  FREE SPACE

any help would be great. 

Thanks

---

### Post by gsiliceo on 2008-01-30
I would recommend the alternate installer cd.
And make a surface test on that hard disk, error check.

---

### Post by Linwe on 2008-01-30
I downloaded ISO and made a cd

Also very new to this so will steps outlined, sorry in advance.

---

### Post by Linwe on 2008-01-30
I can't do anything but try to install Ubuntu if I try to start up windows it tries to start the Hp System recovery tool.

---

### Post by oedha on 2008-01-30
it's better for you back to partition magic ( i suggest gparted )
manage the partition again

then when you install ubuntu at step 4 of 7
choose "manual" ( since you had prepared the partition from PQmagic )

choose i partition that you prepared for linux, make it ext3 and put "/" on the mounting point

click next.....for the next step.....
~E~

---

### Post by Linwe on 2008-01-30
ok tried using my PM bootable diskettes once it loads I have no ability to move my mouse or choose any options using tab key

any ideas

thanks in advance

---

### Post by oedha on 2008-01-30
sorry...i can't help you on PM.....
i usually play with GParted in managing the partition
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

~E~

---

### Post by Linwe on 2008-01-30
Also i am unable to boot to windows XP at all. I cannot use my recovery option. Now what?

---

### Post by oedha on 2008-01-30
do you have XP installation CD ??
if you have.......
1. boot from that cd
2. choose recovery
3. wait until prompt......enter 1 for c:\WINDOWS
4. fill the administrator password
5. you will be in command prompt.....
6. type fixboot  [hit enter and follow the direction]
7. type fixmbr [hit enter and follow the direction]
8. type exit   

now you \r xp will restart....remove the cd

~E~

---

### Post by Linwe on 2008-01-30
I don't have any cd's

With Partition magic I had to make a diskette for BootMagic  I can get to the area where I can choose to load windows but when I do it tells me :

Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll
Please re-install a copy of the above file


Ok I am able to get to the command line and when i do fixboot it tells me it has rewritten the boot sector  but when it reboots I get the same message

---

### Post by drowner on 2008-01-30
I don't know windows, but it sounds like during partitioning you have corrupted/deleted your windows partition?

---

### Post by oedha on 2008-01-30
walah.......it's better for you to get one.....
or you can install ubuntu but you have to sacrifice your windows.....

mmm.......wait
can you try to install ubuntu again and at step 4 of 7....choose manual
give me the screen shot or all information from that window....

i am just afraid.......later on until you give me what's on the 4 of 7 step screen
~E~

---

