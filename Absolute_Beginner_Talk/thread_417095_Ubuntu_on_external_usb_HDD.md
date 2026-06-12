---
title: "Ubuntu on external usb HDD"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by yeleek on 2007-04-21
Hi,

I'm trying to install 7.04 onto a dedicated external usb disk.  I booted off the live cd and installed ubuntu to the external hdd.  If i reboot with the livecd in the drive and then select boot from first hard disk off the menu it works.  If i reboot without the cd in the drive, i get grub error 18.  Problem is as its a usb external hard disk I don't believe its possible to set the disk mode for a usb drive.  Its a 40gb disk, and I've 2gb of ram.  The disk is only for ubtuntu.

I don't know enough either about Ubuntu to set the partition types/sizes myself.  So please can a ubuntu guru tell me how i should partition the disk during the setup process so it will boot without needing the cd?  And without giving me error 18? 

[I]Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel it self does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot.
[/I]

Thanks

---

### Post by billdotson on 2007-04-21
I have no idea what your problem is at all honestly.  Although I was successful in installing and being able to boot and use Ubuntu Edgy on my external HDD.  The first thing you should do is check to see if your motherboard can boot from USB devices.  

Also, did the installer give you a choice as where to install GRUB to??  The way I have it setup is I have GRUB on my external drive so if I don't have it plugged in it boots to Windows (no GRUB menu), but when I plug it in and tell the BIOS to boot from it it goes straight to GRUB, doesn't bring up a menu and boots directly to Ubuntu.  I installed GRUB to my internal Windows drive once and and I am just guessing but if the external drive id not plugged in GRUB will get very confused and not want to load.  GRUB reads the menu.lst file that is normally located in /boot/grub/menu.lst in the Ubuntu filesystem.  If GRUB cannot see this to know what it can boot it can get very confused.

I saw something about it saying it didn't like large IDE drives or something like that.. maybe in the BIOS you could change the emulation to HDD?

I have never encountered that error, but good luck.

Remember google is your best friend.  Just google up Grub error 18 and if you do not find anything reply to me here or either are [email]sgtmattbaker@jabber.org[/email] (which is my Jabber IM nick) or wookieeassassin (my AIM nick)  

About partitioning though, you want a ext2 or ext2 most likely for your Ubuntu partition.  2GB minimum.  If you are gonig to have over I think ~10GB you should use ext3.  Then you need another partition of at the very least 256MiB.  This is called the swap and is similar to the pagefile in Windows as far as I know.  When your computer is running low on RAM it can use that space for some RAM (not going to be as fast though).  Then you can partition the rest according to whatever you want i terms of storage or media space.

Again, good luck.

---

### Post by yeleek on 2007-04-21
Thank you for your reply :)

Just found something on a pc pro forum which said for Linux they recommended

Ext3 /boot 100mb (to make sure its in first 1024 cylinders or something)
Swap Swap 2gb (same as ram)
Remainder ext3 / (for me would be approx 37gb)

Not clear though on how i'd tell ubuntu i'd like grub etc on the /boot and the rest of install on /

What you describe of grub being on the external hdd is exactly what i'm after.  Can you advise at all re the above (if you agree) and how you tell the install to do part on /boot and the rest on /

External usb booting is working as I have bartpe (windows pe) booting from a usb key drive.

Thanks again for replying

B

---

### Post by yeleek on 2007-04-21
That flopped :(

Created the partitions in this order 

ext3  /boot   100mb
swap swap 2gb
ext3 / 36gb

Setup went through fine, but pc won't boot at all from external usb.  Had more luck when i went with the automated install.

Struggle to believe this is something that others wouldn't want to do, i.e. install ubuntu on completely external usb drive.

Anyone have any suggestions?

Thanks

---

### Post by emaxware on 2007-04-24
A couple of things to check on:

- While installing, when shown the "partition summary" screen, there is an "Advanced" button which allows you to designate where to install the GRUB MBR, which defaults to the system's first hard drive.  In your case you'll want to change that to your USB drive.  n

- Secondly, the default initrd may not contain all the modules a system needs to boot from an external usb device.  When I installed to my external USB drive, I needed to add a couple of modules and update my initrd file.  To do this, I added 

yenta_socket
rsrc_nonstatic

to the bottom of /etc/initramfs-tools/modules and ran

sudo update-initramfs -u 

Of course to do this, since I couldn't boot directly into the system after installation, I booted under another system (live CD should work also) and chrooted into the USB system.

Well, don't know if this solves all your problems, but may point you in the right direction.

sudo grub-install [usb partition] 

in case in wasn't done during installation.

---

