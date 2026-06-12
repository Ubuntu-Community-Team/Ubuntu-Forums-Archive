---
title: "Dual Boot"
date: 2019-11-14
forum: Apple Hardware Users
---

### Post by ozfrog on 2019-11-14
Hi,
returning to Ubuntu after some years of absence.
Running a MBPro Retina 512G SSD under 10.14.6
I installed Ubuntu onto a 32G USB stick.
It loads fine when selected on the dual boot page in MacOS and all functions look operational, but,
Any modifications to software (Eg Setting up mail a/c in Thunderbird) or downloads are non persistent (saved).
On the next boot-up, it's like the first time.

I've obviously missed something somewhere during the installation (?)

cheers

Ozfrog

---

### Post by crip720 on 2019-11-14
Sounds from what you say, is that you downloaded the ISO and burned/installed it to USB stick.  This will only give you the 'live' and 'installer' version.  You need to install ubuntu from this to another drive, hard drive, USB stick or SD card.   Can also set up USB stick with persistence if you don't want a full install.

---

### Post by crip720 on 2019-11-14
This is a link for adding persistence.  [https://askubuntu.com/questions/1051543/how-to-make-a-live-ubuntu-18-04-usb-with-a-persistent-storage-of-more-than-4gb](https://askubuntu.com/questions/1051543/how-to-make-a-live-ubuntu-18-04-usb-with-a-persistent-storage-of-more-than-4gb)

---

### Post by ozfrog on 2019-11-16
> **crip720 said:**
> Sounds from what you say, is that you downloaded the ISO and burned/installed it to USB stick.  This will only give you the 'live' and 'installer' version.  You need to install ubuntu from this to another drive, hard drive, USB stick or SD card.   Can also set up USB stick with persistence if you don't want a full install.

Hi and thanks for the reply,

AFAIK - I need the USB non-persistent version in order to be able to install the "persistent" version on the HDD.

I've been trying to use hdiutil convert, to change the .ISO to an .IMG but keep running up against some "folder or file not found" - think I'll abandon this avenue of attack, my eyes are melting!

So, if I've understood this correctly. From the USB "live" version, I should be able to install a persistent version on the external HDD.
Getting the USB stick "persistent" looks a hard ask for this neophyte :)

Thanks fro your info and patience.

Ozfrog.

Here's the hdiutil stuff I was looking at;

[LIST=1]
[*]Download the desired file
[*]Open the Terminal (in /Applications/Utilities/ or query Terminal in Spotlight)
[*]Convert the .iso file to .img using the convert option of hdiutil:
hdiutil convert -format UDRW -o /path/to/target.img /path/to/source.iso
**Note:** OS X tends to put the .dmg ending on the output file automatically. Rename the file by typing:
mv /path/to/target.img.dmg /path/to/target.img
[*]Run diskutil list to get the current list of devices
[*]Insert your flash media
[*]Run diskutil list again and determine the device node assigned to your flash media (e.g. /dev/disk2)
[*]Run diskutil unmountDisk /dev/diskN (replace *N*with the disk number from the last command - in the previous example, *N* would be *2*)
[*]Execute sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img or ./ubuntu.dmg).
**Note:** Using /dev/rdisk instead of /dev/disk may be faster.
**Note:** If you see the error dd: Invalid number '1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.
**Note:** If you see the error dd: /dev/diskN: Resource busy, make sure the disk is not in use. Start the 'Disk Utility.app' and unmount (don't eject) the drive.
[*]Run diskutil eject /dev/diskN and remove your flash media when the command completes
[/LIST]
**Now the USB stick is ready.**[COLOR=#5B5B5B][FONT=&quot] Boot the device that you want from the USB stick.[/FONT][/COLOR]

---

### Post by Impavidus on 2019-11-18
You can have a full install of Ubuntu on either an internal or an external hard drive. Full installs are always persistent.

A live disk can be either persistent or non-persistent. A persistent live disk is has some more possibilities than a non-persistent live disk, but is far from a full install. A non-persistent live disk is more reliable than a persistent live disk. Your post suggest that you only created a non-persistent live disk.

To make a full install of Ubuntu, you need the installer from the live disk, so you first create a live disk. You can use dd to clone the .iso file directly to the usb drive; no need to convert it to something else first. That will give you a non-persistent live disk and is known as a very reliable method. The problem is that a single wrong character in the dd command may wipe your hard drive. There are some tools to make it safer. See for example [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

When you boot your computer from the live disk, it offers you to try Ubuntu before installing or install it right away (and some other options). When you try Ubuntu before installing (a live session), you'll find a launcher for the installer on the desktop.

---

### Post by ozfrog on 2019-11-24
> **Impavidus said:**
> You can have a full install of Ubuntu on either an internal or an external hard drive. Full installs are always persistent.

A live disk can be either persistent or non-persistent. A persistent live disk is has some more possibilities than a non-persistent live disk, but is far from a full install. A non-persistent live disk is more reliable than a persistent live disk. Your post suggest that you only created a non-persistent live disk.

To make a full install of Ubuntu, you need the installer from the live disk, so you first create a live disk. You can use dd to clone the .iso file directly to the usb drive; no need to convert it to something else first. That will give you a non-persistent live disk and is known as a very reliable method. The problem is that a single wrong character in the dd command may wipe your hard drive. There are some tools to make it safer. See for example [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) there.

When you boot your computer from the live disk, it offers you to try Ubuntu before installing or install it right away (and some other options). When you try Ubuntu before installing (a live session), you'll find a launcher for the installer on the desktop.

Hello and thanks for your reply.
I understand all of the above and have been persisting with THIS method.
[https://florisvanbreugel.wordpress.com/2018/03/23/installing-ubuntu-on-an-external-ssd-drive-on-a-macbook/](https://florisvanbreugel.wordpress.com/2018/03/23/installing-ubuntu-on-an-external-ssd-drive-on-a-macbook/)
**This procedure needs a copy of the newly created boot.efi to somewhere MacOS can get access.**
(Also a USB hub - Live version, new version + external HDD - all connected with USB )
I am using Mountain Lion on the external HDD for the final "blessing" as OSX Mojave no longer gives access to the terminal in Recovery mode :(
I'm stuck on this after 3/4 attempts.
From within the Terminal on Live Ubuntu - the Mac partitions are unaccessible (because HFS+?) so I can't copy it with "cp" to there.
The procedure suggests emailing it to yourself :)
1. Thunderbird can't get my .gmail.com account to run.
2. Mailspring says the file's too big.
3. Hiri says 'No you can't attach an .EFI file because it might be a virus"
Tried to make and format a FAT partition on ther external HDD - that's visible but read only. Tried chmod a+rwx on it, but still can't copy the boot.efi to it - the read-only status persists. 
I have tried mkusb.There were dependency issues, and obsolete packages :) 
Today, Sunday 24th November, I'm going to rest my eyes, but hope you can come up with something for future experimentation.
cheers

Ozfrog.

---

### Post by ajgreeny on 2019-11-24
*Thread moved to **Apple Hardware Users**.* which is more appropriate and a better fit.

You may have received better replies quicker had you mentioned earlier that you were using Apple hardware and posted here in the first place.

---

### Post by ozfrog on 2019-11-24
> **ajgreeny said:**
> *Thread moved to **Apple Hardware Users**.* which is more appropriate and a better fit.

You may have received better replies quicker had you mentioned earlier that you were using Apple hardware and posted here in the first place.

You obviously skimmed over my initial post :)
References to MacBook Pro and MacOS therein.
But message received loud and clear. I shall post further gripes in the appropriate subsection

---

### Post by ozfrog on 2019-11-25
[COLOR=#000000]Hello and thanks for your reply.[/COLOR]
[COLOR=#000000]I understand all of the above and have been persisting with THIS method.[/COLOR]
[https://florisvanbreugel.wordpress.c...-on-a-macbook/]("https://florisvanbreugel.wordpress.com/2018/03/23/installing-ubuntu-on-an-external-ssd-drive-on-a-macbook/")
This procedure needs a copy of the newly created boot.efi to somewhere MacOS can get access.
(Also a USB hub - Live version, new version + external HDD - all connected with USB )
I am using Mountain Lion on the external HDD for the final "blessing" as OSX Mojave no longer gives access to the terminal in Recovery mode :sad:
I'm stuck on this after 3/4 attempts.
From within the Terminal on Live Ubuntu - the Mac partitions are unaccessible (because HFS+?) so I can't copy it with "cp" to there.
The procedure suggests emailing it to yourself :smile:
1. Thunderbird can't get my .gmail.com account to run.
2. Mailspring says the file's too big.
3. Hiri says 'No you can't attach an .EFI file because it might be a virus"
Tried to make and format a FAT partition on ther external HDD - that's visible but read only. Tried chmod a+rwx on it, but still can't copy the boot.efi to it - the read-only status persists. 
I have tried mkusb.There were dependency issues, and obsolete packages :smile: 
Today, Sunday 24th November, I'm going to rest my eyes, but hope you can come up with something for future experimentation.
cheers

Ozfrog.

---

