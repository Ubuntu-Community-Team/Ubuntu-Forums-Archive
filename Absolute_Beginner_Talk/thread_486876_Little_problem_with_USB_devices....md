---
title: "Little problem with USB devices..."
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-06-28
[B]When I use my USB pen it appears on the desktop as a drive but not as a 'USB drive', there is no option to 'eject' the device and a warning appears when I pull it out. 

It used to work fine until I followed these instructions to remove hda1 from my desktop (it's a dual boot): [/B]


> You need to mount your hda1 in another place than /media. Everything that is mounted in /media will have an icon on the desktop, which indeed I agree with you is fine for USB sticks, removable devices, etc., but not for a windows partition on a fixed drive. I have a desktop with a Win98 partition (to play tuxracer! Won't work under Ubuntu!) and I moved the mount point to /mnt (which in fact is the "traditional" mount point for external drives)

There are two steps involved: 1) change the mount point in /etc/fstab and 2) create the mount point in your file system (this is in fact just an empty directory).

1) gksudo gedit /etc/fstab
Look for the line of your hda1. In the second entry, change /media to /mnt. Thus, your mount point is going to change from /media/hda1 to /mnt/hda1

2) make a directory hda1 under /mnt. You can do so with a nautilus instance with root rights, but here is how you do it with the command line:

sudo mkdir /mnt/hda1

Upon restarting, the hda1 will be accessible from /mnt/hda1, and won't show up on the desktop anymore. If you are impatient, you can have the changes become in effect right away:

sudo mount -a


**How can I fix it without getting hda1 back on my desktop?**

---

### Post by Inxsible on 2007-06-28
What do you mean appears like a drive but not USB drive?
 
If not eject, is there a Unmount Volume option ?

---

### Post by lamalex on 2007-06-28
what is the mount point of your usb drive? rather than eject does it say unmount when you right click it?

---

### Post by aberadam on 2007-06-28
Yeah, there's an unmount option.  Is that the same thing?

---

### Post by aberadam on 2007-06-28
On the desktop it appears as 'disk-1'.

---

### Post by Inxsible on 2007-06-28
> **aberadam said:**
> Yeah, there's an unmount option. Is that the same thing?
Yes, its the same as Eject !

---

### Post by RanulfWolfSage on 2007-06-28
Yes it does, in Linux any device that acts as a storage medium is 'mounted' just like a regular hard drive would be, including CD's from my minimal experience on some distro's. Just choose the unmount volume option on the desktop icon for your usb drive, and it will safely remove it. Hope that helps! :)

---

### Post by aberadam on 2007-06-28
Ahh, ok, thanks.  Yeah that works.  Be nice if it said 'eject' and had the little USB symbol on the icon like it's supposed to though... 

I'm a pedant! :)

---

