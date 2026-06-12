---
title: "Help me re-install GRUB."
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by madu on 2006-06-02
Hi guys..

I have 2 hdds.. yesterday I installed Ubuntu with one hdd removed.. so now the GRUB only sees one.. I have a Windows partition in the other one which I used to run Matlab.. 
How can I make GRUB see that drive and the windows partion in that.. How can I go about doing that.. I have the cable removed at the moment..

Thanks a lot guys..

Madu

---

### Post by catlett on 2006-06-03
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html#Installing-GRUB-using-grub_002dinstall](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html#Installing-GRUB-using-grub_002dinstall)
Do not enter "#" that just shows that the following text goes into a command line. What it says is that if you can boot into your install you can install grub by running grub-install. I don't know if sata drives are different so if you have one I don't know if these commands are right.'
But for  installing grub after you boot into your ubuntu install, run ```
sudo grub-install /dev/hda
``` Then run```
 sudo grub update
``` That will update the menu list and hopefully grub saw the other install.
Try that first and reboot. If it doesn't work then post again. You can edit your grub menu to see the other installation (assuning you are booting into your install with grub and the only issue is that the other drive's OSs weren't recognised)

---

### Post by BoneKracker on 2006-06-03
EDIT - didnt' mean to step on catlett's suggestion - it wasn't there when I started typing what's below.

It doesn't sound to me like you need to reinstall GRUB.

I'm not quite clear on your situation, though, so I'll try to address several possibilities here.

I ) Assuming you don't have a whole Windows install on that second disk -- that it's just MATLAB stuff and not the OS.   (If you DO, skip to part II):

a) Plug and pray: 
If you plug the drive in and boot the machine, the new version of Ubuntu should just detect the drive and mount any Linux partitions for you (they'll show up on your desktop and under "Places").  The drive should be available to you and you can make use of any unused space on it by using the Disk Manager utility found under the System Menu (System > Administration > Disks).  You probably want to select some unused space and create a Linux partition (with an ext3 filesystem, if for general use).

b) If you want access that Windows partition from Linux:
I don't believe it will just automatically mount an NTFS parition unless you set it up to do so (because Linux can mangle the NTFS filesystem, and for security of the other OS).  If you do want access it you can set that up under the Disk Manager as well (I believe that will only give you read-only access, but if it does allow you read-write access, I recommend you limit it to read-only).  

c) If you definitely need read-write access:
There are tools but I believe this is still somewhat hazardous.  You can google about "Linux NTFS access" or ask more about that here if that's what you need.  On the other hand, if your MATLAB partition happened to actually be a DOS or FAT partition, Linux can read-write to it no problem.  (So if you DO need read-write access to it from both Windows and Linux, you could create a new FAT partition somewhere (moving the contents of the other partition to it in the process) and then get at it that way.

d) sudo gedit /etc/fstab
If the suggestions above don't work, you may need to manually adjust the the one-line entry in your /etc/fstab file that the disk manager should have created (or create one).  You can learn about this by going into the terminal and typing "man fstab".  Come back here and somebody will help.


II) Alternatively, assuming you DO have a whole Windows intall on that other disk (with which you want to multiboot):

a) Simple way: reconfigure GRUB:
You can set up the multiboot by editing the file /boot/grub/menu.lst.  Go to the command line and 
type "sudo gedit /boot/grub/menu.lst" (without quotes).  Scrolling down, you'll see where they provide an example of an entry to boot Windows.  You'll need an entry like that one.  It should look something like this:
     title     Windows
     root     (hd1,0)
     makeactive
     chainloader    +1

Put it at the bottom of the file (after AUTOMAGIC stuff). 

The "root" line will depend on your drives.  If it's the "master" drive you unplugged, it will be hd0.  First partition is "0", second "1", and so on.

b) If you actually need to reinstall GRUB: 
follow catlett's wonderful instructions

---

### Post by confused57 on 2006-06-03
You're getting some excellent advice, and if you're wanting to dualboot see if there's anything here that might give you another option:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by madu on 2006-06-03
Thanks a lot fellows..
I think I need to eloborate my situation..

Actually I have two hdds with windows installed in both. My main priority is Matleb and I have installed it in both my drives, in case of emergency.
So I intalled Ubuntu yesterday, when bith my hdds were pluged it..
Then, after the install was ocmpleted, I got ERROR LOADING OS.. when I restarted It went LAODING GRUB... ERROR.
So I figured something wrong with grub and re-installed Ubuntu again, but this time I unplugged one of my hdds to keep the Matlab safe.. because it will be a pain if I lose both because I cant install it again.. license stuff..
SO anyway, secoond time it was ok and I booted into Ubuntu.. But strange thing was, I was seeing all my Windows partions(I mean NTFS partions) on my desktop.. which I found odd because last time I used Ubuntu it was notl ike that.. I had installed a previous version before..
So anyway, today I wated to laod in to Windows and selected it from GRUB. Windows started the bootup screen, and I got a BSOD.. 
I think I made some error when selecting the partions for Ubuntu install..
Anyway, What I want now is to hook up my other hdd so  that I can use MAtlab.. I hope it is not corrupted too..
I unmouted the NTFS drives.. but still didnthelp.. I will try you guys suggestions..
Thanks a million guys..!

Madu

---

### Post by BoneKracker on 2006-06-03
Ubuntu now uses udev and associated magic to basically plug-and play drives and other devices.  On a recent install, I decided to list only the root and swap partitions (and proc) in fstab, and everything worked, including my second hard drive, zip drive, dvd-ram drive, ipod, usb flash drive, and digital camera.

If you're not sure how to proceed, post the contents of the following files with your next message:

     /etc/fstab

     /boot/grub/menu.lst

Also provide the partition listing for the two drives.  E.g., in console, type: 
```
sudo fdisk /dev/hda
p
```
(and for hdb, or whatver the drives are)

Also, do you really need both copies of Windows?

---

### Post by catlett on 2006-06-03
[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

