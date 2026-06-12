---
title: "Installing Ubuntu Linux without damaging or risking my precious Windows?"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by Solidad on 2006-05-22
I was wonering if anyone of the linux users here can help me. 

determine the damage or changes it will cause my win2Ksp4. and my 40GB HD with a 10:30 partition.

i tried it with my old HD but it failed installing Kubuntu. because of the Bad sectors preventing the installation of the boot files needed. and now i cant use a Fdisk command (Win98se) to restore it back. i was also wondering if any one can help me.

im thinking of installing the Ubuntu in my current HD running win. but i dont want to damage windows and its partitions. since ubuntu needs a seperate partition witha new File system. and a swap file. meaning i will need to scarifice a space in D with a 30GB. w/c mean sacrificing all of my files. 

and i have no idea if windows willbe able to see this linux partition. or linux can see the win parition. on FAT32, i tried the live CD and i can't browse my FAT32 system on it. or i don't know.  how to.

can anyone enlighten me. will i be risking too much? or a little?

---

### Post by nanotube on 2006-05-22
well, before doing anything of this sort, the first thing to do is to back up all your data! 
ubuntu can see and use fat32, but can only read ntfs. also, you need to manually mount those partitions, it does not mount them automatically from the livecd (but knoppix livecd does mount them automatically, so if you are interested in using a livecd, try knoppix).
since you appear to be concerned about your windown install, as well as the data, and do not appear to know much about dual booting, i would advise you to read up about this topic online before attempting to do anything on your computer. one good place to start would be this webpage: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
good luck, and be careful. :)

---

### Post by aysiu on 2006-05-22
Back up your important data.

Then, read these three links:

[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by Solidad on 2006-05-22
wow thanks that a fast. one.

what if i want to undo the damage since linux has a different file system how can i bring it back to windows FAT32?

thats what happend in my old HD and since Ubuntu failed there. i cant use Fdisk on win98se to put it to FAT32

---

### Post by louis_nichols on 2006-05-22
it is possible to read both linux partitions from win and win  partitikn s from linux. some restrictions apply, but it's generally possible (reading works perfectly both ways; writing is not supported from Linux on ntfs, but works on fat32)

now, Ubuntu only occupies the space you tell it to. obviously, it will have to be unused space. generally, you only need about 5 gigs to get an ubuntu up and running, and also have some 3 gigs storage space within.

there is an option on the install cd to just place ubuntu on empty space on your hdd, so the easiest way to install it would be to shrink one of your prtitions with as much space as you want to give to ubuntu, and then choose that option. of course, if you don't have that much space available, you either don't install ubuntu, or just delete some of that data to make some room for it.

hope this helps.

---

### Post by aysiu on 2006-05-22
You can format partitions as FAT32 from within Windows.

Go to Start Menu > Control Panel > Administrative Tools > Computer Management > Disk Management and right-click on the partition you want to format.

---

### Post by Solidad on 2006-05-22
if i let ubuntu choose the space it needs. will it touch my other data. lets say my C: has 5GB and my D has 15GB left. if it chooses the 5GB on the C: will it destroy C:

i tried installing Ubuntu. i set up my partions and it is recomended that i put a swap partition for the Ubuntu. is it necessary?

i also got conufsed. will ubuntu install itself if i have a ext3 or something. will it install on a Fat32 partition?

the partitioning part is the choke point in my installation can anyone enlighten me.

i forgot. how can i mount my HD on the Live CD? of ubuntu?

and thanks for the article i'll read them tommorow. since its way past midnight in my country.

---

### Post by nanotube on 2006-05-22
ubuntu cannot install on fat32, you have to use a linux partition type, such as ext3. 
also, it will not install on some free space of an existing partition - you have to give it its own partition.
please read the links that were posted (aysiu's list is good), and figure out what is required first, before going on to install!

---

### Post by Solidad on 2006-05-22
So i have to destroy D then. risky. 

so how can i mount my HD so that i can see them on Ubuntu Live?

---

### Post by nanotube on 2006-05-22
you do not have to "destroy" d. what you would want to do is to defragment the d drive, and then use a partition editor to chop off some free space into a separate partition, and then you can install ubuntu on that. 

about mounting win partitions from ubuntu live, this tutorial will show you how: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by aysiu on 2006-05-22
[QUOTE=Solidad]
so how can i mount my HD so that i can see them on Ubuntu Live?[/QUOTE] Paste this command into the terminal ```
sudo fdisk -l
``` It'll tell you the location of your FAT32 partition. Let's assume for this example that it's /dev/hda2. To mount it, you'd paste in this command: ```
sudo mkdir /recovery_d
sudo mount -t vfat /dev/hda2 /recovery_d -o umask=000
``` If it's an NTFS partition at /dev/hda1 ```
sudo mkdir /recovery_c
sudo mount -t ntfs /dev/hda1 /recovery_c -o umask=0222
```

---

### Post by Solidad on 2006-05-23
do i always have to do this evreytime i use the live CD? can i save the settings?

---

### Post by aysiu on 2006-05-23
[QUOTE=Solidad]do i always have to do this evreytime i use the live CD? can i save the settings?[/QUOTE] If you find yourself using a live CD often and mounting Windows within that, get [Knoppix](http://www.knopper.net/knoppix/index-en.html)--it's designed to be a live CD and requires no terminal commands to mount partitions.

---

### Post by Solidad on 2006-05-23
ive done the mount thing. i also discover that there is a easier way on doing this. 

in the Administrative>Disk

i'll just make a path folder and enable the drive. viola. 

but there is something that i can't explain. i tried opening a PDF file form my drive D and. then the OS freezes. if it is windows i wouldn't be suprised. but linux dont do this normaly, is there anything to it?

Also. since i was able to mount my drive. how can i make a shorcut? i still go to Disk to open it.

---

### Post by aysiu on 2006-05-23
I don't know anything about the freezing with the PDF, but for a shortcut, you can just middle-click-drag the folder in Gnome (or left-click-drag in KDE) to the desktop and select "link here."

---

### Post by Solidad on 2006-05-23
i dont even know where the folder is. i just put in my path. /<folder> thats it. i just dont know where is is.

---

### Post by nalmeth on 2006-05-23
A shortcut for the drive in windows? I don't know how to do that.
With gnome, the mounted drive should appear on your desktop if it is mounted correctly.

---

### Post by aysiu on 2006-05-23
[QUOTE=Solidad]i dont even know where the folder is. i just put in my path. /<folder> thats it. i just dont know where is is.[/QUOTE] Open up the file browser and press Control-L.

This will focus on the location bar.

In the location bar, type

/

Then press Enter. You should see your folder in there.

---

### Post by Solidad on 2006-05-23
its a live CD anyway. so it wont probably detect right away. anyway

---

### Post by aysiu on 2006-05-23
[QUOTE=Solidad]its a live CD anyway. so it wont probably detect right away. anyway[/QUOTE] Use a Knoppix live CD. I think you'll be blown away by it.

Ubuntu's not really intended to be stand-alone live CD so much as a preview of the Ubuntu installation.

---

### Post by Solidad on 2006-05-23
but it is sure if it its installed on the HD.  ubuntu will blow me up. i hope

---

