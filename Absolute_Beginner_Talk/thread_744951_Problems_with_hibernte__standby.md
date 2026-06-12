---
title: "Problems with hibernte / standby"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Jim_in_Germany on 2008-04-04
Hi,

I have recently installed Ubuntu 7.10 Gutsy Gibbon and am having problems with the power management.

If I press suspend, the screen goes blank and the computer's fan continues to run, which I presume is what should happen. However when I press a key to wake the computer up - Nothing! Just a blank screen and a whirring fan. To get out of this  I have to do a hard reset.

If I press hibernate, I get the error message "Pnp - failed to activate device". The computer then powers off completely. When I restart it, Ubuntu starts from scratch - no saved session.

My graphics card is an Nvidia 8600 XTS. This problem occurs both with and without the restricted drivers.

When installing Ubuntu I allocated 5GB for the swap partition. Installed RAM is 4GB.

I found a lot of links online saying "play around with this" or "tweak that", but as I really am a Linux noob I thought it safer to post in a sensible forum before playing around with system settings that I don't yet understand.

This is driving me mad.
Please help.

---

### Post by ajmorris on 2008-04-04
> **Jim_in_Germany said:**
> Hi,

I have recently installed Ubuntu 7.10 Gutsy Gibbon and am having problems with the power management.

If I press suspend, the screen goes blank and the computer's fan continues to run, which I presume is what should happen. However when I press a key to wake the computer up - Nothing! Just a blank screen and a whirring fan. To get out of this  I have to do a hard reset.

If I press hibernate, I get the error message "Pnp - failed to activate device". The computer then powers off completely. When I restart it, Ubuntu starts from scratch - no saved session.

My graphics card is an Nvidia 8600 XTS. This problem occurs both with and without the restricted drivers.

When installing Ubuntu I allocated 5GB for the swap partition. Installed RAM is 4GB.

I found a lot of links online saying "play around with this" or "tweak that", but as I really am a Linux noob I thought it safer to post in a sensible forum before playing around with system settings that I don't yet understand.

This is driving me mad.
Please help.


Hi there,
Hibernation and Standby modes in linux are still rather unstable... how are you trying to hibernate/standby? i.e. are you using suspend2disk?

AJ

---

### Post by Jim_in_Germany on 2008-04-04
Hi AJ,

Only converted to Linux a couple of days ago so not so sure what you mean by suspend2disk. I am still rather GUI fixated so am clicking on the off sign in the top right hand corner of my screen and selecting suspend / hibernate from there.

---

### Post by Jim_in_Germany on 2008-04-04
P.S. I just tried to install Uswsusp with the command:
sudo apt-get install uswsusp
It told me that swap was not active.
I activated swap with sudo swapon -a.
Now when I try to hibernate the machine doesn't crash, but asks me for my password and then comes back with the rather nice error message that "hibernate" didn't work.
Suspend still causes the same problem.
And I don't know if I installed swsusp correctly or not. I presume not ... :-(

---

### Post by Jim_in_Germany on 2008-04-04
Can nobody help me?
This is driving me nuts and I don't want to start tweaking my system willy nilly without a bit of advice.
Thanks.

---

### Post by Jim_in_Germany on 2008-04-04
Hi,

I managed to get s2disk working after installing uswsusp and making some changes to 
/etc/X11/xorg.conf
&
/etc/default/acpi-support

The only thing is that Gutsy Gibbon's version of uswsusp is missing s2ram.

Can somebody explain what I need to do to install this.

I found these instructions. I did 1 & 2, but 3 I don't fully understand 3.

1. install the uswsusp gutsy package
2. get the uswsusp (v0.7) tarball from [http://suspend.sourceforge.net/](http://suspend.sourceforge.net/)
3. build it and install it (you'll need the pciutils-dev and libx86-dev ubuntu packages on top of the build-essential to be able to compile it)

Thanks muchly

---

### Post by nathansoz on 2008-04-04
> **Jim_in_Germany said:**
> Hi,

I managed to get s2disk working after installing uswsusp and making some changes to 
/etc/X11/xorg.conf
&
/etc/default/acpi-support

The only thing is that Gutsy Gibbon's version of uswsusp is missing s2ram.

Can somebody explain what I need to do to install this.

I found these instructions. I did 1 & 2, but 3 I don't fully understand 3.

1. install the uswsusp gutsy package
2. get the uswsusp (v0.7) tarball from [http://suspend.sourceforge.net/](http://suspend.sourceforge.net/)
3. build it and install it (you'll need the pciutils-dev and libx86-dev ubuntu packages on top of the build-essential to be able to compile it)

Thanks muchly


```
sudo apt-get install uswsusp
```

then download the file and extract the tarball

```
sudo apt-get install pciutils-dev
sudo apt-get install libx86-dev
```

cd to the folder where you extracted the tarball

and type

```
./configure
make
make install
```

---

### Post by ajmorris on 2008-04-04
also, for your swap error, can you please post the output of the following Command Line commands:

```
sudo fdisk -l
less /etc/fstab
```

AJ

---

### Post by Jim_in_Germany on 2008-04-05
Hi AJ,

Thanks for replying.
So, s2disk was working fine. I then (following the above advice) installed linux suspend.
Now when I run s2disk I get the following error message:
s2disk: Could not stat the resume device file. Reason: No such file or director

Why????

P.S. No criticism to Nathansoz. This is all my fault


Results of  sudo fdisk -l:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd86768c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        8494       11044    20480000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           11044       19458    67582976+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3               1        7764    62364298+  83  Linux
/dev/sda4            7765        8493     5855692+  82  Linux swap / Solaris
/dev/sda5           11044       19458    67582976    7  HPFS/NTFS

Partition table entries are not in disk order

Results of less /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=13b95a5b-e32c-49d3-8c5c-8a2a10a47f0c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=D6E0B0EBE0B0D2CB /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=A2CEF437CEF40577 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=3240a7c2-6859-4f52-aad4-396f92bcfef6 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

---

### Post by nathansoz on 2008-04-05
Can you try uninstalling uswsusp and reinstalling the one that came with Ubuntu. It would get you back to where you started at least...

Also you may have to uninstall/install s2disk?

---

### Post by Jim_in_Germany on 2008-04-05
Hi,

I actually formatted my machine after getting the above mentioned problems.
I then installed the version of uswsusp that comes with ubuntu.
Again it told me that swap was not active (this time I opted to continue) and ...
... I still get the same error message.

s2disk: Could not stat the resume device file. Reason: No such file or director

I also made all the tweaks I made before 

editing
/etc/X11/xorg.conf
&
/etc/default/acpi-support

as described here:
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

Still doesn't help.

If anyone can give me step by step  instructions, I would also be prepared to reinstall ubuntu again (only takes about 30 mins) 

Thanks

---

### Post by nathansoz on 2008-04-05
Can you give us some specs about your computer? Desktop? Laptop? Year? etc...

---

### Post by Jim_in_Germany on 2008-04-05
Hi,

'tis a desktop, bought last year.
Mainboard: ASUS P5N32-ESLI
Graphics card: Nvidia 8600 GTS.
It's not a brand computer, I chose the components myself.

What else would you like to know?

Jim

---

### Post by Jim_in_Germany on 2008-04-05
P.S.
160GB sata hard disk, 
4 GB ram

---

### Post by nathansoz on 2008-04-05
Well.... I am sorry to say this, but I cant tell what the problem is (although im sure many more experenced people on this forum could). Perhaps you should wait until 8.04 comes out then try that. I was having a lot of compatibility issues on my latptop with 7.10. I installed the beta of 8.04 and viola! everything worked.

---

### Post by ajmorris on 2008-04-05
> **Jim_in_Germany said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        8494       11044    20480000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           11044       19458    67582976+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3               1        7764    62364298+  83  Linux
/dev/sda4            7765        8493     5855692+  82  Linux swap / Solaris
/dev/sda5           11044       19458    67582976    7  HPFS/NTFS

Partition table entries are not in disk order

Results of less /etc/fstab:

# /etc/fstab: static file system information.

# /dev/sda4
UUID=3240a7c2-6859-4f52-aad4-396f92bcfef6 none            swap    sw              0       0


That entry in /etc/fstab, you can remove the UUID=<number> and remove the leading '#' from /dev/sda, so that it mounts using the block device number, instead of a UUID, you can also do this with the other ones if you want.
That line will now look like:
```
/dev/sda4               none            swap            sw              0 0
```

---

### Post by twin_57103 on 2008-04-08
I'm having a similar trouble with Hardy - had to install it because none of the stable versions would run on my hardware (see sig - very similar to the OP).  At first, I was having black screen/total system freezes, and I was able to fix that from the BIOS.  That fixed the Windows sleep/resume problem, and I thought I was done.  I left it to sleep from Ubuntu last night and when I got up this morning, it was off and I got a suspend error (a bubble in the lower right; kicking myself for not taking a screen shot).

I haven't gotten far at all on troubleshooting - I was just overjoyed to have fixed the BIOS problem and here i find this!  I'd appreciate any pointers.  I've read through the thread, but I'm not sure how much to experiment.

---

### Post by Jim_in_Germany on 2008-04-08
Hi,

What did you adjust in the bios? APCI by any chance?
Can you please let me know as this is still driving me mad.

My latest plan is to follow the instructions given here. Haven't had time to do so yet.
[http://ubuntuforums.org/showthread.php?p=4652388](http://ubuntuforums.org/showthread.php?p=4652388)

---

### Post by twin_57103 on 2008-04-08
> **Jim_in_Germany said:**
> Hi,

What did you adjust in the bios? APCI by any chance?
Can you please let me know as this is still driving me mad.

My latest plan is to follow the instructions given here. Haven't had time to do so yet.
[http://ubuntuforums.org/showthread.php?p=4652388](http://ubuntuforums.org/showthread.php?p=4652388)

Jim - yes, it was APCI.  S3 is a deeper sleep mode, but was causing me trouble.  As I understand it, some of the newer boards won't support S1, but I was fortunate that mine does.  I've attached a photo.

I'm glad to have fixed this problem, but disappointed to find more.  At least Windows isn't freezing on me anymore, and Linux shuts itself down rather than freeze - could be a lot worse.  Good luck on yours!

---

### Post by kushykush on 2008-04-08
I have a similar problem.  Ubuntu Hardy Heron 64 AMD fails to turn off my computer. I have ASUS A-8N-SLI Deluxe.  The screen turns blank but the computer does not shut off.  There is nothing in the application to correct this problem.

---

### Post by dgbearcat on 2008-04-13
Heron comes out in 10 days or so, so I'm hoping that it'll fix all of these suspend problems.

---

### Post by twin_57103 on 2008-04-13
I wish you the best on that, but so far I haven't had any luck with suspend/resume in Hardy beta (32-bit).  Let us know how it works out - good luck!

---

### Post by excogitation on 2008-05-22
> **Jim_in_Germany said:**
> 
s2disk: Could not stat the resume device file. Reason: No such file or directory


The config file changed from uswsusp.conf
to suspend.conf so if you're using uswsup 0.7 or later you have to create/rename and adjust the settings.

---

