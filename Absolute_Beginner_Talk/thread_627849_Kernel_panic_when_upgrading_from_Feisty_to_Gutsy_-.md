---
title: "Kernel panic when upgrading from Feisty to Gutsy - some beginner's  questions"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by taistelutipu on 2007-11-30
Hi fellow beginners!

As I already stated in the title I have a huge problem with the upgrade from Feisty to Gutsy for which I was trying to get help in the Installation and upgrade forum but I got no help there. I guess my questions were too newbie like, e.g. how to open a command prompt before the computer is booting or something like this. So I decided to try my luck here. Here is a full account of the events so far. I hope someone can help me since I really don't know what to do with it and I want to help my sister (it's in fact her laptop and not mine).

My sister ran Feisty on a COMPAQ Evo N610c laptop and everything worked fine. When she upgraded to Gutsy the first error was that the internet didn't work anymore. Since she had experienced already network problems in her dorm earlier she thought a restart might do the trick. But on restart the internet still didn't work. She tried to fix it in the network settings and for this she needed root rights. But the root login window didn't work either. It just froze. She decided then to restart again and then the computer didn't even boot anymore, it stopped right in the beginning of the booting process with the infamous message:
[ 8.898347] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

Now a couple of newbie questions:
Does the upgrade from Feisty to Gutsy include also a kernel update? If so, it is possible that the kernel needs to be rebuilt or recompiled? When I entered the error message above in google I got hundreds of hits which hinted at similar problems when upgrading the kernel. On of the suggestions was the following: "You can either include the filesystem support in your kernel or create an initrd to load the module at startup."
Another problem could be the lilo entry not matching: "The problem was in lilo, i asumed that my loader was pointing to hda3; when in reality it was pointing to hda1"

I'd like to know how I can get these informations, e.g. which kernel version my sister uses or how her grub (she's not using lilo) entry looks like. The problem I encounter is that the blinking cursor at the end of the message freezes, i.e. I can't write anything in the command line.
Is there a way how to interrupt the erronous booting procedure before it freezes to get to these informations? I searched for hours in forums to get help for the problem but I didn't find anything. I guess it is considered common knowledge so that no-one includes it in the instructions how to deal with kernel related problems.

I run a debian distribution at home which my friend set up for me. I know how to maintain it but I never set anything up myself from the very beginning. So when it comes to the basics I'm a beginner. Further I haven't been present when he set up my sister's computer so I don't know anything about it (kernel version, file systems, modules etc.) I can't access anything with the knowledge I have right now since the booting process halts after a couple of seconds.

I suspect that the update somehow messed up the root account since my sister could not log in anymore, for example the directory appointed to root does not match reality anymore or something like that.

Can anyone tell me what I can do about it? My sister recently changed from Windows to Linux so she knows even less than I do. My friend mentioned above lives now in another country so he can't help us with it and I'm now in charge of our distributions. Thank you very much in advance for your advice. It's much appreciated.

Best wishes
taistelutipu

PS: Do you need any other technical specifications of the laptop? Which ones? It will be a bit hard to get them because I don't have the computer here, my sister lives far away but I'll try my best.

---

### Post by djchandler on 2007-11-30
Here's the link for the laptop specs:
[http://h18000.www1.hp.com/products/quickspecs/11382_div/11382_div.HTML](http://h18000.www1.hp.com/products/quickspecs/11382_div/11382_div.HTML)

As for the GRUB problems, all I can do is commiserate. Almost the same thing happened to me when upgrading from Feisty to Gutsy on a desktop Athlon 64-based system with VIA motherboard chipset. Fortunately, I had all my data backed up, so I just blanked the HD and did a fresh install of Gutsy. I believe a lot of us had problems making the switch from Feisty to Gutsy. Ask your sister if the upgrade froze the system. That's what happened to mine. Because of the freeze, the GRUB menu didn't get updated. I blamed the automatic installation of Compiz Fusion with my old 32mb Nvidia GeForce 2 MX200 graphics card. I had problems until I removed Compiz (no Open GL support) and re-installed the free nv driver (not the non-free "nvidia" driver.)

DJ

---

### Post by taistelutipu on 2007-12-02
Thank you very much for your help, djchandler.

Unfortunately my sister didn't make a backup before the update. She's new to Linux so she didn't think there would be so much difference between the updates that the adept manager proposed from tine to time and the upgrade from feisty to gutsy. Should have asked me first before doing it...

But now it is to late to rant about what ifs, all too late now. What can I do now with her laptop? My sister reported that at first glance everything seemed to work just as it should but she had no internet connection. Rebooting didn't help so she assumed there was something wrong with her network configurations and she went into Settings  > Internet & Network > Network Settings.
To be able to change anything there you need root access and this is where the problem really started. The root account froze, it just did nothing when she entered the password. 
When she rebooted the next time she got the message about the kernel panic not syncing and the problems with mounting the root fs on an unknown-block. Could that be caused by a failed update of the GRUB menu?

---

### Post by taistelutipu on 2007-12-02
I just talked to my sister and got the following information out of her:

she has the following kernels:
kernel 2.6.22-14-generic
kernel 2.6.22-14-generic (recovery mode)
kernel 2.6.20-16-generic
kernel 2.6.20-16-generic (recovery mode)
kernel 2.6.20-15-generic
kernel 2.6.20-15-generic (recovery mode)

My assumption was that something went wrong with the latest kernel so I advised her to boot the  previous one, the 2.6.20-16 and heureka, kubuntu ran again, but when she wanted to save her last changes on a USB stick the device was not recognized by the system.

I adviced her to look in /etc/fstab and she copied the entry for me:
# /dev/sda1
UUID=[a 32 digit hexadecimal number hyphenated four times to end up with 36 digits] / ext3    defaults,errors=remount-ro 0       1
# /dev/sda3 
UUID=[a 32 digit hexadecimal number hyphenated four times to end up with 36 digits] /home  ext3    defaults        0       2
# /dev/sda2 
UUID=[a 32 digit hexadecimal number hyphenated four times to end up with 36 digits] none swap sw 0 0 
/dev/scd        /media/cdrom0   iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

no entries for the removable devices - that's why the USB stick could not be mounted.

what strikes me most is the # before the 3 partitions, that means that it is only a comment, like e.g. in my fstab file and has no effect:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

I told her then to tell me which block devices she has in /dev and there I found the usual ones cdrom cdrw dvd dvdrw fd0 loop0 and then some I don't have on my debian distro:
ram0, ram1, ram2... ram15, then the partitions sda, sda1, sda2, sda3 and then sdb (I suspect it is for the USB device) and sr0 (no idea what this is).

I would delete the # before the devices in etc/fstab and add an entry for sdb based on the model of my etc/fstab entry for sdb. Could the solution be so easy? 

My sister is really happy now, she was able to burn all her important files to CD before I would attempt anything with the fstab. I told her to save one version of the current etc/fstab version so that in case all goes wrong I know what was the starting point. 

What do you think of this? Could a corrupt fstab be the reason for all the hassle?

Thank you very much again for your previous entry, djchandler, your comment was really helpful and I think I'm close to the solution now (hopefully). I told my sister to boot only with the old kernel until I have sorted out why the new one would not work.

---

### Post by taistelutipu on 2007-12-10
The problem is nearly solved, the computer booted normally but the trick with the USB didn't work. First, right after the change of etc/fstab the default USB icon appeared, when my sister plugged in an USB device but when clicking on it she got an error message involving hal. 

In the meantime my own laptop starts behaving in an odd manner, it can't recognize my camera anymore. Until the last update the camera was detected as a USB mass storage device but now it is detected as an USB mass storage interface. To tell it shortly, I can't transfer photos from the camera, when accessing the directory via the console it is empty and the ownership has mysteriously changed from root to user and some other weird stuff going on such as renaming of filenames and modification of the read and write rights.

I read the tutorial of mounting USB devices such as sticks, cameras, mp3 players, etc. on this page [http://www.ma.utexas.edu/users/stirling/computergeek/usb.html](http://www.ma.utexas.edu/users/stirling/computergeek/usb.html) and I found my problem in the following paragraph:

    Since the kernel maps the USB device to a SCSI device, all that you need to figure out is WHICH SCSI device it is. Just use the command (as root) "fdisk -l". This will list all of the known drives, including any /dev/sd* SCSI drives.

When I enter fdisk -l I get the following output for the removable devices (after the list of hard drive partitions hda1, hda2, etc.:
Disk /dev/sda: 261 MB, 261488640 bytes
16 heads, 32 sectors/track, 997 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xa234f597

Device Boot Start End Blocks Id System
/dev/sda1 * 1 997 255215+ 6 FAT16

This is my USB stick but there is no entry for the camera (which used to be sdb1), therefore I assume it is no longer recognized as a SCSI drive. What do I need to change in my settings to return to the former two block devices sda and sdb? When plugging in two USB sticks the first one is actually sda1 and the second sdb1. It doesn't work with the camera though. I think the key to this problem lies in the kernel which is no longer able to map the USB to a SCSI device. How can I "tell" the kernel to do so? 

When thinking of this problem a bit longer it seems to me that my sister's kernel has the same problem. It can't map the USB to a SCSI device, telling from what she told me about the recognition of her USB in dmesg there was no statement about the SCSI. Could that be the solution? Do I have to recompile the kernel :confused: help!... it's getting pretty above my knowledge now.

---

### Post by Mvveen on 2007-12-10
Hi,

I had the same issues on two separate machines, I would upgrade, it would fail. I would reboot and would end up with all sorts of issues, both machines ended up with a kernel panic. Any attempts to complete the upgrade would result in broken package errors.

Crash and burn...

I would advise you to boot of a live cd, backup from there and do a fresh Gutsy install.

---

### Post by taistelutipu on 2007-12-10
Thank you very much for your advice :)

Booting is currently not really a problem, my sis can boot with the previous kernel version and she can access all files normally, CD and floppy work normally - in fact everything but the USB devices which are not recognized. A complete reinstallation seems a bit drastic but at least, if all else fails, she is able to burn all to CD or DVD before reinstalling everything. On the other hand I guess that in the end my sis will have to reinstall because running all the time the old kernel ist not really an option. And there is the problem with updates you mentioned. I'm trying to prepare her for the reinstallation ;-)

I'm waiting for a reply to my problem with the USB in the debian help forum, maybe someone knows what to do with the kernel and the USB. 

I'll keep you informed how things are going here. Thanks again for your input.

---

