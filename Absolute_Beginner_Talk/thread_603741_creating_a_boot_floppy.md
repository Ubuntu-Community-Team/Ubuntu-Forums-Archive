---
title: "creating a boot floppy"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by davexnet on 2007-11-05
Hello,
I just installed Ubuntu to a harddrive that already had dual boot Vista and XP.
I installed it to it's own logical partition and chose not to install Ubuntu's boot loader
during the install.

I expected that somewhere during the install it would ask me if  wanted to create a boot floppy
to boot up ubuntu but it did not. 

My plan is to install GRUB on the Linux partition and use Vista's boot loader using this method:
[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

How can I create the boot floppy and /or is it possible to use the LIVE CD to boot the
installed Ubuntu ?

TIA,
Dave

---

### Post by eluzi on 2007-11-05
In the article you mentioned there are instructions on how to install GRUB even after the Ubuntu install... Did u try this ?

Step 1 – Install GRUB on the Linux partition (outside of MBR)

As Windows Vista will replace the Master Boot Record (MBR) with its own, we need to relocate GRUB elsewhere by running grub-install with the Linux partition as a parameter.

•        On Linux, launch a Terminal with root privileges

•    Find the name of the partition Linux is installed on by running fdisk –l (the partition you’re looking for is the one whose system is Linux, can be  something like /dev/sda1 or /dev/hda1. For the rest of this post, I’ll use /dev/sda1)

•    Install GRUB on the Linux partition by running : grub-install /dev/sda1

---

### Post by eluzi on 2007-11-05
In the article you mentioned there are instructions on how to install GRUB even after the Ubuntu install... Did u try this ? U could boot using the Live CD and execute it from there...

Step 1 – Install GRUB on the Linux partition (outside of MBR)

As Windows Vista will replace the Master Boot Record (MBR) with its own, we need to relocate GRUB elsewhere by running grub-install with the Linux partition as a parameter.

•        On Linux, launch a Terminal with root privileges

•    Find the name of the partition Linux is installed on by running fdisk –l (the partition you’re looking for is the one whose system is Linux, can be  something like /dev/sda1 or /dev/hda1. For the rest of this post, I’ll use /dev/sda1)

•    Install GRUB on the Linux partition by running : grub-install /dev/sda1

---

### Post by davexnet on 2007-11-05
The grub -install command does not work.

Instead it opens to a grub shell of some kind waiting for sub commands.
I think something else is needed, I haven't figured it out yet.

Dave

---

### Post by davexnet on 2007-11-05
Is there a bug in the install ?
I ask this because during the Ubuntu install, it tried to install the boot loader
on HD0 MBR (IDE in my PC), but I have installed Ubuntu to a 2nd drive, SATA, which is also
the drive set to be the boot drive in the BIOS.

Something odd here.

Secondly,I would have liked to install GRUB to the linux partition, not the MBR.
Why no such option in the install ?
Other distributions have this.

---

### Post by logos34 on 2007-11-05
> **davexnet said:**
> Is there a bug in the install ?
I ask this because during the Ubuntu install, it tried to install the boot loader
on HD0 MBR (IDE in my PC), but I have installed Ubuntu to a 2nd drive, SATA, which is also
the drive set to be the boot drive in the BIOS.

actually that's normal,  grub is set to detect ide channels/drives first, so grub often ends up on ide disk mbr even if sata is first in bios boot order.

> Secondly,I would have liked to install GRUB to the linux partition, not the MBR.
Why no such option in the install ?

You have to change the destination device from (hd0) to (hd0,**0**) or **/dev/sda1** format in the 'advanced' box (assuming for example's sake root is the first partition):

[http://img519.imageshack.us/my.php?image=feistydual18cv5.png](http://img519.imageshack.us/my.php?image=feistydual18cv5.png)

If you want to send grub to floppy you would enter **(fd0)**

(unlike the alternate desktop cd which actually prompts you, it's not very apparent but it's possible nevertheless)

See this for grub boot floppy (you'll have to adjust the paths if working from live cd):
[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

---

### Post by davexnet on 2007-11-05
Thank you logos34.  When I installed the product, my linux partition ended up being
sda9, with swap partition sda10.

What is (hd0,0)  < how does this notation work?

Now that I've installed ubuntu without GRUB, is it best to completely reinstall and set
\dev\sda9 here ? [http://img519.imageshack.us/my.php?i...ydual18cv5.png](http://img519.imageshack.us/my.php?i...ydual18cv5.png)

Assuming I do get GRUB installed, will the floppy disk creation work?
It certainly doesn't work now with no GRUB installed. (Using the instructions you posted:)
[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

Dave

---

### Post by logos34 on 2007-11-05
> **davexnet said:**
> Thank you logos34.  When I installed the product, my linux partition ended up being
sda9, with swap partition sda10.

What is (hd0,0)  < how does this notation work?

If sda9, then use /dev/sda9 or (hd0**,8**)  

('8' because grub starts counting at 0)

> Now that I've installed ubuntu without GRUB, is it best to completely reinstall and set
\dev\sda9 here ? [http://img519.imageshack.us/my.php?i...ydual18cv5.png](http://img519.imageshack.us/my.php?i...ydual18cv5.png)

can't link to the image...but it might be easiest to reinstall
> 
Assuming I do get GRUB installed, will the floppy disk creation work?
It certainly doesn't work now with no GRUB installed. (Using the instructions you posted

yes, you need to find a way to run grub-install successfully before it will work (and it should--I use it).  

I don't know why you're having a problem running it frm the live cd...are you sure you logged in as root or used sudo

sudo grub-install /dev/sda9

?

Make sure to manually mount the root partition rather than just clicking on it in nautilus and having it mount at default '/media/disk' location (the latter invariably gives me trouble):

Ex:

sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda9 /mnt/ubuntu
cd /mnt/ubuntu
sudo grub-install /dev/sda9

---

### Post by davexnet on 2007-11-05
Thanks for your detailed answer.  Your example is much appreciated because I'm very much
a novice in Linux.

Looks like I'll have to delete the Linux install (Probably from inside Windows XP's disk manager)
because when I tried to boot the Live CD, instead of eventually taking me to the GUI,
I get a black screen with the verbiage Busy box,and a command prompt initramfs>

I read up on it, but I don't understand why it's appearing here.  Something to do with a possibly
damaged harddisk installation?  Why does that bother the LIVE CD?

---

### Post by davexnet on 2007-11-05
Sorry to be a pain in the backside.
I tried your command sequence - here's the output:

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda9 /mnt/ubuntu
ubuntu@ubuntu:~$ cd /mnt/ubuntu
ubuntu@ubuntu:/mnt/ubuntu$ sudo grub-install /dev/sda9
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:/mnt/ubuntu$ 

Some other step need to be done ?


PS got the LIVE CD to work by choosing the first option "start or install",
however, it's in 800*600 - little difficult to navigate!

---

### Post by logos34 on 2007-11-06
> **davexnet said:**
> Looks like I'll have to delete the Linux install (Probably from inside Windows XP's disk manager)
because when I tried to boot the Live CD, instead of eventually taking me to the GUI,
I get a black screen with the verbiage Busy box,and a command prompt initramfs>

I read up on it, but I don't understand why it's appearing here.  Something to do with a possibly
damaged harddisk installation?  Why does that bother the LIVE CD?

I doubt it's the hard drive (hope not).

[/bin/sh: can't access tty; job control turned off]("http://ubuntuforums.org/showthread.php?t=415009")

could be as simple as a floppy left in the drive (which the live cd hardware detection appears to choke on if present).  Or any number of other things. 

Reinstall would be the best way to go.

> PS got the LIVE CD to work by choosing the first option "start or install",
however, it's in 800*600 - little difficult to navigate!

Making some progress.  Go back and try 'safe graphics' mode.  Or open a terminal and run 

sudo dpkg-reconfigure xserver-xorg

-choose another video driver, like 'vesa'.  Go throught the interactive accepting defaults/hitting enter for the most part.  Then ctrl+alt+backspace to restart desktop. System>prefs>screen resolution

Otherwise for[ grub-install try this]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall"):

sudo grub-install **--root-directory=/mnt/ubuntu** /dev/sda9

or try chrooting:

ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
>ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda9 /mnt/ubuntu
>ubuntu@ubuntu:~$ **sudo chroot /mnt/ubuntu**
>root@ubuntu:/#** sudo grub-install /dev/sda9**
>root@ubuntu:/#** sudo update-grub**

---

### Post by davexnet on 2007-11-09
Hello ,
I'm getting somewhere  (I think !) I reinstalled Ubuntu and chose where grub should be loaded.
Installed into /dev/sda10 so I chose (hd1,9).

I used the dd command to copy over the first 512 bytes as my intention is to use Vista's
boot loader.  It's the procedure described here:
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

When I choose Ubuntu from Vista's boot menu, I do indeed get the grub boot menu.
When I select Ubuntu, I receive error 22 - no such partition.

This seems odd since it was setup as part of the install.
Any thoughts?

TIA,
Dave

---

### Post by davexnet on 2007-11-10
I fixed it myself.  I edited the menu.lst and changed (hd1,9) to (hd0,9)

Why was it necessary?  I used (hd1,9) during the install and it installed Grub in the proper place,
the partition containing the linux root.

However, a boot time, (hd1,9) was invalid.

---

