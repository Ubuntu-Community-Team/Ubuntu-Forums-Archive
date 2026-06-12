---
title: "Booting Ubuntu from second mac drive"
date: 2006-08-27
forum: Apple PPC Users
---

### Post by micben@earthlink.net on 2006-08-27
I have installed Ubuntu to a second internal Mac hard drive in my G5 tower.  After the installation, Ubuntu did not reboot into the hard drive filesystem and returned to MacOS X on my primary drive.  How do I make the startup process recgonize Ubuntu on second drive as an option.  Pressing L causes MacOS X to look for the system, but it skips past and boots in MacOS X.  I attempted the fix suggested by an earlier post to edit yaboot.conf, but cannot find any such file in Ubuntu file system. 

Any suggestions much appreciated.

---

### Post by xurios on 2006-08-27
For any changes in yaboot.conf to take effect, you have to be booted into linux and then you have to run ybin (which I assume is not possible, since you can't boot into linux). Also, assuming you let the ubuntu intaller do what it wanted with the paritioning scheme during install, then you should have a viable partition from which you can boot ubuntu and editing yaboot.conf will only muck things up. Since you can't find yaboot.conf on your ubuntu file system (it should be at /etc/yaboot.conf), I would suspect that something went wrong during the install.

---

### Post by micben@earthlink.net on 2006-08-27
I apologize for not having read the Mac support threads before entering my question.  I worked out the process to update yaboot.conf to support haveing Ubuntu on second internal drive.  For the sake of anyone else loading Ubuntu on second internal Mac drive here is the process.

Preparing second internal drive - Make sure you have about 10 gig of continous free space.  The only thing you might do on MacOS side is backup any existing data, and used Disk utility to make a smaller Mac Drive for any data you want to restore for your Mac OS later.  Leave about 10 gig of 'Free Space' at that time.  This is not really necessary, as you should be able to shrink any existing HFS+ partitions with the Ubuntu partition utility when you boot the Ubuntu CD, and not harm your existing data

1. Download and burn PPC ISO file to CD as per instructions.

2. Boot Mac from the CD.

3. Run the installer and select the second internal drive as your destination.  Select 'using largest continous free space' and then allow the install to run to completion.

4. Do not restart, stay in 'Live CD' mode.

5. Bring up a terminal window.  Enter 
 
sudo parted /dev/sdb print

sdb is the device id of the second internal drive
sda would be the first internal drive (home of your macos, presumably)

The first column identifies the partition number and the last column is the type of partition.  You want to identify the Boot, Linus-swap, and Root partitions.  In my case they were;

  2  boot
  4  root
  5  swap

Enter

sudo parted /dev/sda print

Confirm the partition number of main drive MacOSX home partition. In my case it was 9

6. In the terminal window, enter:

sudo mount /dev/sdb4 /mnt

to mount the hard drive root directory

7. To edit yaboot.conf in the root partition of sdb:

sudo pico /mnt/etc/yaboot.conf

edit yaboot.conf to match:

boot=/dev/sdb2               
device=sd1:
partition=4
ofboot=sd1:2
root=/dev/sdb4
timeout=100
install=usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
enableofboot
macosx=/dev/sda9

image=/boot/vmlinux
   label=Linux
   root=/dev/sdb4
   initrd=/boot/initrd.img
   partition=4
   read-only

8. Exit and save

9. To copy to correct location:

sudo cp /mnt/etc/yaboot.conf /etc/yaboot.conf

10. Reinstall yaboot:

sudo ybin -v

Restart and hold down 'Option' key.  Select Linux penguin Drive.  Select L

I was in Ubuntu from my second drive.  I had original files on a seperate partition.  I was gold.

Please correct if you see errors here.

Mike







4.

---

