---
title: "Unable To resize my screen Resolution"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by yossarain on 2006-08-26
hi all

i have installed UBUNTU from this link

[http://mirror.pacific.net.au/linux/ubuntu-releases/6.06/](http://mirror.pacific.net.au/linux/ubuntu-releases/6.06/)

for my Intel PC and the problems i am facing are:-

1. The default resolution it has setup is 800*600 pixels while my monitor best works on 1024*68 pixels. I tried going to SYSTEM-> Preferences-> Screen Resolution but of no help as I am unable to change the default settings.

2. While Everybody said it is so user-friendly, i beg to disagree. I don't know how to look for my hard disks or opening files. Could anyone please direct me how to open my hard disk, access files etc.

3. How do I install my network configuration? My sound card is well detected but not my modem. I use a broadband service.

GRUB is loading well. Some of system specs are as below:

80 GB hard disk
1 GB RAM
2.66 GHz

I am sorry if some of these questions have been asked before and that they have been answered. But I am very exhausted to search for them. Any links or explanation would be highly appreciated.

---

### Post by Perfect Storm on 2006-08-26
> 1. The default resolution it has setup is 800*600 pixels while my monitor best works on 1024*68 pixels. I tried going to SYSTEM-> Preferences-> Screen Resolution but of no help as I am unable to change the default settings.

It might be that your monitor isn't supported.
Which graphic card do you have? If you have installed the proper driver for it, then, make sure you have your monitor manual first:
<ctrl>+<alt>+<F1>
```
sudo dpkg-reconfigure xserver-xorg
startx
```


> 2. While Everybody said it is so user-friendly, i beg to disagree. I don't know how to look for my hard disks or opening files. Could anyone please direct me how to open my hard disk, access files etc.

Well, it's about that you are use to do one thing . Now you have to learn a new thing to do things. To learn a new thing isn't allways easy. What you mean looking for specific? You mean browsing through the files?

---

### Post by yossarain on 2006-08-26
Thanks for the reply but still I am left with some more questions than some real satisfying answers.

I don't have a graphics card and yes i have been given a driver support on a cd which i am not sure works in LINUX, as i haven't checked. Will be doing that

I am sorry i don't understand the code you have put in the box and where am i to type it or use it. I am very new to Linux so basics would be greater use.

Secondly,  I have book with me by the name : Beginning Ubuntu Linux From Novice to Professional, which hasn't given any troubleshooting in this regard. But the problem is the version he explains is of UBUNTU 5.0 wherein at the end of the boot process and after restarting I am supposed to get a option for choosing my screen resolution.

Keeping that apart one more worrying aspect is when i go to Places-> Computer i see all my Hard disks. But there are no names for it. When i try to double-click and open them, i recieve a error message saying 'UNABLE TO MOUNT' then pressing for details it says "some hda\6a" Some technical detail. I am not able to open any hard-disk.

What i fear is have i installed right UBUNTU. My system is of Intel Make but it is 64 bit processor. The one I downloaded is as i said before the option : Ubuntu for Intel X86.

Is it one of the reasons for such performance? thanks again for reply but i repeat earlier SUSE which i formatted for this was at least showing me the hdd's and me able to browse through folders. THe problem was with locating the sound cards, network cards etc..

and lastly a small tutorial or guide for setting up network connections.

---

### Post by FizDev on 2006-08-26
> **yossarain said:**
> I am sorry i don't understand the code you have put in the box and where am i to type it or use it. I am very new to Linux so basics would be greater use.


As he said, just press on Ctrl+Alt+F1
Login the do the sudo dpkg-reconfigure xorg-server thingy (what he told you)

> **yossarain said:**
> 
What i fear is have i installed right UBUNTU. My system is of Intel Make but it is 64 bit processor. The one I downloaded is as i said before the option : Ubuntu for Intel X86.


I think it should work anyway, only you won't have the advantages of your 64bit processor... it's simply gonna be as if you were running with a 32bit

---

### Post by calvinthomas on 2006-08-26
> **yossarain said:**
> Thanks for the reply but still I am left with some more questions than some real satisfying answers.

I don't have a graphics card and yes i have been given a driver support on a cd which i am not sure works in LINUX, as i haven't checked. Will be doing that

I am sorry i don't understand the code you have put in the box and where am i to type it or use it. I am very new to Linux so basics would be greater use.

Secondly,  I have book with me by the name : Beginning Ubuntu Linux From Novice to Professional, which hasn't given any troubleshooting in this regard. But the problem is the version he explains is of UBUNTU 5.0 wherein at the end of the boot process and after restarting I am supposed to get a option for choosing my screen resolution.

Keeping that apart one more worrying aspect is when i go to Places-> Computer i see all my Hard disks. But there are no names for it. When i try to double-click and open them, i recieve a error message saying 'UNABLE TO MOUNT' then pressing for details it says "some hda\6a" Some technical detail. I am not able to open any hard-disk.

What i fear is have i installed right UBUNTU. My system is of Intel Make but it is 64 bit processor. The one I downloaded is as i said before the option : Ubuntu for Intel X86.

Is it one of the reasons for such performance? thanks again for reply but i repeat earlier SUSE which i formatted for this was at least showing me the hdd's and me able to browse through folders. THe problem was with locating the sound cards, network cards etc..

and lastly a small tutorial or guide for setting up network connections.


Ok, I'll try and say this in a step-by-step way:

1) First open a terminal by clicking applications, then accessories, then terminal.

2) Type "sudo dpkg-reconfigure xserver-xorg" without the quotes and press enter. This will then ask you several questions, for the most part you can just keep hitting enter, at one point it'll talk about resolutions, use spacebar to select the resolution you want (1024x768) then keep pressing enter.

3) restart your computer and it should then be in 1024 x 768 (and you'll be able to choose it in the method you mention)

The harddisks you are trying to open are your other partitions, by default they are not available in ubuntu, search the forums for Mounting windows partitions for how to enable them.

Your ubuntu partition will be under 'Filesystem' rather than the harddisks, that is where all your files etc will be. For full functionality (i.e. deleting files in certain folders, copying and pasting to certain files etc) open a terminal (as above) and type:

"sudo nautilus" without the quotes, press enter, type your password, press enter, this will open your filesystem as root user with full access to everything.

For setting up a network, search through these forums, you'll find a how-to!

As a previous poster said, installing the x86 version is absolutely fine, only installing a 64bit edition on a 32bit processor is a problem. I use 32bit Ubuntu with a 64bit AMD processor

Calv

---

### Post by Coffee Break on 2006-08-27
Calvin,

Thanks for your step by step answer.  I just loaded Xubuntu 6.06 a few hours ago on a very old laptop.  I'm searching the forums to resolve a few issues, but your answer fixed my resolution problem.  So far, I'm extremely pleased with Xubuntu.:)

---

### Post by yossarain on 2006-08-27
Sorry for the delay in replying but my screen resolution has been fixed now and it is the way i wanted. thanks calvin for such detailed explanation.

I don't know if still my thread title holds good for a new query but as you said i tried searching through the forum for MOUNTING WINDOWS PARTITIONS IN UBUNTU (FYI ,the drives in my system are C, D ,and E which are in NTFS(WINDOWS XP), FAT32, FAT32,respectively) and landed up with this site

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

i tried following the instructions at this page to the tee, after typing in "sudo fdisk -l" i have gotten something similar to this 

[B]Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes 

Device Boot Start End Blocks Id System
/dev/hda1 * 1 1911 15350076 7 HPFS/NTFS
/dev/hda2 1912 19457 140938245 5 Extended
/dev/hda5 1912 14716 102856131 83 Linux
/dev/hda6 14717 17278 20579233+ 83 Linux
/dev/hda7 17279 17404 1012063+ 82 Linux swap / Solaris
/dev/hda8 17405 19457 16490691 83 Linux
[/B]

i have just pasted it from the site above mentioned.
but after typing in the command "sudo nano /etc/fstab" the screen that followed isn't exactly the same as that of what was shown, infact, it is not showing "/dev/hda1/"  and the code that follows and also the following lines are missing. I have two cd-roms, one DVD and one VCD.

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0

fearing changing anything might affect my system, i have stucked on to windows and making sure i get right answer before venturing UBUNTU. please help..

and also there aren't any easy explanation the way you have told me through the forums i searched to enable internet, i have a broadband connection that is connected through a modem.

---

### Post by apc15x on 2006-08-27
Thank you Calvin Thomas, I didn't ask the question but I have been really looking how to change my screen resolution and your information work.

---

### Post by calvinthomas on 2006-08-27
Glad I could help, i'll have a look about the harddisk thing but it may be best to open a new thread if you can't find an answer in the forum!

Calv

---

### Post by imwkwk on 2007-06-08
Thanks Calvin...Followed your step by step and it fixed my problem...Had a hard time during install, because all I had was 640x480 off the disk...Finally figured out to hold ctrl+tab to move around and eventually got my laptop going...You were a big help...I look forward to using Ubuntu and ditching the MS at home...

---

