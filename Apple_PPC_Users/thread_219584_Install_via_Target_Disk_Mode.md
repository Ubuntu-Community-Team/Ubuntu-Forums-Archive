---
title: "Install via Target Disk Mode?"
date: 2006-07-20
forum: Apple PPC Users
---

### Post by Taiden on 2006-07-20
I have two computers.

My ibook, 600 MHz, 128MB ram, 20GB hd.  Broken CD drive.
My mothers ibook, same specs, working CD drive.

I put my ibook in target disk mode, booted up the CD on my mothers ibook, and installed onto my ibooks drive. All went well until it came to the bootloader, which it failed to install. This was with a Xubuntu (Dapper Drake) alternate install CD.

Can any of you think of a way for me to get this to work? :-k

---

### Post by Taiden on 2006-07-20
I am going to bump this.

All i need is some way to install a bootloader. Maybe there is a way to make OpenFirmware boot from linux? Any ideas are welcome..

Xubuntu is installed... I just can't boot from it!!

---

### Post by Taiden on 2006-07-20
Okay, here is some food for thought.

While on my MOTHERS ibook with MY ibook in target disk mode, when the yaboot installer fails, it gives me this message.


-----------------------------------------------------------
No boot loader has been installed, either because you chose
not to or because your specific architecture doesn't support
a boot loader yet.

You will need to boot manually with the /boot/vmlinux kernel
on partition /dev/sda3 and root=/dev/sda3 passeed as a kernel
argument.
-----------------------------------------------------------


I bet changing sda3 to hda3 and figuring out how to boot onto hda3 with MY ibook would make it work. I just dont know how to...

Maybe OpenFirmware?

---

### Post by Taiden on 2006-07-21
I figure i might as well document my progress here just in case someone wants to jump in with some ideas, also I need a spot to put my notes, since I am formatting and reformatting drives left and right.


Current partition setup (all done through target disk mode with an alternate install cd (Xubuntu Dapper Drake).



-------------------------------------------------------------------------

#1---32.3 kB------------------------------------Apple			
#2---5.0 MB--------------unallocated
#3---19.5 GB-------f----ext3 ---------------untitled--------/
#4---498.8 mb-----F---swap---------------swap-----------swap

-------------------------------------------------------------------------



partition #2 will be changed to HFS+ and have yaboot installed on it via target disk mode and my mothers ibook. i heard that you can install yaboot onto an HFS+ partition, which would be best for me since that is the most compatible with OS X, which is the OS I will be using to set up the whole booting process (that and open firmware if possible)

---

### Post by pindar on 2006-07-21
Seeing that you're not getting many replies, I jump in, but beware: I'm no expert. My thoughts: as long as you're booted into Mac # 1 and try to install a bootloader to Mac # 2 mounted as Target Disk, this will fail because yaboot either can't figure out the open firmware (of for short) path to the hard disk of # 2 or will give an incorrect path. What you could try:

1. boot off of CD with your iBook in target disk mode.

2. chroot into the target disk:
find out what /dev nodes point to the target disk. Let's say this is /dev/sda. then do:
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda3 /mnt/ubuntu
sudo mount -t proc none /mnt/ubuntu/proc
sudo mount -o bind /dev /mnt/ubuntu/dev
sudo chroot /mnt/ubuntu /bin/bash

3. Now head into /etc, write a yaboot.config:
```
boot=/dev/hda2
device=hd:
partition=3
ofboot=hd:2
root=/dev/hda3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
enableofboot

image=/boot/vmlinux
      label=Linux
      root=/dev/hda3
      initrd=/boot/initrd.img
      partition=3
      read-only
```

After writing this file to /etc, run 
mkofboot -v

Alternatively, you could also try lilo, which I find a bit easier to use, though you'd need to install it first (in your chrooted environment, of course), it's not part of the livecd, AFAIK.

4. When you've run mkofboot successfully, exit chroot, unmount all the mounted partitions etc. and try to restart your iBook. 

Good luck!

---

