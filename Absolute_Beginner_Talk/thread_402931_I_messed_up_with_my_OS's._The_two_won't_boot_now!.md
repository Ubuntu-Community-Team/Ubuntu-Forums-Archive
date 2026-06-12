---
title: "I messed up with my OS's. The two won't boot now!"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-06
Please read this in detail...

I had four partitions. I had three OS's and the last partition is the swap partition. The first partition had Kubuntu (hda1), the second had OpenSuSE, and the third had Windows XP (hda3).

OpenSuSE was the last one I installed so my boot loader was OpenSuSE's GRUB at that time.

I deleted OpenSuSE's partition and there, I moved my Kubuntu's /home. Unfortunately, the partition was too small for my  Kubuntu's /home so the moving of files ended.

I decided to just install a fresh copy of Ubuntu where I moved my Kubuntu's /home. During installation, I selected my Kubuntu partition as the mount point of /home so I expected to access my Kubuntu's /home in my new Ubuntu.

When I rebooted, I was unable to boot from my hard disk. There was an error message. I tried to insert the Ubuntu Edgy Eft Live CD before booting, and from the live CD's first menu, I selected the option of booting from the first hard disk. That way, I was able to boot from my first hard disk and saw in the GRUB menu my fresh Ubuntu and my old Windows XP. Kubuntu was not in the menu. 

I booted the fresh Ubuntu install, and to my surprise, OpenSuSE's old settings were there! My OpenSuSE's desktop icons were there, my OpenSuSE's firefox session was left there as well as the bookmarks, and "hda3," my Windows XP partition was mounted which was mounted also by my OpenSuSE install. Also, I was not able to access my Kubuntu's old /home. How can that happen!?

I edited my GRUB menu.lst and added my old Kubuntu as an option. I rebooted; still I needed the Ubuntu Live CD to boot from my hard disk. After booting from the hard disk, I chose my old Kubuntu from the GRUB menu. There were weird error messages. I'm sorry but I don't remember what they exactly were, but if I'm not mistaken, they were about a missing partition. After the error messages, Kubuntu still booted. After I logged in, there was an error message saying that "kstartup" or something was missing, and of course, I wasn't able to use Kubuntu.

I restarted and tried my old Windows XP. After booting XP, I was stuck the blue Windows XP screen and it did not even proceed to the welcome screen. So, I also cannot use my old XP.

How do I fix this??????????????

**Edit**

Updates:

I can now boot from hard disk. I don't know how it happened but when I just booted a while ago it worked.

I tried my Kubuntu again. Apparently, the filesystem check failed. It was looking for a missing partition or the partition was not ext2. I do not understand that error message quite well so I don't know what to do with it. Also, it said that "superblock" was corrupted or something.

I think I did not state it clearly before but what I meant by the blue XP screen is the screen right after the Windows XP loading screen (with the loading bar below the Windows XP logo), which is also right before the welcome screen. It was stuck before the welcome screen even appeared.

---

### Post by cypherzero on 2007-04-06
It appears that you do indeed have a big mess on your hands.

You need to format the partitions before you install anything to them, do not just hope the new install will 'overwrite' anything that's already there.

Using your Live CD you can do this and then reinstall Ubuntu.
It shouldn't make a difference but you might want to reformat your Swap partition anyway, just to be extra-safe.

I don't know what the blue Windows XP screen is, but I'll assume NTLDR is loading okay, so you could try booting XP into safe mode. If that fails you might even have to reinstall XP, or at least try the XP recovery console (boot your XP disk).

If grub is messed up you can easily reinstall that alone from the Live CD, hopefully it should detect XP, if it doesn't detect XP this is suggestive of a corrupted disk and/or partition table.

---

### Post by dstew on 2007-04-06
You cannot access your Kubuntu /home directory because when you gave that partition the mountpoint /home, all your directory names changed to reflect that. So, your Kubuntu root directory is now /home, your Kubuntu boot directory is /home/boot etc. Your old Kubuntu home directory is now /home/home. See if that is true.

Similar problems may now be confusing your grub setup. If you setup grub when you installed Ubunutu, it may not be pointing to the correct partitions.

---

### Post by wersdaluv on 2007-04-06
> **cypherzero said:**
> If grub is messed up you can easily reinstall that alone from the Live CD, hopefully it should detect XP, if it doesn't detect XP this is suggestive of a corrupted disk and/or partition table.

If it is a corrupted disk, what does that exactly mean?

I think I saw something about partition table in the error message. What do I do to fix the partition table?

---

### Post by wersdaluv on 2007-04-06
> **dstew said:**
> You cannot access your Kubuntu /home directory because when you gave that partition the mountpoint /home, all your directory names changed to reflect that. So, your Kubuntu root directory is now /home, your Kubuntu boot directory is /home/boot etc. Your old Kubuntu home directory is now /home/home. See if that is true.

Similar problems may now be confusing your grub setup. If you setup grub when you installed Ubunutu, it may not be pointing to the correct partitions.

I just mounted my Kubuntu(hda1) partition and found out that my Kubuntu /home partition is still there. Apparently, it isn't the /home that my new Ubuntu install is using. Why is it that way even if I set hda1 as a mount point for /home? Oh well... What's done is done. 

Now, I want to mount /home there and I will delete my Kubuntu OS there making hda1 solely a /home partition. How do I do that?

---

### Post by wersdaluv on 2007-04-06
I edited the first post for updates.

---

