---
title: "How to delete partitions?"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by deiniol on 2006-03-26
Currently I have my box set up to dual boot both Windows XP and Ubuntu. However, the last time I actually used Windows was around 3 months ago, and I want to delete the partition it's on and use all the space for Ubuntu. Is this possible without having to reinstall Ubuntu? If so, how do I go about doing so?

---

### Post by piedamaro on 2006-03-26
boot a live cd equipped with parted (or gparted), then delete the windows partition and grow the ubuntu partition. Do it only if you know what you're doing.

---

### Post by Sef on 2006-03-26
> the last time I actually used Windows was around 3 months ago, and I want to delete the partition it's on

Using the Live CD, u can use gparted to delete XP.  However, you have to change the boot, since it resides on the partition you want to delete.  And you can change the formatting of the file to ext3 or reisfers or other.

> and use all the space for Ubuntu

Not sure how to set it up to be used by Ubuntu.

---

### Post by deiniol on 2006-03-26
[QUOTE=piedamaro]boot a live cd equipped with parted (or gparted), then delete the windows partition and grow the ubuntu partition. Do it only if you know what you're doing.[/QUOTE]

Unfortunately I don't, that's why I'm posting this in absolute beginners!

---

### Post by deiniol on 2006-03-26
[QUOTE=Sef]Using the Live CD, u can use gparted to delete XP.  However, you have to change the boot, since it resides on the partition you want to delete.  And you can change the formatting of the file to ext3 or reisfers or other.[/QUOTE]

How do I change the boot?

---

### Post by piedamaro on 2006-03-27
> you have to change the boot, since it resides on the partition you want to delete.
Wrong, the 1st stage of the bootloader resides in the first 446 bites of the MBR wich contains the partition table too.
Unless you installed grub on the first sector of the windows partition, very unusual, you don't need to do anything.

Now, supposed you have a common configuration, your 1st partition is the windows one, and then you have the linux partion (ext3 I suppose). Ext3 can be growed but not moved iirc, so you should delete your windows partition, make a full backup of your linux partition, (cp -a is your friend), then recreate an ext3 partition which fills the whole disc, and then copy your files back.
You need to change your boot loader config file too (/boot/grub/menu.lst), to point at what becomes your 1st partition. (now it should point to your 2nd partition).
Hope this helps, if not post your partition table and your grub config file before anything else. ;)

---

### Post by meborc on 2006-03-27
if it was my machine, i would just do a new install of dapper and format the whole drive... BUT that is just my thoughts... probably you have usea all that 3 months to make breezy just the way you like it and therefore don't go through whole installation process again...

and dapper is still not stabel yet... ;)

---

### Post by deiniol on 2006-03-27
[QUOTE=piedamaro]Wrong, the 1st stage of the bootloader resides in the first 446 bites of the MBR wich contains the partition table too.
Unless you installed grub on the first sector of the windows partition, very unusual, you don't need to do anything.

Now, supposed you have a common configuration, your 1st partition is the windows one, and then you have the linux partion (ext3 I suppose). Ext3 can be growed but not moved iirc, so you should delete your windows partition, make a full backup of your linux partition, (cp -a is your friend), then recreate an ext3 partition which fills the whole disc, and then copy your files back.
You need to change your boot loader config file too (/boot/grub/menu.lst), to point at what becomes your 1st partition. (now it should point to your 2nd partition).
Hope this helps, if not post your partition table and your grub config file before anything else. ;)[/QUOTE]

Thanks! :D I've got it set up the way you describe- ext3 is the Windows partition and ext3 the Linux one. Would it work if I delete the windows partition, copy the Linux one into the now-unassigned space at the beginning of the drive and then delete the original Linux partition and then grow the new Linux partition to fill up the rest of the drive (excluding the swap space)? This is from looking at gparted.

---

### Post by deiniol on 2006-04-02
Well, I tried the above, and as far as I can see, it worked. However, the downside is that I can no longer boot into Ubuntu- when I try grub gives me "Error 22". I've tried pretty much everything I can think of. I've edited menu.lst and changed instances of /hda3 to /hda1 and updated the partition location thing from hda(0,2) to hda(0,1). I've changed fstab to reflect the new partition structure. But I now have absolutely no idea what to do. I'm still getting "Error 22" and am completely lost. ](*,)  Please help!

---

