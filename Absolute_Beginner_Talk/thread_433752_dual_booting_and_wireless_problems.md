---
title: "dual booting and wireless problems"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-05-05
Hi

hey I got a couple of doubts.


Yesterday I installed feisty on my laptop, but when I tried to enter windows xp it said that a system file was damaged, so I installed again windows....
The problem is that now windows starts automatically no matter that ubuntu is in other partition.
Can anybody tell me how to fix it? or can anybody please tell me where to find a "howto dual booting"? 

Now the second problem (and the very reason why I wanted to enter windows) My laptop didn't detect the wireless card and I couldn't connect to internet.... My laptop is a HP Compaq nx6325 turionx2. 



Any help would be really appreciated.

---

### Post by mikewhatever on 2007-05-05
To address the boot problem, check this [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

About the wireless, I suspect you have a broadcom stinker and probably will need ndisrapper. Anyhow, first, you need to figure out the exact type, so either check in Windows device manager, or in Ubuntu, open the Terminal (Application>Accessories>Terminal) and type 
> sudo lshw -C network

---

### Post by Jorge32 on 2007-05-05
I've seen the guide for dual, but as far as I understand it refers to commands for the terminal.... and I can't enter Ubuntu, I am on Windows...

I really forgot a couple of things I learned months ago in my desktop wint ubuntu so I am kinda of newbie again :S, please can you tell me what to do? or can anybody please tell me? Will I have to install again Ubuntu? is ther a way of just installing the grub from the alternate CD?

---

### Post by mikewhatever on 2007-05-05
All I posted before can be done from either Ubuntu or the Live CD if you have one.

Here are different ways to reinstall GRUB [http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

All you have to do is follow instructions. If there is something you think you do not understand, do ask.

---

### Post by Jorge32 on 2007-05-05
ok everything went ok until it gave me to choose which device to use as root file system, I select  /dev/sda2 because it is where Ubuntu is, and then the option reinstall grub boot loader.
then it comes something like this:

```
[!!] Enter rescue mode


You need to make the newly installed system bootable, by installing the GRUB boot loader on a bootable device. The usual way to do this is to install GRUB to the master boot record of your first hard drive. If you prefer, you can install GRUB elsewhere on the drive, or to another drive, or even to a floppy.

The device can be specified using GRUB's "(hdn,m)" notation, or as a device in /dev. Below are some examples:
- "(hd0)" or "/dev/hda" will install GRUB to the master boot record of your first hard drive (IDE);
- "(hd0,1)" or "/dev/hda2" will use the second partition of your first IDE drive;
-"(hd2,4)" or "/dev/hdc5" will use the first extended partition of your third drive (SCSI here);
-"(fd0)" or "/dev/fd0" will install GRUB to a floppy.

Device for boot loader installation

 _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ 
  
<Go Back>                                              <Continue>
```

So I first tried with hd0,1 and it said fatal error, continue or go back so I tried witbh hd,0 , hd2,4 , hd2 , /dev/sda2 ... and always the same error message and everything in red. .... Can anybody please help me? this is first time I use the dual boot

---

### Post by mikewhatever on 2007-05-05
Is there any chance you can get and use the Super Grub Disk? [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

It should be able to restore Grub to the mbr without you having to mess with choices.

---

### Post by jargoman on 2007-05-05
you probably want to install grub on the master boot record. thats the most common choice
 
/dev/hda

that's my guess, worth a shot

---

### Post by Jorge32 on 2007-05-05
yes, i already solved that problem thanks a lot.

Now I am dealing again with the problem of my wireless card, because I can't make it run.
I instaled ndiswrapper and I couldn't make it recognise the wirelles card, wll in fact i don't know what to do. 
Please can anybody tell me how to make this a little more like step by step, because I can't understand some guides that I have found or that some peope had told me to search on ..:confused:

---

### Post by mikewhatever on 2007-05-06
Can you please post the output of 
> sudo lshw -C network

It will show what wireless devices there are, and perhaps, someone can help you.

---

