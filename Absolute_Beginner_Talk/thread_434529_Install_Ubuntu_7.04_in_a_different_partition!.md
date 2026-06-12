---
title: "Install Ubuntu 7.04 in a different partition!"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Arkanos on 2007-05-06
Hello all, I'm new on linux, but a friend of mine talked to me very good about Ubuntu, so yesterday I tried to install it, but I had some problems.
This is my desktop configuration:
2 SATA disks, 1 IDE.
The 2 SATA disks are partitioned so I have 5 partitions, C:(win vista os), D:, F:, G:, H:
The IDE has 1 partition of 60 Gb.

Yesterday I put on the Ubuntu 7.04 CD and run the live distro.
Clicked on Install and started the isntallation process.
It asked to choose the partition, I choose manual option, selected the IDE disk and started to resize it.
1 partition of 23 Gb for the OS and 1 of 2.3 Gb for the swap.
So I had:
/dev/hdb
   /dev/hdb1  23000 Mb   /mount/hdb1  
   /dev/hdb2  2300 Mb     /swap

If I push OK, it tells me something about root, if I choose '/' instead of '/mount/hdb1' it resizes the IDE disk, but doesn't install the OS.
In fact when I switch on the PC, it starts Windows Vista!

Some help? Thank you in advanced and sorry for my bad english!

---

### Post by alienexplorers on 2007-05-06
When you install to a hard drive you need a root partition (/)and a swap partition.  Dusing the partitioning you must define which partition is root.  If you don't the OS will not install correctly if at all.  The best way to setup your IDE would be:

Partition 1     /
Partition 2     /home
Partition 3    swap

Adding the home partition allows you to save your preferences seperate from the root partition in case you have to ever re-install (It will happen eventually).

---

### Post by Arkanos on 2007-05-06
Thank you for the answer, so I have to do 3 partitions of the IDE.
Another easy question:
the '/' is where I install the OS, the 'swap' is the swap, and the /home??
I don't want to use all the 60 Gb for Ubuntu, I prefer use about 25 Gb.
Could you tell me the best configuration for the 3 partitions using 25-30 Gb?
Thank you again!

---

### Post by alienexplorers on 2007-05-06
the /home partition stores all your preferences.  It is wise to keep it on a second partition in case you have to re-install Ubuntu.  A good breakdown of partitions would be:

> Root     /          10GB
Home     /home        13GB
Swap      swap         2GB

---

### Post by Arkanos on 2007-05-06
I've already installed Ubuntu on the IDE dirive, following a tutorial on this forum, but.....
I disconnected the SATA drives, setted the IDE as master and installed Ubuntu.
When I reconnected the SATA drives and setted the IDE drive as primary in the boot sequence, I can see only Ubuntu Linux and no Windows Vista.

I really have no idea.

P.S.: sorry for my bad english!!

---

### Post by alienexplorers on 2007-05-06
Was Windows ZVista on the SATA drive.  If so you have to edit the /boot/grub/menu.lst file to add Windows Vista to the grub boot loader.

> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

#[COLOR="Red"] 
title		Microsoft Windows Vista
root		(hd1,0)
savedefault
makeactive
chainloader	+1[/COLOR]

---

### Post by Arkanos on 2007-05-07
Thank you. I've fixed that problem yesterday evening and now Ubuntu runs vey well.
Now I have another problem:
- I've installed some packages (sun-java6, codecs, chat Programs, and so on), Ubuntu freezes and I've pushed Reset on my PC to restart the machine and when I enter in ubuntu I have a white screen without anything.
I can login but nothing appears after it!

---

### Post by antoz on 2007-05-07
Can't really help myself but I remember reading somewhre that linux doesn't like hard reboot but forgot where, maybe someone else can help.

---

### Post by steve.horsley on 2007-05-07
So you get a good-looking login screen with the username box in the middle. You enter username and password, and **then** get the white screen?

If this is correct, see if you can get a black text screen with a login prompt by pressing <Ctrl-Alt-F1>. If you can, there's a possibility to fix things. Ctrl-Alt-F7> should get you the white screen again, much good as it does you. 

If I am right and you only get the white screen after you log in, there may be some bad setting in one of the hidden files in your home directory. You can try this out by switcing to the text window with <Ctrl-Alt-F1> and creating a new user from there. These commands will do it:
[B]sudo -i
adduser newusername
adduser newusername admin[/B]
Then you can log in as newusername and see if you get a good screen there. If so, the problem is a setting in your home directory somewhere, probably in one of the hidden folders 
.gnome
.gnome2
.gnome2_private
.gconf
.gconfd
The easiest thing may to be to copy the files you need to keep to /tmp for a while and delete everything in your home directory, and then copy your data bask again.

---

### Post by steve.horsley on 2007-05-07
> **steve.horsley said:**
> So you get a good-looking login screen with the username box in the middle. You enter username and password, and **then** get the white screen?

If this is correct, see if you can get a black text screen with a login prompt by pressing <Ctrl-Alt-F1>. If you can, there's a possibility to fix things. Ctrl-Alt-F7> should get you the white screen again, much good as it does you. 

If I am right and you only get the white screen after you log in, there may be some bad setting in one of the hidden files in your home directory. You can try this out by switcing to the text window with <Ctrl-Alt-F1> and creating a new user from there. These commands will do it:
[B]sudo -i
adduser newusername
adduser newusername admin[/B]
Then you can log in as newusername and see if you get a good screen there. If so, the problem is a setting in your home directory somewhere, probably in one of the hidden folders 
.gnome
.gnome2
.gnome2_private
.gconf
.gconfd
The easiest thing may to be to copy the files you need to keep to /tmp for a while and delete everything in your home directory, and then copy your data bask again.

P.S. I think I have just discovered a bug in Feisty - I cannot delete a user that I added with the adduser command by deleting them in System->Administration->Users and Groups. I had to manually delete the relevant lines from these three files:
/etc/passwd
/etc/shadow
/etc/group
Oh well. Time for a bug report I guess.

---

### Post by Arkanos on 2007-05-07
Thank you all, I fixed all the problems.
I tried to install Beryl too, but my graphic card is old I think (Ati Radeon 9600XT), so it runs bad on it!
Now I'll search for MP3/AAC codec for audio and something to watch my divx and DVD.
I also connected my iPOD, it works but Amarok tells me that it doesn't have the MP3 support and then it freezes!
Some hints?

---

### Post by steve.horsley on 2007-05-07
How did you fix the whits screen - others may want to know?

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Players_.26_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Players_.26_Browser_Plug-ins)

---

### Post by Arkanos on 2007-05-07
sorry, I haven't written it, because it isn't a good method: reinstalling Ubuntu!
Sorry but I'm noob and that was the best method :)

---

