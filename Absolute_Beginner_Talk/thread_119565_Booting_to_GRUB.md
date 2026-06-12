---
title: "Booting to GRUB"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by thepomegranateprophecy on 2006-01-19
Ok, so I just installed Ubuntu over the weekend after numerous trys. It was a long and quite treachourous path, but ultimately led me to a very nice brown place.

So, here is my setup:
Dell DImension 8300
BIOS Revision 1.05
5 Partitions:
#1: Linux System
#2: WIndows XP System
#3: Swap
#4 Imaginary divider:
     #5: Windows Files
     #6: Linux Files
Ubuntu 5.10 installed initially. 

Problem:
Grub will not load automatically after boot. I have to his Boot Options, and then say load Primary Master Drive. Then, I get GRUB. Otherwise, I get XP's defualt OS chooser, which cannot launch Ubuntu. So, while luckily I can now launch Ubuntu, I wanted to make it a lot easier for me. I don't quite enjoy trying to catch a key while my boot screen flashes by. If you need any text let me know, and I'll get it. Thanks in advance. By the way, I'm loving Linux.

---

### Post by Sutekh on 2006-01-19
When you get to the GRUB menu, does Windows load corectly, does Ubuntu?  

If so, then go into your BIOS settings and make sure that the primary Master Drive with GRUB is booted by default.  That would be the easiest way.

---

### Post by thepomegranateprophecy on 2006-01-19
[QUOTE=Sutekh]When you get to the GRUB menu, does Windows load corectly, does Ubuntu?  

If so, then go into your BIOS settings and make sure that the primary Master Drive with GRUB is booted by default.  That would be the easiest way.[/QUOTE]
Yes, they both boot. I did precisely that. I went into BIOS setup to see if I could make that the default, but the only options I have when booting are Hard Drive (C:) and CD. Well, that doesn't help much. Could the fact that the letter designation doesn't coorelate have something to do with the issue?

---

### Post by Sutekh on 2006-01-19
[QUOTE=thepomegranateprophecy]Yes, they both boot. I did precisely that. I went into BIOS setup to see if I could make that the default, but the only options I have when booting are Hard Drive (C:) and CD. Well, that doesn't help much. Could the fact that the letter designation doesn't coorelate have something to do with the issue?[/QUOTE]

There must be an option somewhere in the BIOS that lets you select which hard drive to boot from.  Are you talking about selecting the boot device as your PC boots up or actualy going into the setup?  

I know with my BIOS that I can press F11 and select the boot device (HDD or CD) but not the specific device.  I have to go into my BIOS setup by pressing Del, and choose the boot order or my HDDs.

What is the brand of your BIOS?

---

### Post by thepomegranateprophecy on 2006-01-19
[QUOTE=Sutekh]There must be an option somewhere in the BIOS that lets you select which hard drive to boot from.  Are you talking about selecting the boot device as your PC boots up or actualy going into the setup?  

I know with my BIOS that I can press F11 and select the boot device (HDD or CD) but not the specific device.  I have to go into my BIOS setup by pressing Del, and choose the boot order or my HDDs.

What is the brand of your BIOS?[/QUOTE]
Yeah, see I don't know how to do the latter. Del doesn't do anything for me. What brand of BIOS, no clue. It came with my Dell. Here let me see if Dell's site says anything.

Well, I just went to their website. Couldn't find anything except a BIOS update, which didn't help.

---

### Post by Sutekh on 2006-01-19
[QUOTE=thepomegranateprophecy]Yeah, see I don't know how to do the latter. Del doesn't do anything for me. What brand of BIOS, no clue. It came with my Dell. Here let me see if Dell's site says anything.

Well, I just went to their website. Couldn't find anything except a BIOS update, which didn't help.[/QUOTE]
Ok so what I'm reading is that you can't get into your BIOS settings, just the boot menu, right?  And by BIOS settings I mean you get to choose everything, time/date, system voltages, power off modes, etc.  Its not a laptop is it, I've found with my last 2 laptops that there was no obvious way to enter BIOS settings.

Anyway, when your computer restarts, at the very first screen that appears, is there any indication as to what your BIOS is?  My very first screen at power on, reads in the top left 
'Phoenix Award Bios 5.06'

You could always try keys like 'Delete', and the 'F#' keys until you get in.  Or read the manual, lol, it might have they keystroke you need to access the BIOS.  

If none of this works you can install GRUB onto the MBR of the HDD that boots by default, and get all the options you need.

---

### Post by thepomegranateprophecy on 2006-01-19
No, I can get into BIOS setup. It just has no other option under Boot Sequence than HD & CD, which isn't helping. So, basically is there some hidden advanced setup screen I'm miising. And this MBR, everyone tlaks about it. Enlighten me? And if that would work, how would I go about doing this?

---

### Post by WoodPost on 2006-01-23
I too have a 8300 and have the same problem, any help would be appreciated.

---

### Post by Luke771 on 2006-01-23
Is the Partition where Grub is installed set to active?
If not, maybe making that partition active could solve your problem.
If the Grub partition is already active, then it looks like that particular model has some problem with Grub; maybe booting to the Windows partition and manually configuring the Windows Boot Manager will do the trick.
Yes I mean that: configure the PC to use the Windows bootloader.
You need  to make the Windows partition active; you can use a Linux System Rescue CD, or some Partition Magic-like software. Select the Windows partition, make it active and reboot; now the system should boot directly to Windows like it did when it was the only OS installed.
Now, boot o to Ubuntu; if you can't do that because you have made the windows partition active and the machine will only boot to windows, then you can boot from a Linux Live CD (Ubuntu Live CD is available at [http://www.ubuntulinux,org](http://www.ubuntulinux,org) ), if you have a FAT32 partion, mount it 
assuming you are using an Ubuntu LiveCD, and your FAT32 partition is hda6 (if not sure use QParted to find out)

```

sudo mkdir /media/fileshare
sudo mount -t vfat /dev/hda6 /media/fileshare

```

(if you are running some liveCD other than Ubuntu, try "su" instead of "sudo")
if you don't have any FAT32 partition use only the first one of the two lines.

Then, assuming that hda2 is the windows partition and hda1 is the ubuntu partition (reading your post it looks like they are , but use QParted anyway if you're not 101% sure); open a terminal window and run:

```

sudo dd if=/dev/hda1 of=/media/fileshare/ubuntu.bin bs=512 count=1

```

That will create a 512Kb file called ubuntu.bin in your FAT32 partition (the one you see as "fileshare" on the desktop if you are using Ubuntu) or in your /media/fileshare directory if you dont have any FAT32.

OK, now if you do NOT have the FAT32 partition you will need to write the file on a floppy or on a CD because you will have to copy it to C:\ under Windows; if you DO have the FAT32 partition, and the file "Ubuntu.bin" is actually there, or after you have copied the file on a CD, floppy, USB (FAT32) drive, zip drive, 5'' floppy, tape drive or whatever (even a remote file storage server will do fine), then you can reboot to windows.

Once in windows, go to your FAT32 partition (probably D:\) or instert the CD or floppy where you have the file (or log in to the remote file storage server etc), and copy ubuntu.bin to C:\.
In the Windows Explorer menu bar, go to Tools --> Folder Options --> View and select "Show hidden files and folders", now you should see a file called Boot.ini or Boot in C:\ ; right click it and under Properties uncheck the "read only" checkbox, then  open it with Notepad and add the last line

[in Windows, edit C:\boot.ini and add the following line]
```


C:\ubuntu.bin="Ubuntu Linux"

```

You may find aline about some "Unknown Operating System" and change it to C:\ubuntu.bin="Ubuntu Linux" or, if Windows is the only OS listed, simply add the line at the end of the file.
It can be a nice idea to change the default 30 seconds timeout to a more reasonable 7 or 10 seconds; I think 30 is way too much,  5 secs can be kinda stressy...
Whatever.
Those are details, the important stuff is that if you can't use Grub you can try to use the windows boot loader, I haven't tried this myself because Grub works fine for me, but I am fairly sure that it will work.  It is worth a try, anyway. Good luck.

---

### Post by thepomegranateprophecy on 2006-01-25
Yeah, I fixed it. I had to re-install both operating systems and this time I didn't install XP's NTLDR and guess what it works, yeah!

---

### Post by xurizaemon on 2007-05-04
[Same problem over here]("http://ubuntuforums.org/showthread.php?t=433213").

I will try the method posted above. Thanks.

---

### Post by xurizaemon on 2007-05-16
I tried adding my boot sector to XP's NTLDR, but I'm afraid it didn't work for me.

When the system boots, if I hit "F12" then select "Primary Master" from the menu (which lists CD-R, Floppy, Drive C:, Primary Master, Primary Slave, Boot to utility partition, and Detect IDE Disks) then Ubuntu boots fine.

However, the Dell BIOS, in all its genius, omits the option to select Primary Master for one of the boot drives.

I tried this using ubuntu.bin dd'd from my /dev/sda1 (ubuntu root partition). Next time I reboot I will try it from my /dev/sda instead; GRUB is installed there, but Dell BIOS ignores it and leaps straight onto XP's warty doodle at the first opportunity.

*sigh* ... it's a nice machine, and was a good deal, but the previous system had a stock AMI BIOS that just plain worked. Why, DELL, did you even need to improve on a working system?

Oh, the big colour logo. Of course. Thanks for that.

---

