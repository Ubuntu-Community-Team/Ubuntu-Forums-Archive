---
title: "External USB HDD"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by mugwump99 on 2007-10-27
As a newcomer to any form of Linux I recently installed 7.10 as a dual-boot with Windows XP. I have had for some time a Iomega 500Gb external disk connected via USB, which works fine under Windows.

When I boot into Ubuntu, this disk usually doesn't appear as a drive, but there have been two occasions where it did pop up on the desktop, and on those occasions it was fully accessible. Iomega don't provide any Linux support or drivers etc, but as a USB device I would have thought it wouldn't need any, like my USB key, camera card reader etc. don't.

The fact that the drive has been recognised twice seems to indicate that Ubuntu is willing to communicate with this disk, but how do I get it to do so consistently? Are there any settings I can configure to increase the chances of my disk being picked up, or is there a way of bringing it online post-boot?

Thanks in advance for any help you can give,

Martin.

---

### Post by p_quarles on 2007-10-27
I believe you can automate this by adding a line to /etc/fstab for the disk. That said, I don't use an external drive, so I don't know whether you're supposed to for those or not. 

There is a relatively simple way of doing this manually, though, and I've done the same thing when I've had trouble with USB flash drives. First, open the terminal and type this:
```
sudo lshw
```
This will spit out a list of all your hardware. Look for the external drive's entry. As an example, this is the entry for one of my flash drives:
```
     *-scsi:1
          physical id: 2
          bus info: usb@5:8
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: DataTraveler 2.0
             vendor: Kingston
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdf
             version: 1.00
             size: 1940MB
             capabilities: removable
             configuration: ansiversion=2
           *-disc
                physical id: 0
                logical name: /dev/sdf
                size: 1940MB
                capabilities: partitioned partitioned:dos
              *-volume
                   description: FAT16 partition
                   physical id: 1
                   logical name: /dev/sdf1
                   capacity: 1939MB
                   capabilities: primary
```
The important part here is the logical name, so make a note of that. The next step is to create a mount directory for it:
```
sudo mkdir /media/*drive-name*
```
The *drive-name* part can be whatever you want. My disk listed above mounts under /media/BACKUP. To manually mount it, I would type the following:
```
sudo mount /dev/sdf1 /media/BACKUP
```
Just change the logical name and the mount directory to the one's based on your information, and voila. You can now access this in your file manager. 

If you don't want to have to type out that long command every time, you can also make an "alias" that will shorten it. For instance, if I wanted to do that by just typing "mbackup" instead of the whole thing, I would hit alt-F2, type in 
```
gksudo gedit .bashrc
```
and add the following to that file:
```
alias mbackup='sudo mount /dev/sdf1 /media/BACKUP'
```
Hopefully someone else can give you better advice that's specific to external disk drives, but that's a good workaround in the meantime.

---

### Post by mugwump99 on 2007-10-29
Thanks for your help - The disk appeared on the list, but gives an error when I try to mount it..

     *-scsi
          physical id: 2
          bus info: usb@3:2
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 0A
             vendor: ST350083
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdc
             version: 3.AA
             size: 465GB
             capabilities: partitioned partitioned:dos
           *-volume
                description: HPFS/NTFS partition
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdc1
                capacity: 465GB
                capabilities: primary bootable
martin@martin-desktop:~$ sudo mount /dev/sdc1 /media/iomega
fuse: failed to access mountpoint /media/iomega: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdc1 (IOMEGA_HDD)

---

### Post by Rinzwind on 2007-10-29
```
martin@martin-desktop:~$ sudo mount /dev/sdc1 /media/iomega
fuse: failed to access mountpoint /media/iomega: No such file or directory

```

Is there a iomega/ inside /media? 
If not create the directory and try again.


Btw I usually do a rightclick on the disc-icon on the desktop, goto properties and on the farmost right tab there's an arrow with underneath it:

mountpoint
filesystem
parameters

Insert iomga at 'mountpoint' and leave the rest alone. 

That normally works perfect for me. No need to add it into fstab.
This way your disc will mount with an icon onto your desktop.

To me(!) /etc/fstab should be used for fixed discs and not discs you can unmount (like usb discs).

---

### Post by mugwump99 on 2007-10-29
Thanks. With /media/iomega pre-created, I can successfully run sudo mount /dev/sdc1 /media/iomega and get the drive online. Neither option for bringing it online at startup automatically works though.

---

### Post by mjwebber on 2007-10-31
I have similar problems as mugwump99, though with a maxtor drive.  
first i could see the drive but not access files or write to it.  so then, following another advice, i logged on through the recovery mode.  that got me access.
Second, but i still could not write.  so then i followed yet more advice and installed ntfs. 
Third, i cannot even see the drive now.  so i followed the advice above, but get:
~$ sudo mkdir /media/maxtor
~$ sudo mount /dev/sdb1 media/maxtor
mount: mount point media/maxtor does not exist.
please can i have some advice?  ta - m

---

