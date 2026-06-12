---
title: "Resizing the partition error."
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Nigters on 2007-04-22
Hello Ubuntu guys

I decided i want to try Ubuntu out in a real install, so i wanted to resize my current partitions.

I have a C drive with 20 Gb. and a D drive with 60 gb. now in Gparted the first one is listed as HDA1    thats normal... now the thing is that the 60 Gb thats called D is first listed as 60 Gb extended, and when i try to modify the size of that i cant even draw the box to set the new size.... below that listed this way

HDA1
HDA2 extended
.........HDA5 (remove . then its the right way, added to show the placement of the text)


when i then try to rezise the HDA5 i can perfectly specify that i want it to be 25 Gb, i can press the proceed button, but when i click apply and ok in the confirmation box, i simply gets an error saying that the task couldnt be done, no error number etc. now i cant just delete my whole D drive to install Ubuntu as all my games is on that drive (C is windows and OpenOffice only)

I really wanna install Ubuntu because im tired of windows and mr. BG. Windows rock, everything else suck. 

What is wrong here, hope i described it the best way i could, wanted to post a Screenshot, but i dont know where the button is on the live-cd, please help me

Best regards... me!

---

### Post by leibowitz on 2007-04-22
The best way to resize an existing windows partition is
[LIST=1]
[*]To have an NTFS partition
[*]Backup all the data of all your partitions and disk, just to be sure.
[*]To defrag this partition before any resizing.
[*]And last, resize it!
[/LIST]

Now you know what to do.

---

### Post by Nigters on 2007-04-23
The file system is NTFS
I defragged all my HDD
Backed up all important stuff... BUT i get the error saying the task could not be completed (resizing)

Best regards

---

### Post by antoz on 2007-04-23
If your D drive is an extented partition you should be able to add an other partition within, have you got enough free space? Can't figure out why it will not let you resize though. Back up all the data you have in there and see if you can create the Linux partitions inside your extented partition (in fact you can have multiple logical partitions inside an extented partition)
I normally just right click on the partiton I want to alter an take it from there, hope this may help,A

---

### Post by Nigters on 2007-04-23
There is no unpartitioned space on my HDD, the D drive is listed as extented.

So when there is no unpartitioned space, can i instead create a logical partition ON the D drive it self, so that space will be "reserved for Linux? if so... how?

Thank you for the reply

Best Regards   me

---

### Post by leibowitz on 2007-04-23
I had one time no luck with the resizing. It's possible you can't resize it, and it's preferable because probably something wrong has been detected and it avoids to break anything.

Creating a partition inside another one is impossible as it. You need special tools, or dynamic partitions.

Your solution may be to install Ubuntu from inside Windows. As you don't have more space to create a partition, this will use the free space in your D partition.

Warning: I never tested this process. But it has been tested by many people and it's not bug-free, it's possible it don't work. But at least it should not break anything and won't need to create a partition.

[http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)
More information here: [https://wiki.ubuntu.com/install.exe/Prototype](https://wiki.ubuntu.com/install.exe/Prototype)
And here: [http://ubuntuforums.org/showthread.php?t=338279](http://ubuntuforums.org/showthread.php?t=338279)

---

### Post by Nigters on 2007-04-23
Cant i just tell the Ubuntu installer on the live-cd to install it on the free space on the D drive? (60Gb...40 free)
or is it impossible to change where the installer installs it? (in the installer i couldnt find a place where i could select which partition to install on...

hmm i could also just buy a new HDD... what if i did that would i stillbe able to dual-boot? or would that be impossible due to being on 2 different HDD's?

---

### Post by leibowitz on 2007-04-23
You can't put it on the free space as it. You need to resize the NTFS partition, then it will create all needed partition in the unpartitionned space.

Free space isn't sufficent.

Note that if you can't resize your D partition, it may be because this partition has errors, or is not well defragmented. But it seems that it's caused by errors rather than fragmentation. Please check both carefully anyway.

Now if you buy a new HD, you can easily install ubuntu onto this. Then you will need to install the GRUB bootloader menu (this will be installed on the first HD MBR) to be able to boot all OS.

Again, please try to fix your D partition to be able to resize it. Maybe checkdisk / fdisk or what ever tool you have on Windows to fix that.

---

### Post by Nigters on 2007-04-23
[QUOTE=leibowitz;2516104
Now if you buy a new HD, you can easily install ubuntu onto this. Then you will need to install the GRUB bootloader menu (this will be installed on the first HD MBR) to be able to boot all OS.

[/QUOTE]
What is HD MBR? anyhow if i get a new HDD can i simply install Ubuntu onto that and the Bootloader will automatically install AND detect that i also have Windows installed?

---

### Post by leibowitz on 2007-04-23
HD MBR I mean your Hard drive Master Boot record, which is where GRUB will be installed.

And of course it will detect windows and configure itself for it. No problem sir.

---

### Post by Inxsible on 2007-04-23
> **Nigters said:**
> Hello Ubuntu guys
 
I decided i want to try Ubuntu out in a real install, so i wanted to resize my current partitions.
 
I have a C drive with 20 Gb. and a D drive with 60 gb. now in Gparted the first one is listed as HDA1 thats normal... now the thing is that the 60 Gb thats called D is first listed as 60 Gb extended, and when i try to modify the size of that i cant even draw the box to set the new size.... below that listed this way
 
HDA1
HDA2 extended
.........HDA5 (remove . then its the right way, added to show the placement of the text)
 
 
when i then try to rezise the HDA5 i can perfectly specify that i want it to be 25 Gb, i can press the proceed button, but when i click apply and ok in the confirmation box, i simply gets an error saying that the task couldnt be done, no error number etc. now i cant just delete my whole D drive to install Ubuntu as all my games is on that drive (C is windows and OpenOffice only)
 
I really wanna install Ubuntu because im tired of windows and mr. BG. Windows rock, everything else suck. 
 
What is wrong here, hope i described it the best way i could, wanted to post a Screenshot, but i dont know where the button is on the live-cd, please help me
 
Best regards... me!
 
You mentioned that you were using GParted for creating/resizing your partitions .
Do you by any chance have Vista installed? GParted will not be able to resize Vista partitions. Something MS changed abt NTFS in Vista, so you would need to resize the windows partitions using Vista's partitioner and then try to install Ubuntu.
 
Of course if you are not using Vista, I am not really sure what could be the cause except that your drive has some errors.

---

### Post by Nigters on 2007-04-23
Thank you all for the replies, trying it all when i get home, and no i dont have Vista installed.:D

Ty for the help!

---

