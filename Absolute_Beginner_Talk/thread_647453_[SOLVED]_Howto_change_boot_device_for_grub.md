---
title: "[SOLVED] Howto change boot device for grub?"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by shareMenaPeace on 2007-12-22
Hi,
im dual booting VISTA and GUTSY, somehow i screwed the boot with Vista System Panel ... i not even changed a setting there.

Rightnow the notebook cannot even boot into GRUB, no error message appears.

When i 
```

sudo fsck.reiserfs /dev/sda6
```  (ubuntu live cd)

I get 
Partition /dev/sda6 is mounted with write permissions, cannot chek it 

Do i need gparted live cd? [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
Or can i unmount the mounted partition with the live cd session?

Basicly i think i can fix my boot problem with changeing the boot device (partition), 
```

sudo fdisk -l 
```gives me 
/dev/sda2  as BOOT, but i need /dev/sda6 - right?

Thanks for help :)

---

### Post by Duck2006 on 2007-12-22
What is the full output of

fdisk -l

and the output of

cat /boot/grub/menu.lst

That should tell you as to what you have to change.
If i remenber write you can do it all from the live CD as you boot it up. It should not mount on boot(may be wrong).

---

### Post by shareMenaPeace on 2007-12-22
Thanks, well i just run SUPER GRUB DISC :) And i think this fixed it ... 

The output was like 

sda1 windows
sda2 swap
sad3 ubuntu

and the BOOT was either win nor ubuntu ...



[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

btw isnt cat giving me the boot of the live cd?

---

### Post by Duck2006 on 2007-12-22
> btw isnt cat giving me the boot of the live cd?

No it will give you the menu,lst of the hard drive that it finds on your system that has a /boot/grub/menu.lst file or for what ever file i want to display. 
Super grub fixes a lot of things with boot stuff it is a great disk to have.

---

### Post by shareMenaPeace on 2007-12-22
its is 

hd0 = sda

---

### Post by Duck2006 on 2007-12-22
> **shareMenaPeace said:**
> its is 

hd0 = sda

hd = ide or pata
sd = sata or scsi

But a lot of disro's these day just call them all sd.

---

### Post by shareMenaPeace on 2007-12-22
moment i post teh exact output ...

---

### Post by shareMenaPeace on 2007-12-22
Ahhh OK, 
what 

cat /boot/grub/menu.lst does is showing me my grub boot options.
These are fine, as SUPER GRUB DISC fixed my boot device ...it was sda2 .... now its back to ubuntu partition (sda6)...

My device.map what i was refering to is
(hd0) /dev/sda

The output of cat /boot/grub/menu.lst is like

Ubuntu ...kernel xxxx
ubuntu kernel .... 

Other OS

windows

If you want the exact output let me know, im just on my desktop computer so i need to manually transfer the content of menu.lst ... BECAUSE somehow all is fine in my network ...just browser connection in ubuntu isnt working yet - what i fix next

Cheers

---

### Post by shareMenaPeace on 2007-12-22
Btw fdisk -l  still shows /dev/sda2 as BOOT, but all is fine now ....strange and i thought it now shows sda6 as boot .... sda2 is HPFS/NTFS

---

