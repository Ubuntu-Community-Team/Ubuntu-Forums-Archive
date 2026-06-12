---
title: "I have a REALLY old mac..."
date: 2008-09-11
forum: Apple Hardware Users
---

### Post by G-Dub on 2008-09-11
Hey guys, i have a really really old mac. It's a powerbook 1400cs. Would Ubuntu be able to run on it?

---

### Post by snowpine on 2008-09-11
Hi G-Dub,

I don't know much about that specific model, but here are the recommended minimum hardware requirements from Ubuntu.com ([https://help.ubuntu.com/community/Installation/SystemRequirements):](https://help.ubuntu.com/community/Installation/SystemRequirements):)

> Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution
    * Sound card
    * A network or Internet connection

---

### Post by G-Dub on 2008-09-11
yea, i think this has a 1.5 gb hard drive...lol. Basically all i want to run on it is openoffice. Are there any other flavors of linux that have really low system requirements that can run openoffice?

---

### Post by snowpine on 2008-09-11
> **G-Dub said:**
> yea, i think this has a 1.5 gb hard drive...lol. Basically all i want to run on it is openoffice. Are there any other flavors of linux that have really low system requirements that can run openoffice?

Check out this thread, it's pretty complete:

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

Obviously not all of them will work with a Mac, so you'll have do a little research. I haven't used a Mac since I made the switch to Linux so unfortunately I can't take you any farther. Good luck!

---

### Post by G-Dub on 2008-09-11
wow! very informative. I think my issue will be finding one that works with 64mb of RAM...

---

### Post by gaussian on 2008-09-11
Note that most distros on that list are Intel only (not for old Macs).

---

### Post by panhandle on 2008-09-11
I think I had the PPC version of edgy running on a really old ibook clamshell with 64 mb of RAM and a 6GB HD.

Try running a really lightweight GUI like fluxbox and it might be fine.

Obviously, if you can find more RAM, that would be good.

---

### Post by G-Dub on 2008-09-11
If anyone else is wondering... it appears that [Fluxbuntu]("http://fluxbuntu.org/explain.html") is the best option. The have support for older macs. I will give it a try and let you guys know how it goes!

---

### Post by y@w on 2008-09-11
You might also want to check out [Slackintosh]("http://workaround.ch/"). It's Slackware for running on Apple hardware.

---

### Post by snowpine on 2008-09-12
> **G-Dub said:**
> If anyone else is wondering... it appears that [Fluxbuntu]("http://fluxbuntu.org/explain.html") is the best option. The have support for older macs. I will give it a try and let you guys know how it goes!

Hi G-Dub, the PowerPC version of Fluxbuntu never materialized, plus I don't think you have the hard disk space or processor speed to run it anyway. You need something waaaay lighter than Fluxbuntu, and I frankly have my doubts that Openoffice is going to run on a 133mhz PPC with 64mb of ram. :)

from everymac.com:

> The Apple Macintosh PowerBook 1400cs/133 features a 133 MHz PowerPC 603e processor, 16 MB of RAM, and a 1.3 GB hard drive in a black portable case with a 11.3" color dual-scan display. The built-in display of the PowerBook 1400cs/133 supports 16-bit color, and also can support up-to 8-bit color on an external monitor with an optional video card. The PowerBook 1400 series included new features such as an internal CD-ROM drive, a "swappable" drive bay, and "BookCovers" that can customize the look of each PowerBook.

---

### Post by oswaldkelso on 2008-09-12
His is part of a thread on the debian ppc mailing list. It deals with one way installing debian on a old mac. 

It may help you, you do need a mac os cd and [bootx]("http://penguinppc.org/historical/benh/")
With such a small amount of ram using debian sarge may be a better option. Even then I doubt you would get a usable X. As a command line only machine then it may be quite possible.  


> I have OS9.2 on a circa 500 meg HFS+ partition, leaving the rest for debian (I will add here something I didn't mention in the original post - don't format this space using the OS9 CD, just leave it as "free space"). I use BootX as a boot loader. I used the netinstall CD for Etch.

First boot into OS9 with the Etch CD in the CD drive. Copy the vmlinux kernel from the CD install directory and put it into the kernels folder in the system folder. Copy the initrd.gz image to the BootX folder. Select the BootX application and tell it to use the vmlinux kernel and set the RAM disk to initrd.gz image. In the additional kernel arguments box, type "DEBCONF_PRIORITY=low" (no quotes). Boot into linux.

The installer will start. Go through this answering questions. When you get to the partitioning section, Partman will run. You should choose "manual" as your partitioning method. Select the free space and make a linux partition with Ext3 format and choose to mount "/" on it. On my machine this then becomes /dev/hda7/. Also make a swap partition (/dev/hda8). The sizes of these will depend on your HD size. You can also obviously choose to split up your file system so that not everything is under the root (/). I also named my /dev/hda7/ as "debian". Probably makes no difference, but I did notice that the HFS+ partition (/dev/hda6) was called "untitled" as was /dev/hda7/ and did not think this a good idea.

Once you are happy with how the partitions look, write out the partition table. This will destroy the apple driver partition, but don't worry, you can recover from this providing you have your OS9 CD. More of this later...

Continue with the installation and install the base system and whatever else you want.

Despite being in the "expert" install mode, after install of the base system, the installer went straight into trying to install quik as the boot loader without giving me the option to avoid this. However, since quik only works with ext2 file systems, it bombed out with an error and allowed me to continue. I go all the way through to the point where it says the install is finished and wants me to remove the install CD and then select reboot. We stop at this point and swap to a new console (alt right arrow).

In here we can access the newly installed file system *and* the mac HFS+ partition. At the prompt, type "cd /" to make sure you are in the root of the file system. On my system, there was a folder at the root called "mnt" that contained nothing. I therefore typed in:

mount -t hfsplus /dev/hda6 /mnt

(note: I had put "/dev/hda7" here in the first post regarding getting Etch installed. hda7 on my system is actually the linux root partition. When deciding on which partition to mount here, the partitioning step will help, since partman lists the partition numbers).

This mounted the mac HFS+ partition under "mnt". You could use another directory, since mount just takes over the directory and then will give it back when you "umount", but I prefer to use an empty directory just in case.

Now you can cd to mnt and you should see your mac HD.

cd to /target/boot/ and cp whatever is symlinked to vmlinux and initrd (do a "ls -l" on the directory to see the details) over the mac HD.

Now "umount /mnt", change back into the installer console (alt left arrow) and remove the netinstall CD from the drive. Pop in your OS9 CD, because you will need it.

Reboot by selecting that option in the installer.

Your machine will boot into the OS9 installer (even without you holding down the "C" key). If you get a flashing disk symbol with a question mark in it, you have not got your OS9 CD in the drive. Remember that the partitioning  has trashed the mac hard disk driver partition so your mac does not know what to do.

Once the OS9 installer disk has booted and you are at the window where you can choose to install OS9, go to the utilities folder and select drive setup. Once this has found the drives on your machine, select the one at the top (on mine it said "not mounted") and then select from the drop down menu at the top of the screen to "update apple hard disk driver". Once you do this, you get a message saying you need to reboot. Do this.

Now we can get back into OS9 on the hard drive.

Once in OS9, move the vmlinux kernel you copied above into the kernel images folder in your system folder. Put the initrd image anywhere you want.

Select the BootX application.

Select the linux kernel you just moved. Select "use specified ram disk" and choose the initrd image you copied above. Now in the additional kernel arguments box, enter "root=/dev/hda7" (without the quotes). Obviously your root file system might not be hda7, so change that appropriately. Save these settings to the defaults. You may want/have to enter other kernel arguments (eg for video), but I did not have to.

Now boot into linux.

BootX should hand over to linux and your new install will boot up. At least it did for me ;-)

If you upgrade to a new kernel / initrd image, you will need to mount the HFS+ drive and copy these over to it so that you can specify these in the BootX app.

Hope this has been of some use to someone.


---

### Post by G-Dub on 2008-09-12
> **snowpine said:**
> Hi G-Dub, the PowerPC version of Fluxbuntu never materialized, plus I don't think you have the hard disk space or processor speed to run it anyway. You need something waaaay lighter than Fluxbuntu, and I frankly have my doubts that Openoffice is going to run on a 133mhz PPC with 64mb of ram. :)

from everymac.com:

yea i noticed it never materialized after i posted that...lol. I think i may just give up on this project. Too much work.

---

### Post by DGortze380 on 2008-09-14
commandline debian etch, install fluxbox and openoffice. good luck, no idea if it will work, but thats the smallest most stable OS/desktop that I was able to find for a PPC.

---

