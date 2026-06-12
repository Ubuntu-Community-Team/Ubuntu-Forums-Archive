---
title: "[SOLVED] Reinstalling Ubuntu?"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by keshava on 2008-02-20
I`v f@*#ed up my computer pretty bad, so the display aspect is broken & I can only run it in command or off the installation CD(I`m doing that now). I was wondering what would happen if I just hit install in the CD. Would i loose everything in my home folder?

---

### Post by Presto123 on 2008-02-20
How about doing this before you go that far (in the command prompt) and hit Ctrl+Alt+Backspace:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by bodhi.zazen on 2008-02-20
> **keshava said:**
> I`v f@*#ed up my computer pretty bad, so the display aspect is broken & I can only run it in command or off the installation CD(I`m doing that now). I was wondering what would happen if I just hit install in the CD. Would i loose everything in my home folder?

Yes you would, unless you have /home on a separate partition.

You can fix the problem form the live CD.

Mount your ubuntu partition at /media/ubuntu

Now chroot and fix X

```
sudo chroot /media/ubuntu /bin/bash
sudo dpkg-reconfigure -phigh xserver-xorg
```

Now reboot and all should be well again.

If not we need a better description of what you did to break your system.

---

### Post by amyst on 2008-02-21
How is that /home folder on a separate partition wouldn't be deleted? If I reinstall ubuntu from the cd, would I be asked to create another /home folder?

---

### Post by bodhi.zazen on 2008-02-21
It is very cool ...

Say you have a partition , /dev/sda1 for root ( / ) and a second, sda2, for /home

Now re-install

during the install, select manual partitioning. Set /dev/sda1 as root, reformat

Set /dev/sda2 as /home DO NOT FORMAT

This will re-install and preserver your data in /home

---

### Post by johnn1949 on 2008-02-21
If /home  is on a separerate partition it wouldn't be affected by a reinstall if you choose manual install and specify the original ubuntu partition and swap partition to be reinstalled . This  does not affect any other partition on the drive.  

It's like putting your "my documents" on drive d: in windows so you can reinstall windows on drive c: without affecting your "my documents" on d:.

---

### Post by keshava on 2008-02-21
it says there is no /media/ubuntu... what now?

---

### Post by keshava on 2008-02-21
some body please help

---

### Post by Brendan Hart on 2008-02-21
sudo dpkg-reconfigure -phigh xserver-xorg

will this work for configuring my gfx card?

---

### Post by forestpixie on 2008-02-21
you might not have /media/ubuntu - in fact you probably haven't - you need to find where you're install is - it'll probably be sdax - where x is a number

open aterminal and do 

sudo fdisk -l

ther will be a list of all your partitions - chnage 'ubuntu' to the partition you have installed to

---

### Post by jan quark on 2008-02-21
are you now in the live cd session?

if it is not there we have to manually create a mount point

but run these terminal commands first 

```
sudo fdisk -l
```
```

cat /etc/fstab
```

---

### Post by keshava on 2008-02-21
i dont think i fully under stand.
what dos this do/meen

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 119.8 GB, 119834104320 bytes
255 heads, 63 sectors/track, 14569 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca3eca3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14195   114021306   83  Linux
/dev/sda2           14196       14569     3004155    5  Extended
/dev/sda5           14196       14569     3004123+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

---

### Post by jan quark on 2008-02-21
```
You can fix the problem form the live CD.

Mount your ubuntu partition at /media/ubuntu

Now chroot and fix X


[CODE]
sudo chroot /media/ubuntu /bin/bash
sudo dpkg-reconfigure -phigh xserver-xorg
```

Now reboot and all should be well again.[/CODE]

we are trying to do what bodhi.zazen suggested.


first point boot with your ubuntu cd into the live session

second point mount the ubuntu partition at media/ubuntu

you said
> it says there is no /media/ubuntu... what now?
so we must create the mount point manually and mount the partition by hand
the output you just posted tells us what partitions are recognized by the system, how are their names, what format type they have, essential info for mounting

so now create the mount point with
```

sudo mkdir /media/ubuntu
```

and check if it is really there with 

```
ls /media
```
```
ls /mnt
```

---

### Post by keshava on 2008-02-21
i see now

---

### Post by keshava on 2008-02-21
there is a /media/ubuntu now

---

### Post by keshava on 2008-02-21
oh no it says there no /bin/bash now

---

### Post by bodhi.zazen on 2008-02-21
I apologize my instructions were a little too terse.

Next step is to mount your ubuntu root partition. fdisk -l lists your partitions adn we can see your ubuntu partition is /dev/sda1

```
sudo mount /dev/sda1 /media/ubuntu
```

The proceed with the chroot command and reconfigure X

Then reboot and let us know how it goes.

Note : Mounting prepares the partition for use.

---

### Post by keshava on 2008-02-21
ok i did the reconfigure X and after it says

grep: /proc/cmdline: No such file or directory
pcilib: Cannot open /proc/bus/pci
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080221004427

---

### Post by keshava on 2008-02-21
do i use the backup file & if so how?

---

### Post by bodhi.zazen on 2008-02-21
No, go ahead and reboot

(the backup is your old xorg.conf)

---

### Post by keshava on 2008-02-21
ok hope it works

---

### Post by keshava on 2008-02-21
it worked XD thank you thank you all!!!!!

---

### Post by jan quark on 2008-02-21
good to hear
:)

please mark this thread as solved
thank you

and a happy linux usage

---

### Post by bodhi.zazen on 2008-02-21
> **keshava said:**
> it worked XD thank you thank you all!!!!!

Just a FYI: You could have just run that command ```
dpkg-reconfigure -phigh xserver-xorg
``` from recovery mode (you do not need sudo from recovery mode). The only reason I used chroot is you had already booted the live CD and I though it would have been faster.

---

