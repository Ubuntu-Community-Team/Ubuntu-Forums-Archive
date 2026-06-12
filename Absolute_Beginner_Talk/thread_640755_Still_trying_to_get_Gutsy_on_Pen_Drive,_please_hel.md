---
title: "Still trying to get Gutsy on Pen Drive, please help"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-12-14
I've tried twice to install gutsy on my 4GB flash drive but not got very far.

Today I tried again, and was doing well until I hit the 'w' command, then something went wrong.  I'm hoping that someone with more knowledge than me might be able to suggest what I should do next.

Thanks.


1.Open a terminal window and type sudo su
2.Type fdisk -l to list available drives/partitions. Note which device is your flash drive (example: /dev/sda) Throughout this tutorial, replace x with your flash drive letter. For example, if your flash drive is sdb, replace x with b. 
3.Type umount /dev/sdx1
4.Type fdisk /dev/sdx 
type p to show the existing partition and d to delete it
type p again to show any remaining partitions (if partitions exist, repeat the previous step) 
type n to make a new partition
type p for primary partition
type 1 to make this the first partition
hit enter to use the default 1st cylinder 
type +750M to set the partition size
type a to make this partition active
type 1 to select partition 1
type t to change the partition filesystem 
type 6 to select the fat16 file system
type n to make another new partition
type p for primary partition
type 2 to make this the second partition 
hit enter to use the default cylinder
hit enter again to use the default last cylinder
type w to write the new partition table

............................
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. 
The new table will be used at the next reboot.

WARNING: If you have created or modified any DOS 6.x
partitions, please see the fdisk manual page for additional
information.
Syncing disks.
root@ubuntu :/home/ubuntu#

---

### Post by DezSP on 2007-12-15
Is the disk mounted? Try typing sudo umount /dev/sdx1 first.

---

### Post by L Campbell on 2007-12-15
> **DezSP said:**
> Is the disk mounted? Try typing sudo umount /dev/sdx1 first.


Thanks.

I guess you noticed that this is instruction #3 on my list.

Should I then assume that you mean to do this before even doing #1 ?

Kind regards.

---

### Post by DezSP on 2007-12-15
Whoops, indeed it is on there. Ubuntu can be funny with flash drives though, it tends to hotplug them when the partitions change, which can cause problems. Try separating the deletion and creation -- do fdisk, d, w, then the rest afterwards. If it complains after the deletion, unplug the flash drive and plug it back in again.

---

### Post by dcstar on 2007-12-15
> **L Campbell said:**
> I've tried twice to install gutsy on my 4GB flash drive but not got very far.
.........

Installing and using a full O/S on any flash drive can hasten the death of these devices because they (still) have a finite quantity of write cycles.

You can create a version of the Ubuntu Live CD that stores changes and uses system RAM to minimise writes to the drive:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

You can boot off this (just like the live CD) but it will keep changes you make.

---

### Post by kelvin spratt on 2007-12-15
This is how I do it I use GParted Live CD and partition my flash drive the first partition to 850mb fat16 then partition the rest to ext2 Make the 1st partition bootable by clicking the bootable flag, thats the first bit. Then load the gutsy live CD this is most important you must use the live CD. Insert your flash drive, Then follow the instructions from this link from No8. from website No1 on my guide
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
I have used this method many times with no problems. I personally use a 4gb pendrive for what its worth with no problems at all
[LIST=1]
[*]Type **umount /dev/sd[COLOR=#ff0000]x[/COLOR]1** to ensure the 1st partition is unmounted
[*]Type **mkfs.vfat -F 16 -n ubuntu710 /dev/sd[COLOR=#ff0000]x[/COLOR]1** to format the first partition
[*]Type **umount /dev/sd[COLOR=#ff0000]x[/COLOR]2** just to ensure the 2nd partition is unmounted
[*]Type **mkfs.ext2 -b 4096 -L casper-rw /dev/sd[COLOR=#ff0000]x[/COLOR]2 **to format the second partition
[*]Remove and Re-insert your flash drive
[*]Back at the terminal, type **apt-get update**
[*]Type [B]apt-get install syslinux mtools
[/B]
[*]Type **syslinux -sf /dev/sd[COLOR=#ff0000]x[/COLOR]1**
[*]Type **cd /cdrom**
[*]Type **cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz ****casper/initrd.gz ****/media/ubuntu710/**[INDENT]Ignore any **"cannot create symbolic link" **errors
[/INDENT]
[*]Type **cd /home/ubuntu**
[*]Type **wget pendrivelinux.com/downloads/U710fix.zip**
[*]Type **unzip -o -d /media/ubuntu710/ U710fix.zip**
[*]Restart your computer, set your BIOS or Boot menu to boot from the USB device and reboot again.[/LIST]You should now have a USB Ubuntu 7.10 Gutsy Gibbon flash drive that should automatically save your changes, restoring them on boot.
 **Note:** If your having trouble getting Ubuntu to boot, your memory stick may have a corrupted MBR. To repair the MBR of your USB device, at the terminal type **sudo apt-get install lilo** then type **lilo -M /dev/sd[COLOR=#ff0000]x[/COLOR]** (replacing **[COLOR=#ff0000]x[/COLOR]** with the letter of your flash device)

---

### Post by L Campbell on 2007-12-15
> **kelvin spratt said:**
> This is how I do it I use GParted Live CD and partition my flash drive the first partition to 850mb fat16 then partition the rest to ext2 Make the 1st partition bootable by clicking the bootable flag, thats the first bit. Then load the gutsy live CD this is most important you must use the live CD. Insert your flash drive, "
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
I have used this method many times with no problems. I personally use a 4gb pendrive for what its worth with no problems at all
[LIST=1]
[*]Type **umount /dev/sd[COLOR=#ff0000]x[/COLOR]1** to ensure the 1st partition is unmounted
[*]Type **mkfs.vfat -F 16 -n ubuntu710 /dev/sd[COLOR=#ff0000]x[/COLOR]1** to format the first partition
[*]Type **umount /dev/sd[COLOR=#ff0000]x[/COLOR]2** just to ensure the 2nd partition is unmounted
[*]Type **mkfs.ext2 -b 4096 -L casper-rw /dev/sd[COLOR=#ff0000]x[/COLOR]2 **to format the second partition
[*]Remove and Re-insert your flash drive
[*]Back at the terminal, type **apt-get update**
[*]Type [B]apt-get install syslinux mtools
[/B]
[*]Type **syslinux -sf /dev/sd[COLOR=#ff0000]x[/COLOR]1**
[*]Type **cd /cdrom**
[*]Type **cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz ****casper/initrd.gz ****/media/ubuntu710/**[INDENT]Ignore any **"cannot create symbolic link" **errors
[/INDENT]
[*]Type **cd /home/ubuntu**
[*]Type **wget pendrivelinux.com/downloads/U710fix.zip**
[*]Type **unzip -o -d /media/ubuntu710/ U710fix.zip**
[*]Restart your computer, set your BIOS or Boot menu to boot from the USB device and reboot again.[/LIST]You should now have a USB Ubuntu 7.10 Gutsy Gibbon flash drive that should automatically save your changes, restoring them on boot.
 **Note:** If your having trouble getting Ubuntu to boot, your memory stick may have a corrupted MBR. To repair the MBR of your USB device, at the terminal type **sudo apt-get install lilo** then type **lilo -M /dev/sd[COLOR=#ff0000]x[/COLOR]** (replacing **[COLOR=#ff0000]x[/COLOR]** with the letter of your flash device)

Thanks, this looks very helpful.

If I might ask you to clarify a couple of points:-
 "use GParted Live CD"  Does this mean use the Live CD to partition, then remove it and reboot to do the rest of the procedure?

"Then follow the instructions from this link from No8. from website No1 on my guide"  I got confused here, too.  (sorry to be so dense)  :-)

Kind regards.

---

### Post by L Campbell on 2007-12-18
> **L Campbell said:**
> Thanks, this looks very helpful.

If I might ask you to clarify a couple of points:-
 "use GParted Live CD"  Does this mean use the Live CD to partition, then remove it and reboot to do the rest of the procedure?

"Then follow the instructions from this link from No8. from website No1 on my guide"  I got confused here, too.  (sorry to be so dense)  :-)

Kind regards.

I have run the procedure you show here through my mind several times and I feel like I can follow it now.

After making a Gparted Live CD I tried to partition 2 different 4GB pen drives to your specs here and it all seemed to work well except that, on both drives, the largest #1 partition it would allow me to make was 722MB so, when I tried this command (mkfs.vfat -F 16 -n ubuntu710 /dev/sdx1) I got a message something to the effect that I didn't have enough room.

Once more I am confused.    :-)

---

### Post by bumanie on 2007-12-18
I have not tried this with a full sized distro., but I have certainly manged to get some of the smaller linux distros to boot from usb devices via the instructions on this link [http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/](http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/)
It is worth a try. I tried all the other methods people are suggesting and I could not get any of them to work very. This method worked first time (at least on the smaller distros).
It is not ultra fast due to the emulation, but it does work. 
Hope this works for you.

---

### Post by L Campbell on 2007-12-22
> **L Campbell said:**
> I have run the procedure you show here through my mind several times and I feel like I can follow it now.

After making a Gparted Live CD I tried to partition 2 different 4GB pen drives to your specs here and it all seemed to work well except that, on both drives, the largest #1 partition it would allow me to make was 722MB so, when I tried this command (mkfs.vfat -F 16 -n ubuntu710 /dev/sdx1) I got a message something to the effect that I didn't have enough room.

Once more I am confused.    :-)

Here I am again, still struggling with this installation.

I believe that I have got the issue of partitioning my 4GB Pen Drive ( with the Gparted Live CD ) resolved, however, when I follow the instructions ( see [http://tinyurl.com/2xnnp8](http://tinyurl.com/2xnnp8) ) I find everything seems to go smoothly till I reach #17 ( Type cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz casper/initrd.gz /media/ubuntu710/ )

Whatever is supposed to happen here, doesn't happen.  Progress just ceases, instead of taking me back to root@ubuntu:/home/ubuntu#

I would appreciate any suggestions.

---

### Post by bumanie on 2007-12-22
> **L Campbell said:**
> Here I am again, still struggling with this installation.

I believe that I have got the issue of partitioning my 4GB Pen Drive ( with the Gparted Live CD ) resolved, however, when I follow the instructions ( see [http://tinyurl.com/2xnnp8](http://tinyurl.com/2xnnp8) ) I find everything seems to go smoothly till I reach #17 ( Type cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz casper/initrd.gz /media/ubuntu710/ )

Whatever is supposed to happen here, doesn't happen.  Progress just ceases, instead of taking me back to root@ubuntu:/home/ubuntu#

I would appreciate any suggestions.

Have you tried the instructions I posted above?
I have got a usb pendrive and a usb external hard drive booting puppy linux via that method. I tried all the instructions you seem to be following and got nowhere. The method I used does not need g-parted or lots of command lines. It was very easy. I suggest you give it a try, I assume it will work with ubuntu 7.10. as one of the downloads, claims it will boot any linux distro.

---

### Post by L Campbell on 2007-12-22
> **bumanie said:**
> Have you tried the instructions I posted above?
I have got a usb pendrive and a usb external hard drive booting puppy linux via that method. I tried all the instructions you seem to be following and got nowhere. The method I used does not need g-parted or lots of command lines. It was very easy. I suggest you give it a try, I assume it will work with ubuntu 7.10. as one of the downloads, claims it will boot any linux distro.

Hi, thank you for your continued interest.

I have to admit that I didn't try your suggestion (yet) because it involved using my Win computer but I will give it a try.

With so few instructions it does appear as if it should go well.

One thing that you might be able to answer for me:-   do I need to format, or partition, my 4GB Pen Drive in any way before beginning this?

Kind regards.

---

### Post by bumanie on 2007-12-22
I underatnd the reluctance to use windows, however, when I followed the instructions it did work well. I hope it does for you too. I did not need to partition either drives (the usb pendrive was new) and as far as I remember the usb hdd had already been formatted to ntfs (for reasons other than trying linux in emulation).
I suggest you format the pendrive under windows and see how it goes. The advantage of this system is that you can boot it on top of windows and switch between the two OS's as you wish. If I remember correctly I did boot it on top of feisty at one stage just to see if it worked - it did.
I did this many months ago and both drives still boot perfectly well (I actually forgot it had to be done under windows, thanks for the reminder!). 
You must remember that your linux distro needs to be an iso file. 
Hope this helps. I really did find this method easy and the only one that worked in any manner.

---

### Post by L Campbell on 2007-12-22
> **bumanie said:**
> I underatnd the reluctance to use windows, however, when I followed the instructions it did work well. I hope it does for you too. I did not need to partition either drives (the usb pendrive was new) and as far as I remember the usb hdd had already been formatted to ntfs (for reasons other than trying linux in emulation).
I suggest you format the pendrive under windows and see how it goes. The advantage of this system is that you can boot it on top of windows and switch between the two OS's as you wish. If I remember correctly I did boot it on top of feisty at one stage just to see if it worked - it did.
I did this many months ago and both drives still boot perfectly well (I actually forgot it had to be done under windows, thanks for the reminder!). 
You must remember that your linux distro needs to be an iso file. 
Hope this helps. I really did find this method easy and the only one that worked in any manner.

Well, I tried it 3 times but each time things just got jammed up and I had to 'reset'.

The first 4 instructions seemed to work well.  When I reached #5, I never saw a place to, ' add persistent to the boot options ' and it went down hill fast after that.

Maybe my computer has a problem?

Kind regards.

---

