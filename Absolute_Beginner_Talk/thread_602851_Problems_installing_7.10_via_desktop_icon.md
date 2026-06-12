---
title: "Problems installing 7.10 via desktop icon"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by goslings on 2007-11-04
Hi 
is it me or is the latest version of the step by step install (Ubunto 7.1) totally different to that on the web docs
for eg [http://www.psychocats.net/ubuntu/installing#partitioning]("http://www.psychocats.net/ubuntu/installing#partitioning")
shows 1st option where by you pick the partition % 
(I assume) you have an installation of Ubunto and your xp remains *totally* intact, 
But I do not get that step, does anyone else ? 
all I get at step 4 is ..... guided (wipe it all) or  manual see image below
 really really confused and rather frustrated as it all looks so good and works !
Ian

---

### Post by goslings on 2007-11-04
ah well I'll have to wait another week to get back to this
shame

---

### Post by goslings on 2007-11-05
apparently it is step 4 that asks the % question
as you can see from the image i uploaded earlier it does NO ask me that
really frustrated with this install

---

### Post by ratatosk13 on 2007-11-05
Ack! Honestly, whenever humanly possible,I only set up a dual boot with Windows and Linux if I can use separate drives for each. 

I'm a newb, but it looks like you used the entire drive for your Windows partition--you can set the partition size for WinXP in the WinXP setup. Since you have no free space (unpartitioned space), that may be why the Guided - resize option isn't showing up. I don't know if the Windows install is new or old; but, if you can backup your stuff in Windows, I would recommend starting from square one: go into the WinXP setup, delete all partitions, setup a new Windows partition and specify how much of your drive to use for it and then try the Linux install again. At that point, you can use the guided option and have it use the remainder of the drive for the Linux partitions.

If you really don't want to redo everything, you need to resize your Windows partition--you'll have to since the entire drive is formatted using NTFS already. To do this, you can try using the [Knoppix]("http://knoppix.net/") Live CD . Please be aware that some people encounter problems with resizing their Windows partition, so be careful--and don't forget to defragment the drive first.

Good luck!

---

### Post by qamelian on 2007-11-05
> **goslings said:**
> apparently it is step 4 that asks the % question
as you can see from the image i uploaded earlier it does NO ask me that
really frustrated with this install

Unless I'm missing something from your description of the problem, once you select manual, you need to click the forward button. The installer will then present you with the partitioning tool.

---

### Post by jaybombalous on 2007-11-05
Its asking u want u wanna do???

If u use the guided setup, I think it will automatically set up the partitions for and preserving any other partition that has a primary OS installed. But DO NOT quote me on that... What I am trying to say is this... I believe if u use option one u will be fine and windows will be saved, but I am not sure since I don't use windows and don't know what its like dual booting with windows. :(

U have to think a little for yourself, right now if u have windows, then the windows partition is gonna be 1. So if u only have one partition then whatever you do don't let the program format or delete partition 1 since this your windows partition.

Knowing that, u will need 3 partitions to install ubuntu. 

Primary partition for the ubuntu OS
Extended partition
Swap partition

^^^ at some point u will see a reference to this, either they will call your drives like

hda, hdb, hdc or sda, sdb, sdc, etc... The partitions will be named as such sda1, sda2,sda3, etc... same with the hda1, hda2, etc...

WHATEVER U DO, DO NOT DELETE OR FORMAT THE WINDOWS PARTITION. it will be clearly labeled. :)

---

### Post by goslings on 2007-11-05
thanks for everyones help
It has been suggested that I use winxp to make a partition, then the installation process will recogise the free space and ring up this "missing" slider.

---

### Post by LowSky on 2007-11-05
you dont need the "slider", just make a partition he size you want and install ubuntu there

---

### Post by goslings on 2007-11-08
> **LowSky said:**
> you dont need the "slider", just make a partition he size you want and install ubuntu there
At what step is the option to make a partition size ? 
because I don't seem to see one in steps 1-7
regards

---

### Post by goslings on 2007-11-11
think I might have overcome this problem 
GParted signed errors on the extended area of the disk 
so i've formatted it and re run GParted and am currently resizing that area
i wait with bated breath

---

