---
title: "How to add Windows to GRUB?"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by WaterWalker on 2006-06-11
How can I add Windows to the GRUB(I installed Win after Ubuntu so it isn't in the GRUB)? WinXP is on the Second partition of the First Hard Drive(=hd0,1???)
Many thanks

---

### Post by Alienkind on 2006-06-11
If you have just installed both Ubuntu and WIndows and have done little or no important work on it that you saved, I recommend reformatting your hard drive and installing WinXP *first*.

I am also a new user, but from what I know, I believe most, if not all, of the Linux distributions work properly with dual-booting only if Windows is installed first.

In your case, you might not be able to or want to reformat your hard drive. In that case, you will have to wait for another user to help you out.

---

### Post by linuchsan on 2006-06-11
Read the menu.lst. It is all there.

---

### Post by confused57 on 2006-06-11
I haven't seen anybody have success dualbooting installing Windows after Ubuntu(unless Windows is installed on the first partition), but you can try:

```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```

This will open your menu.lst, where you can try adding the Windows entry.

---

### Post by rowanparker on 2006-06-11
> I haven't seen anybody have success dualbooting installing Windows after Ubuntu

I did and had no problems. The only thing I had to do was run grub-install from rescue mode on the installation cd.

Rowan.

---

### Post by confused57 on 2006-06-11
[QUOTE=rowanparker]I did and had no problems. The only thing I had to do was run grub-install from rescue mode on the installation cd.

Rowan.[/QUOTE]

Was Windows installed on a partition after Ubuntu, i.e. Ubuntu partition#1, Windows partition#2?  If you did, that's good info for someone in a similar situation...

---

### Post by chameleonkid on 2006-06-11
How bout installing the new windows beta after ubuntu?

---

### Post by rowanparker on 2006-06-11
> Was Windows installed on a partition after Ubuntu, i.e. Ubuntu partition#1, Windows partition#2? If you did, that's good info for someone in a similar situation...

No, I installed WinXP, then Ubuntu. Then i got rid of XP and put Vista on, then got rid of Vista and put XP back. That all went fine, all i did was re-install grub.

> How bout installing the new windows beta after ubuntu?
Yes, but you need to re-install grub.


Rowan.

---

### Post by hajk on 2006-06-11
Indeed, when you install Windows last, then GRUB must be reinstalled to the MBR.
This requires that you first boot from a liveCD, you can use the Dapper liveCD for this or any other kind, like Knoppix. 

Once booted from the liveCD you must mount the partition that the Ubuntu root directory / is on -- I assume that this is /dev/hda1, but obviously you must use whatever it is in your case. You could use the existing directory /mnt as mount 
point, so "sudo mount -t ext3 /dev/hda1 /mnt". Again, if you don't use ext3, then specify whatever FS you use. If you have a separate partition for /boot, as some people do, then mount it on /mnt/boot (make it first with mkdir).

Now you must prepare for a chroot to the /mnt directory:

sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc /mnt/proc
sudo cp /proc/mounts /mnt/etc/mtab

followed by 

sudo chroot /mnt  /bin/bash

after which you are in the chrooted environment.

You can now edit the /boot/grub/menu.lst file to add the lines for Windows XP, they're already there as an example, so just add them (uncommented) to the end of the file. After that all you need to do is 

sudo /sbin/grub-install /dev/hda

(or use /dev/sda if you have a SATA disk). This will have restored GRUB to the 
MBR of your first harddisk.  

That's all, you can shut down now, remove the liveCD, and reboot.

---

