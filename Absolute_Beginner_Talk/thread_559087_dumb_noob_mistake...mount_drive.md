---
title: "dumb noob mistake...mount drive"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-09-24
Hello....
So....

I went into the properties for this usb device that for some reasen always launches rhythmbox and the icon on the desktop is an iPod...It thinks its an iPod...which is annoying... Anyway, I thought I could fix this by changing the mount options....So I changed the mount options under "Volume" (i think) to /media/floppy0

So now obviously it will not mount. How can I change this??? I get this message when I insert the drive:
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-gnome-mount.png[/IMG]

Somebody please help...


sv

---

### Post by ddrichardson on 2007-09-24
Mount it manually then go back in and change the option you added.```
sudo mount -t vfat /dev/sda1 /media/usbdisk
```Obviously you will need to set sda1 to  your device and usbdisk to its moount point in /media.

---

### Post by staticvoid on 2007-09-25
Hi,
**I have a partitioned hardrive and I did not delete the rescue partition, so "sda1" shows up on my desketop as a sony rescue partiotion, does that matter??** I do'nt want to break anything else. Is the code you gave me to mount it manually? I'll run the code and see what happens...
SV

EDIT: I tried what you said and it gave me this:

nathan@freddy:~$ sudo mount -t vfat /dev/sda1 /media/usbdisk
Password:
mount: mount point /media/usbdisk does not exist
nathan@freddy:~$ 

So... Was I supposed to manually mount it some how? if so; how?

---

### Post by alienexplorers on 2007-09-25
You need to create a directory for the drive to mount on in /media.
You need to:
> sudo mkdir /media/usbdisk

---

### Post by staticvoid on 2007-09-25
Hi,
Thanks alienexplorers, I tried what you said, but now with the other code it says:

nathan@freddy:~$ sudo mount -t vfat /dev/sda1 /media/usbdisk
mount: /dev/sda1 already mounted or /media/usbdisk busy

So... I think it is conflicting with my sda1 recovery harddrive what should I use instead 
ddrichardson?

Back to the origianal error message:

I changed the devices mount point to "/media/floppy0" and my error message says I cannot of " / " characters. Windows recognizes it. If I format the device will that change anything??

[B]EDIT:

Yey :D It worked...go... windows? ha, I just formatted it to FAT32 and then renamed the volume. Now it's back to recognizing it as an iPod and launching rhythmbox everytime I pop it in :P[/B]

---

### Post by mesilliac on 2007-09-25
You might be able to see the USB disk under "Computer" in the file browser. You could probably just right-click it and change the properties again.

After you get it to mount again, the right way to get it to not start up rhythmbox automatically is to go to System > Preferences > Removable Drives and Media in the main gnome menu, and change the preference in the "multimedia" tab :).

EDIT: By the way, the error was because automount always puts removable drives under /media. Just put "floppy0" in stead of "/media/floppy0"

---

### Post by mcduck on 2007-09-25
> **staticvoid said:**
> Hi,
Thanks alienexplorers, I tried what you said, but now with the other code it says:

nathan@freddy:~$ sudo mount -t vfat /dev/sda1 /media/usbdisk
mount: /dev/sda1 already mounted or /media/usbdisk busy

So... I think it is conflicting with my sda1 recovery harddrive what should I use instead 
ddrichardson?

Back to the origianal error message:

I changed the devices mount point to "/media/floppy0" and my error message says I cannot of " / " characters. Windows recognizes it. If I format the device will that change anything??

It's impossible for us to tell what device your disk is as we couldn't possibly know what disks you have and how they are connected.

But try running 'sudo fdisk -l' to list all your partitions. That should help you to figure out the correct device.

Also there seems to be something wrong with the way you configured the mounting. I'm not sure what the 'Volume' option in the GUI does (as I always handle these things from CLI), but based on the error message I'd suppose it doesn't ask you for full path where to mount the drive but just the name to use instead. So don't use the '/media/'-part  when doing that.

---

### Post by staticvoid on 2007-09-25
woohoo :D thanks mesilliac. Now it doesn't launch rhythmbox! I'll try just putting floppy0. Will that make the icon different??

sv

---

### Post by staticvoid on 2007-09-25
> **staticvoid said:**
> ... went into the properties for this usb device

I believe I said at the start, mcduck, that I was trying to mount a usb device...Anyway, no worries it's mounted now. but theres an ipod icon over it :P haha...funny computers....

sv

---

### Post by mcduck on 2007-09-25
> **staticvoid said:**
> I believe I said at the start, mcduck, that I was trying to mount a usb device...Anyway, no worries it's mounted now. but theres an ipod icon over it :P haha...funny computers....

sv
I know you said that. But USB drives use the same device names as SATA and SCSI drives do, and get their number in the order they are recognized by the system. So if you have no SATA/SCSI drives and you plug in USB drive it becomes /dev/sda, if you have one SATA drive that will be /dev/sda and your USB drive becomes /dev/sdb and so on. So just telling us that it's USB drive doesn't tell us what the device name for it would be.

To make things even more complicated at least Feisty started using SATA/SCSI driver for PATA drives as well, so in older Ubuntu versions they are mounted as /dev/hda, /dev/hdb and so on while in Feisty they use the same /dev/sdX naming as SATA/SCSI and removable drives do..

---

### Post by staticvoid on 2007-09-25
Aaahhh... Ok :X. Hahaha, I get it. So my sda1 and sda2 are labeled like that because they are partitions of the same drive? and not sda and sdb. I think I follow you. thanks for the explanation :)

SV

---

