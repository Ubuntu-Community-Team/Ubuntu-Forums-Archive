---
title: "Black screen w/blinking cursor @ every boot, Ubuntu 7.04"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Getwild2 on 2007-06-27
I just installed Ubuntu 7.04 on a Pentium 4 Dell workstation w/onboard video using the Live CD.  

Installed just fine, however every time it boots, just past the "Grub Loading Stage 1.5, Grub Loading Please Wait, Press ESC to Enter the Menu" prompt it takes me to a black screen with a blinking cursor in the upper left-hand corner.  Then it just sits no matter what I press, all I can do is hit the big red button to restart.

_If I do press ESC I am given the option to boot to the following:_
     Ubuntu, kernel 2.6.20-15-generic
     Ubuntu, kernel 2.6.20-15-generic (recovery mode)
     Ubuntu, memtest86+

I am also able to press 'e' to edit the commands before booting, or 'c' for command-line.

Now this workstation only has one HDD, it is formatted with a 74000MB /ext3 for /, 3000MB /ext3 for /home and 3000MB for swap.  This workstation is going to run solely Ubuntu, no dual booting.

_Out of curiosity I have tried to 'e' edit the 'Ubuntu, kernel 2.6.20-15-generic' command and the following is what I was provided:_
     root (hd0,0)
     kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=e7aca200-c09f-4248-...
     initrd /boot/initrd.img-2.6.20-15-generic
     quiet
     savedefault

I read in one post where someone recommended changing the 'root (hd0,0)' to (hd0,1), (hd0,2), (hd0,3) to see if that works but it did not.  I then tried to change the 'root (hd0,0)' to (hd1,0) but I knew that wouldn't work because I'm only running one HDD.  It was just a shot in the dark.

So at this point I'm not sure what to do.  I can't boot in regular mode or recovery mode, I've tried command line but not sure what to do there, I've tried pressing CTRL+ALT+F1 as I've read, CTRL+ALT+BACKSPACE as I've read to absolutely no avail.  

Does ANYONE have ANY suggestions or recommendations for me?  

Thanks SO MUCH!

---

### Post by DBStevens on 2007-06-27
Could you provide some additional information such as your bios boot settings (order) and what devices you have installed or pluged in especially usb devices that act as storage devices?

Also could you select the memtest option and see if that starts up?

It acts like it isn't seeing the system in the same manner as it did when setup or something has changed.

At least it is able to run grub.

---

### Post by Getwild2 on 2007-06-28
> **DBStevens said:**
> Could you provide some additional information such as your bios boot settings (order) and what devices you have installed or pluged in especially usb devices that act as storage devices?

Also could you select the memtest option and see if that starts up?

It acts like it isn't seeing the system in the same manner as it did when setup or something has changed.

At least it is able to run grub.
_Right now my boot sequence is:_
1. Onboard or USB Floppy Drive (None)
2. Onboard or USB CD-ROM Drive
3. Onboard SATA Hard Drive
4. Onboard PATA Hard Drive (None)
5. Onbaord Network Controller

The only USB devices that are plugged in are the keyboard and mouse, nothing acting as a storage device.  

Memtest produces the same blinking cursor.  

On a side note, when installing this system I simply booted to the LiveCD and performed the aforementioned partition setup.  Windoze being installed would have no bearing on that, right?  The partition setup would have wiped out the partitions and existing OS.  

On my home installation of Ubuntu I created a /boot partition, however I noticed the auto-partitioner did not.  Could this be the issue?  

Thanks for your help!

---

### Post by Getwild2 on 2007-06-28
Are there a series of commands I can enter at the GRUB console by which to check things out to see what's going on?

---

### Post by DBStevens on 2007-06-28
There are several mentions of this issue in launchpad.

From reading the bug reports it looks like a lot of finger pointing between various parts of the system.

Instead of trying root (hd0,1) ,2 or ,3 which increments the partion 

Did you try root (hd1,0) ? which would try the next drive.

Can you also boot using the liveCD and   provide the output of

sudo lshw -C disk

and 

sudo fdisk -l

and

cat /etc/fstab

and

blkid

---

### Post by Getwild2 on 2007-06-28
> **DBStevens said:**
> There are several mentions of this issue in launchpad.

From reading the bug reports it looks like a lot of finger pointing between various parts of the system.

Instead of trying root (hd0,1) ,2 or ,3 which increments the partion 

Did you try root (hd1,0) ? which would try the next drive.

Can you also boot using the liveCD and   provide the output of

sudo lshw -C disk

and 

sudo fdisk -l

and

cat /etc/fstab

and

blkid
I tried (hd1,0), (hd2,0), etc, but get "The selected drive does not exist".  I also tried changing my boot order to HDD=1st but that didn't help.  Below you will find the output of the commands you mentioned separated by color for ease of reading.
[COLOR="Blue"]
_ubuntu@ubuntu:~$ sudo lshw -C disk_
  *-disk                  
       description: SCSI Disk
       product: WDC WD800JD-75MS
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda 
       version: 10.0
       serial: WD-WMAM9RF45689
       size: 74GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: Linux filesystem partition 
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 68GB
          capabilities: primary
     *-volume:1
          description: Linux swap / Solaris partition 
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          capacity: 2863MB
          capabilities: primary nofs
     *-volume:2
          description: Linux filesystem partition 
          physical id: 3
          bus info: scsi@0:0.0.0,3
          logical name: /dev/sda3
          capacity: 2855MB
          capabilities: primary
  *-cdrom
       description: DVD reader
       product: TSSTcorp CD-RW/DVD-ROM TS-H492C 
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: DE02
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd 
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hda[/COLOR][COLOR="SeaGreen"]

_ubuntu@ubuntu:~$ sudo fdisk -l_
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1        8997    72268371   83  Linux
/dev/sda2            8998        9362     2931862+  82  Linux swap / Solaris
/dev/sda3            9363        9726     2923830   83  Linux[/COLOR]
[COLOR="Blue"]
_ubuntu@ubuntu:~$ cat /etc/fstab_
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda2 swap swap defaults 0 0[/COLOR]
[COLOR="SeaGreen"]
_blkid did not produce any output:_
ubuntu@ubuntu:~$ blkid
ubuntu@ubuntu:~$ [/COLOR]

---

### Post by DBStevens on 2007-06-28
Try editing this line:

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=e7aca200-c09f-4248-...  to read

kernel /boot/vmlinuz-2.6.20-15-generic root=/dev/sda1 ro  

This should uncover any additional messages and might actually boot your system.

---

### Post by Getwild2 on 2007-06-28
> **DBStevens said:**
> Try editing this line:

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=e7aca200-c09f-4248-...  to read

kernel /boot/vmlinuz-2.6.20-15-generic root=/dev/sda1 ro  

This should uncover any additional messages and might actually boot your system.
Same thing occurred.  :confused:

---

### Post by DBStevens on 2007-06-28
You haven't been able to use the system since you installed it correct?

If so, I'd try a reinstall,  maybe something happened and you didn't see a message etc....  Maybe the alternate install CD might show more of what happens during the process.   

This back and forth stuff is a very slow way to do things.

---

### Post by Getwild2 on 2007-06-28
You are correct, it has never worked on this workstation.  This is a brand-new out of the box Dell P4 from my supply closet.  

I have thought about the alternate install CD, I am going to give that a try.  I really, really appreciate your help though.  It was not for lack of trying, that's for sure.  

I actually contemplated a different Linux distro as I am using this in an enterprise environment for some proxy and system logging.  I run Ubuntu at home so it is the first place I looked.  I may take a gander at Red Hat or something of the like.  I'm not real experienced at Linux but it will give me something to toy with in a not-so volatile environment.  If I wreck it I can wipe and reload/setup.

Thanks again!! :D

---

### Post by ScutMonkey on 2007-06-28
If you're going to consider a Red Hat distro then take a look at centos.org.  Red Hat makes you pay for downloading these days and makes you pay for support so the centos.org guys took the Red Hat source code and just recompiled it so everyone could use it for free.

---

### Post by DBStevens on 2007-06-28
Red Hat Community aka Fedora

[http://mirrors.fedoraproject.org/publiclist](http://mirrors.fedoraproject.org/publiclist)

---

### Post by Getwild2 on 2007-06-28
Which is more user friendly to the not-so knowledgeable yet will be secure and good for what I need in my enterprise application?  Fedora or Centos?

---

