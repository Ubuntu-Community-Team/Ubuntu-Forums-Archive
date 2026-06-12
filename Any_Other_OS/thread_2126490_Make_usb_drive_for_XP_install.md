---
title: "Make usb drive for XP install"
date: 2013-03-17
forum: Any Other OS
---

### Post by joey00 on 2013-03-17
I have no Windows machines, and no floppy drives.

I need to create an USB boot/install drive from either the XP cd or the iso file.

The additional complication is that I need to include whatever is needed to install to a SATA HDD.

----
On  Linux there are a number of apps which will handle multi-boot installs  for various distros. So a big usb stick can be used to install a  selection of distros.

Is the same possible (from ubuntu) with a selection of Windows CDs (W98, XP, Win7, Vista)?

I found threads on this subject, but they seem to be unworkable or start from a Windows environment.  :mad:

Joey

---

### Post by sanderj on 2013-03-17
What's your goal? Install Ubuntu? Install Windows XP?

---

### Post by joey00 on 2013-03-17
> **sanderj said:**
> What's your goal? Install Ubuntu? Install Windows XP?

As the header says, I want to make an usb stick, from which I  can install XP (with SATA drivers extra).

I rarely use Windows, but occasionally I need to use an app that only runs on Windows. So, I just need the ability to install it easily,

---

### Post by sanderj on 2013-03-17
> **joey00 said:**
> As the header says, I want to make an usb stick, from which I  can install XP (with SATA drivers extra).



And you're asking that in "Ubuntu General Support" ... ? :confused:

Sorry ... can't help you.

---

### Post by ikt on 2013-03-17
Moved to Other OS.

---

### Post by joey00 on 2013-03-17
> **sanderj said:**
> And you're asking that in "Ubuntu General Support" ... ? :confused:

Sorry ... can't help you.

Since I don't see a section for the making of USB boot disks, I thought this might be the right place for it. It is essentially the ability of Ubuntu to make a boot disk of an unusual type, no?

Perhaps you can suggest a better classification?

I am sorry you are unable to be helpful.

---

### Post by mips on 2013-03-17
> **joey00 said:**
> 
I need to create an USB boot/install drive from either the XP cd or the iso file.

Is the same possible (from ubuntu) with a selection of Windows CDs (W98, XP, Win7, Vista)?


Google "128mbdos.img" and download it, it's only 1MB in size, alternatively get it from my google drive below.
[https://docs.google.com/file/d/0B10iPl6hgL_dY055Ml8tcTkzZ1k/edit?usp=sharing](https://docs.google.com/file/d/0B10iPl6hgL_dY055Ml8tcTkzZ1k/edit?usp=sharing)
It contains Freedos.
Use dd to write the image to a USB stick **sudo dd if=128mbdos.img of=/dev/sd[COLOR=#ff0000]x[/COLOR]** where x is the USB Stick. DO NOT SPECIFY THE WRONG OUTPUT DEVICE AS IT WILL OVERWRITE IT!!!

You will see it creates a small partition with freedos on it. On the remaining space create a FAT32 partition and simply copy the contents of the cd/iso over to this new partition (make sure you can see hidden files from your file manager, ctrl-h in thunar). You can also dump any additional drivers on this partition for sata etc. and just point windows to it.

Now boot from the USB, change the drive letter to d: or whatever it is for the large FAT32 partition and simply run setup.exe. I have not tried using this method with Vista & later but it works for WinXP and earlier.

This says you can use unetbooting to load Win7 [http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/](http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/) but I have never tried it.

Alternatively you can create a small XP/Win7 VM and run the MS Win7 download tool from there which will create a bootable USB for you from a iso image of Win7 (& later I think). [http://www.microsoftstore.com/store/msstore/html/pbPage.Help_Win7_usbdvd_dwnTool](http://www.microsoftstore.com/store/msstore/html/pbPage.Help_Win7_usbdvd_dwnTool)
This will also allow you to use tools like nLite & vLite to slipstream service packs & drivers into the images shuold you have the need.

Hope this helps.

---

### Post by mips on 2013-03-19
Come right?

---

### Post by joey00 on 2013-03-20
Thx for this. It sounds like the way to go! :-)

I will try it out and report back.

It occurs to me that I can create several partitions for each system I want to have available. Is this so? Presumably Windows /DOS sees them as Drive D, E, F etc.?

I had a look at unetboot earlier, but it didnt seem to work. Maybe it was the hardware, maybe me.

Sorry to reply slowly - I had work distractions.  :-(

Thx again for your help.  :-)

---

### Post by mips on 2013-03-20
> **joey00 said:**
> 
It occurs to me that I can create several partitions for each system I want to have available. Is this so? Presumably Windows /DOS sees them as Drive D, E, F etc.?


Should work or you could also try just having a separate folder for each OS.

---

### Post by joey00 on 2013-03-31
hi, 

sorry for the delay, I have been experimenting.

The link you gave for Freedos doesnt seem to work - File does not exist. But I managed to find a copy of 128mbdos.img.

I used your dd instructions (with changes for shifted letters) on an empty 4Gb memory stick. This created a small FAT16 partition on the memory stick.

I then partitioned the remaining stick to FAT32 with partitions (gparted) for each flavour O/S.

That did not work.

I did the same with a single FAT32 partition (and the flavours in directories) with no better success. :(

At the time I was discouraged, with other things to do, so I didnt go further.

You are going to ask exactly what happened, but it was something like syntax error, and I didnt make a note. (sorry)

I am now going to repeat the experiment and I will report the exact result.

Thx for your help so far.

Joey

---

### Post by joey00 on 2013-03-31
Addendum
========

I tried again, I now remember what happened.  :)

The boot part works fine. I get a simplified DOS screen with prompt.

But that's all.

I cannot find the windows drives or directories.

I suspect this has something to do with FAT16 / 32 bit issues.  If so, what to do?

Joey

---

### Post by mips on 2013-03-31
I'll try this again tomorrow some time if I remember and let you know. I know this worked for me. If you don't see a reply from me in 48hrs it means I forgot so please PM me a reminder.

---

### Post by mips on 2013-04-03
Ok just tried the 128mbdos.img and it did not work. I'm probably confused but I know for a fact I have done this before. I've got another dos image save on my HDD but I don't remember how I created that one. I'll have a look and see if that one works.

---

### Post by joey00 on 2013-04-05
Well, I am not sure if this is a relief or not!:confused:

I was hoping that I had not just done something stupid, but I still don't have a working boot...

The idea that the FAT16 cannot see FAT32 files and directories seems right to me. But I am not sure where that logic takes us. 

I can copy and unpack an iso image file using dd I believe, but then I need a large FAT16 directory/drive to put it on. It would be within the 4Gb limit for XP, but not much else.

But that leaves 2 questions: are the files on windows FAT16 compatible, and what is the total size of the files on an install disc for later windows versions.

I feel like I am looking for something small in a very dark room!  :-)

---

### Post by mips on 2013-04-07
Seeing as I cannot remember how I did it back in the day I started googling and found the following for you. The first link looks like it will do everything and  more for you ;)

[http://www.sarducd.it/](http://www.sarducd.it/)

[http://www.sjpc.org/mppcclub/contents11/How%20to%20create%20a%20bootable%20USB%20flash%20drive.pdf](http://www.sjpc.org/mppcclub/contents11/How%20to%20create%20a%20bootable%20USB%20flash%20drive.pdf)
[http://www.neowin.net/forum/topic/948072-how-to-install-all-versions-of-vista-7-8-from-a-single-usb-hard-drive/](http://www.neowin.net/forum/topic/948072-how-to-install-all-versions-of-vista-7-8-from-a-single-usb-hard-drive/)
[http://wintoflash.com/overview/en/](http://wintoflash.com/overview/en/)

Let me know if those links work, SARDU looks like the one you want.

---

### Post by joey00 on 2013-04-19
After some digging and testing, I have the following. Maybe someone can help to find a way forwards?

I can create the 128Mb Freedos partition as per instructions. The maximum partition size for FAT16 is 2Mb (MSDOS). That should be enough for XP.

So, to enlarge the new partition, using gparted should be a simple step, right?

No!!! There is an acknowledged bug in gparted 15 that prevents this.  Also, I do not know how to remove gparted 15 and substitute gparted 14.  They suggest this workaround, while they work on a fix.

I have looked for alternative paritioners but cannot see anything that  works. Maybe I can run a partitioner from a CD, but this is an ugly  solution at best.

Once I have a 2Gb FAT16 partition, surely I can copy XP files onto that partition to complete the boot stick?

However, there are 2 things which strike me as problems further ahead:
1.  Is XP going to install correctly when its files are run from FAT16?
2. XP is reaching the end of its life. Later versions of windows are  bigger than XP. I assume they might be too large for that FAT16 limit.  Is there then a FAT32 image which can be installed in the same way as  Freedos?

Does anybody have more insight in this direction?

Joey

---

### Post by mips on 2013-04-19
[http://www.linuxquestions.org/questions/linux-general-1/creating-the-ultimate-grub2-setup-windows-installer-live-linux-installer-live-813544/](http://www.linuxquestions.org/questions/linux-general-1/creating-the-ultimate-grub2-setup-windows-installer-live-linux-installer-live-813544/)

---

### Post by mips on 2013-04-20
Grub4Dos method info,
[http://www.rmprepusb.com/tutorials/how-to-create-a-usb-drive-that-will-install-vista-win7-and-server-2008](http://www.rmprepusb.com/tutorials/how-to-create-a-usb-drive-that-will-install-vista-win7-and-server-2008)
[http://www.rmprepusb.com/tutorials/winiso](http://www.rmprepusb.com/tutorials/winiso)
[http://www.rmprepusb.com/tutorials/install-xp-from-an-iso](http://www.rmprepusb.com/tutorials/install-xp-from-an-iso)

Not exactly what you are looking for but I'm just adding stuff to this thread as I go along which others might find useful.

---

### Post by mips on 2013-04-20
GRUB2 can also boot ISO images so I will hunt around and see what I can find out wrt to making it work with windows images.

Somehting else I found here while looking [http://ubuntuforums.org/showthread.php?t=2035071](http://ubuntuforums.org/showthread.php?t=2035071)

---

