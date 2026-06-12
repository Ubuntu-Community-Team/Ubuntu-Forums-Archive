---
title: "Editing Menu.lst?"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by hotrod1 on 2006-01-26
Well I have to edit Grub's menu.lst file but I can't boot into Ubuntu so how else can I access the file in order to edit it if I can't boot into Ubuntu? Thanks

---

### Post by aysiu on 2006-01-26
Do you have a live CD?
Live Ubuntu?
Knoppix?

---

### Post by Adrian on 2006-01-26
[QUOTE=hotrod1]Well I have to edit Grub's menu.lst file but I can't boot into Ubuntu so how else can I access the file in order to edit it if I can't boot into Ubuntu? Thanks[/QUOTE]

If you can boot into the GRUB menu, you can edit a menu item by pressing 'e'.
These are not permanent changes, so you have to edit /boot/grub/menu.lst afterwards.

---

### Post by hotrod1 on 2006-01-27
I have a live copy of Ubuntu.

---

### Post by steve.horsley on 2006-01-28
[QUOTE=hotrod1]I have a live copy of Ubuntu.[/QUOTE]

Good. Boot the live CD, mount the installed Ubuntu partition and then edit the file.

Mount the installed Ubunti partition:
First, create a directory to mount it on:
    **sudo mkdir /media/something**
then mount the installed Ubuntu partition. You need to know what partition it is - i'll assume it's hda1
    **sudo mount -t ext3 /dev/hda1 /media/something**
Then edit the file
    **sudo gedit /mnt/something/boot/grub/menu.lst**

---

### Post by hotrod1 on 2006-01-28
Well gedit can't seem to find the file since everytime I try to open it, gedit creates a file with the same name for me but I have grub installed on a seperate partition from Ubuntu, hda4.  Thanks

---

### Post by gatorbrit on 2006-01-28
If you have a dual boot windows machine you can boot into windows and then use this [http://www.fs-driver.org/index.html]("http://www.fs-driver.org/index.html")
to view your EXT2 linux partitiont, you could then edit in notepad.

---

### Post by hotrod1 on 2006-01-28
Thanks alot, now I am able to edit the file.

---

### Post by hotrod1 on 2006-01-28
Well I tried to edit the file but grub still doesn't launch and I can't boot to Ubuntu. Anyone know how to fix this, I really want to start using Ubuntu badly and I can't wait to get this fixed.

---

### Post by Adrian on 2006-01-28
[QUOTE=hotrod1]Well I tried to edit the file but grub still doesn't launch and I can't boot to Ubuntu. Anyone know how to fix this, I really want to start using Ubuntu badly and I can't wait to get this fixed.[/QUOTE]

You can reinstall GRUB from the Ubuntu installation CD. Here is a HOWTO:
[http://www.ubuntuforums.org/showthread.php?t=76652](http://www.ubuntuforums.org/showthread.php?t=76652)

---

### Post by Soccarrfreak on 2006-01-28
I had a similar if not the same problem.  I installed ubuntu, restarted, and windows booted up.  then i tried installing grub to windows drive and that sort of worked as grub then booted, but it would give errors when i tried to boot somewhere.  after reinstalling i just went to bios and there was an option "hd boot priority" or something like that and i just put the ubuntu drive to boot first (new ubuntu install with grub on same drive-which didnt boot in the beginning and just went to windows).  Now grub boots up because its booting from my ubuntu drive instead of booting as normal to windows.  Now i can select ubuntu (which is default) or go down the list to windows, and everything works fine.  

Now a question - how do you change the boot priority for grub.  i want windows to be default, and for it to auto boot to the default after only 2 seconds or so instead of 8 or whatever.  How..?

---

### Post by gatorbrit on 2006-01-28
You can just cut and paste the order of the menu items in the grub menu.lst file and put the windows boot at the top.  I do this on my home pc so as not to freak out my dear spouse.   At work, I just boot straight to linux.

Alternatively go to this section of menu.lst

[B]# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		1
[/B]

Count down the number of Operating system entries and change the 1 to whatever the windows entry is.

There is also a line in menu.lst that alters the number of seconds before it goes to the default.  I don't remember what it is but it is pretty intuitive.  Just change that that "8" to "2"

Actually the relevant code is...
[B]
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		8[/B]

---

