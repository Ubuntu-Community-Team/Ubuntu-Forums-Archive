---
title: "help with triple boot mac, windows 7, ubuntu 9.10"
date: 2009-10-26
forum: Apple Hardware Users
---

### Post by borovy3488 on 2009-10-26
Ok, I've been trying to get this to work for awhile, and can't find a solution. I have installed windows 7 via bootcamp, and everything went smoothly.

Then, to install ubuntu, I just resized the windows partition. Now, I have all three installed, but cannot boot into them from refit. All it shows is mac and windows. I was told that all I had to do was run the partition tool once in refit, and it would find all of them. 

So, I tried. But when I try to run the partition tool, I get an error that says it will not touch the disk because somefilename.efi returned unknown. Does anyone know how I can fix this? I would greatly appreciate it.

Oh yeah, I'm on a 4,1 macbook. When I get into ubuntu, there are no proprietary drivers for my wireless. How can I get those??

Thanks in advance,
Wayne

---

### Post by borovy3488 on 2009-10-26
New Info::

OK, I figured some stuff out.  If I just let my macbook reboot, it goes into refit.  If I select Mac from refit, everything boots up fine.  However, there is no icon for linux, and if I choose the windows icon, it locks up the computer and I have to do a hard restart.  

Now, if I hold the option key on restart to bring up the bootcamp menu, and I select windows instead of the refit option, it loads grub, where I can choose mac, windows, or ubuntu.  The only one I tried was ubuntu, and it worked perfectly.

Does anyone have a work around for this issue?  Obviously, GRUB is already installed, so what should i do??

---

### Post by macaholic on 2009-10-26
The only thing I can think that might help is completely reinstalling rEFIt. I've never had much luck with it myself, I find it slow and unreliable, so  Ijust hold down option during boot and select the partition I want to boot.

---

### Post by borovy3488 on 2009-10-27
OK, so I uninstalled everything and tried again.  Same problem occured.  Everything was working perfectly after the windows install, but the ubuntu install makes it not work.  

Now, the refit will not show linux, so I am trying to run the partition tool from refit. It says that it will not touch the disk because a return of 'Unknown' is given.  

The only disk whose format is 'Unknown' is also given the boot flag "bios_grub."  I'm guessing that this is the grub bootloader.  How can I make refit recognize this so that it can recognize them and boot windows and linux???  Any ideas?

---

### Post by borovy3488 on 2009-10-27
Since the install, I tried removing refit to see if it would help anything.  If I hold alt on restart, I get to choose from Mac and Windows.  When Windows is chosen, it says GRUB loading, then takes me to a black and white boot menu.  I can load Mac, Windows, and Ubuntu.  

I dont really care about keeping refit or not, because this solution works.  Now, is there any way that I can make this menu come up at startup and skip the hold alt or whatever.  Also, is there any way to make this menu look better?

Thanks again,
Wayne

UPDATE: OK, so from GRUB, ubuntu will boot, and so will Windows.  However, Mac fails to boot for some reason.  Any ideas on getting refit to work?

---

### Post by borovy3488 on 2009-10-27
Maybe a screen shot will help.  I can mount the unknown partition in ubuntu.  All it contains is a lost and found folder that cannot be opened.[ATTACH]133336[/ATTACH]

---

### Post by sebovzeoueb on 2009-10-28
I've just posted here how I managed my triple boot: [http://ubuntuforums.org/showthread.php?t=1303459](http://ubuntuforums.org/showthread.php?t=1303459)
It seems to me like rEFIt is a bit unecessary, as when I booted into Linux or Windows from it, it just took me to GRUB anyway. Mac OS doesn't show up in my GRUB at all, I just let my computer boot normally to start OS X, and hold [alt] to go to Ubuntu or Windows. Does this not work for you?

P.S. not sure what is going on with your partitions! Looks like you have rather alot of them...

---

### Post by itagaki on 2009-10-29
>The only disk whose format is 'Unknown' is also given the boot flag "bios_grub."  I'm >guessing that this is the grub bootloader.  How can I make refit recognize this so that it can >recognize them and boot windows and linux???  Any ideas?

you have to install GRUB into the linux partition. do not create a new one for it... this way you can fix the gptsync error message. but i am still not able to get into the grub boot menu...

---

### Post by besweeet on 2009-10-29
I don't use or like rEFIt. I did what you did. I just use the GRUB boot loader when choosing Windows while holding ALT, then I choose the entry for Ubuntu. I can go into all three whenever I please.

---

### Post by pelle.k on 2009-10-30
I dont use refit either. I boot grub (installed to linux root partition, NOT the mbr) for linux/windows. It still shows up as "Windows" in the mac boot menu (when pressing the alt key at bootup) though.

Just a quick note, apparently windows have to be the last partition on the hard drive. I learned that the hard way. Also, if you squeeze in a new partition before the windows partition, or modify a partition before the windows partition (at any point in time after windows is installed, that is), you may have to modify boot.ini to use a new partition number as boot target. It's often +-1 from the existing target. That's for windows XP however, i wouldn't know how to do the same with Vista/7.

Another "issue" i've had, is that when modifying the partition table at some point, the "bootable flag" got erased on the partition i want to have the "alt menu" to boot, with some cryptic error message thrown in my face as a result of this when selecting it. This is easily fixed with the fdisk util on OS X though. Basically you do;
```
sudo fdisk -e /dev/disk0
print
flag <nr>
write
exit
```
"print" will print the table, and an asterisk should mark the slice that is marked as bootable. If no/wrong slice is bootable, note the number it should be, and use it with "flag" as <nr>.
btw, a slice is basically the same thing as a partition.

Personally, i use one partition for each and every OS. Extended partitions make it all way too complicated when having to deal with these kind of troubles/errors. I wouldn't know how to handle extended partitions with fdisk for example. This is a bit limiting, but it works very well for me anyway.

I hope that i gave some valuable pointers, should anyone have problems with getting a triple boot up and working. I am no expert at this myself, mind you.

---

### Post by besweeet on 2009-10-30
So I'm having trouble myself with this stuff...
 
I reinstalled the Windows 7 boot loader because I couldn't boot the "Windows 7" entry in GRUB 2 (it would kick me back to GRUB). So the Windows boot loader is installed now. I've tried using EasyBCD and its various Linux boot things but none can boot my ext4 partition for 9.10.
 
I installed rEFIt in OS X, and it only shows my Windows and Mac OS X drives. I can boot my Windows one and it will load the Windows boot loader. 
 
**SO**, my problem right now is booting Ubuntu. I can't seem to find a way to do it. I'd like to reinstall GRUB 2 but I have absolutely no idea how to do it. I guess there isn't a nice packaged installer that can automatically do it :(.

---

### Post by pelle.k on 2009-10-30
You may use the ubuntu live cd to reinstall grub. I seem to recall that there is an automated "reinstall grub" option on the live cd as well, but i might be wrong there.
If you choose to do it from the live session, open a terminal and run
```
sudo grub
find /boot/grub/stage1
```
find will show you what target ubuntu is, use that below instead of **(hd0,1)**
```
root (hd0,1)
setup (hd0,1)
quit
```

You may, or may not (i don't know if it's necessary with refit) have to activate the "bootable" flag on that partition using an OS X terminal and fdisk as i described above.

---

### Post by besweeet on 2009-10-30
After I do:
```
find /boot/grub/stage1
```

I get:
```
Error 15: File not found
```

Getting very mad over here. Was all happy for Ubuntu until I removed GRUB 2. I didn't think it would be this damn hard to install. I also thought that I'd be able to boot Ubuntu by using EasyBCD.

---

### Post by pelle.k on 2009-10-30
> **besweeet said:**
> After I do:
```
find /boot/grub/stage1
```

I get:
```
Error 15: File not found
```

Getting very mad over here. Was all happy for Ubuntu until I removed GRUB 2. I didn't think it would be this damn hard to install. I also thought that I'd be able to boot Ubuntu by using EasyBCD.

I'm sorry to hear you have such troubles getting it up an running. Maybe something changed with grub2 making the steps i described to you obsolete, but i doubt it. What did you mean by "removing grub2"? If you did "apt-get remove" it in any way, you have to reinstall ubuntu. That's a small price to pay to get it working again.
If you didn't "apt-get remove grub" in any way, maybe these instructions would help you. As i said, i haven't got much experience with grub 2; [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

I'm fairly sure EasyBCD's grub4dos component doesn't handle ext4 partitions though. That's why installing grub to the linux root partition is still necessary.

---

