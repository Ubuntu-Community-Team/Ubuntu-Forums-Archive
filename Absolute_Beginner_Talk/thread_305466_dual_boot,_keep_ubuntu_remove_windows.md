---
title: "dual boot, keep ubuntu remove windows"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by Dainn on 2006-11-23
Hello-  I installed Ubuntu 6.06 with a dual boot for Windows 98.  I would like to remove Windows.  I have searched the help on my desktop, in  forum(s), links provided within posts on the forums, and linux google.  Now, *blushing* this either has a very obvious answer that I am not getting (which is entirely possible), or I am not searching correctly.  I keep finding where people want to remove ubuntu and keep windows. I like ubuntu, I think I'll be keeping it, thank you very much.
 
	I would like to know the best way to keep the ubuntu I already have (updates etc), and get rid of windows.  I have seen many suggestions of using gparted for removing ubuntu, would I just apply it towards removing the windows partition, or is there a better way? 

	As far as I know, I do not need or want to save anything from the windows partition.
	
	On a side note, is it possible to just change the format for that partition in disk manager to ext3?  If not, why?

	If either of these questions has been answered before, please accept my apologies and if possible provide a link, I am more than willing to read up and try to figure this out.  I'm just a little leary of doing this wrong and having to start over again if it can be avoided.

	I noticed that this was asked for in another post, if any other information is required, please let me know.  Any help would be appreciated, and Thank you for your time, Dainn.


tyler@Tear:~$ sudo fdisk -l
Password:

Disk /dev/hda: 8700 MB, 8700346368 bytes
255 heads, 63 sectors/track, 1057 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         535     4297356    c  W95 FAT32 (LBA)
/dev/hda2             536        1035     4016250   83  Linux
/dev/hda3            1036        1057      176715    5  Extended
/dev/hda5            1036        1057      176683+  82  Linux swap / Solaris
tyler@Tear:~$

---

### Post by Bachstelze on 2006-11-23
Just use GParted to delete your windows partition and delete the Windows entry from /boot/grub/menu.lst to remove it from the GRUB menu. Then you can create another partition instead - or just format it to another FS, GParted will do that for you.

---

### Post by Dainn on 2006-11-23
Thank you for the quick reply!  I would not have "picked up" on removing windows from the GRUB menu.  Which is why I asked, I had a feeling I was missing something.  I need to download the gparted and then I will attempt this and post how it worked. Thanks again.

---

### Post by Bachstelze on 2006-11-23
Well, you can very well leave your GRUB alone if you wish. Only when you'll select the "Windows" entry and press Enter, you'll have a nice error :)

---

### Post by bodycoach2 on 2006-11-23
I would suggest a clean Ubuntu install. Save your important files to another drive, or an online storage service (like xdrive.com or mediamax.com - there both free). Once you're 'saved' -yes, a play on religion there- reinstall Ubuntu. 

> **HymnToLife said:**
> Just use GParted to delete your windows partition and delete the Windows entry from /boot/grub/menu.lst to remove it from the GRUB menu. Then you can create another partition instead - or just format it to another FS, GParted will do that for you.

---

### Post by Bachstelze on 2006-11-23
It seems a little too much to me. Why bother with a reinstall when the system is working fine ?

---

### Post by steve.horsley on 2006-11-23
I agree. A reinstall would be a complete waste of time.

Another file that may need fixing though is /etc/fstab, if the windows partition was being mounted. You can just delete or comment out the reference to that partition.

---

### Post by Dainn on 2006-11-23
ok, it's done.  *happy dance*  I have been able to get rid of hda1 and increase the size of hda2 (grow).  That part was suprisingly easy:).  I rebooted and my ubuntu worked as expected *more happy dance*.

The only problem I ran into was when I went to edit the /boot/grub/menu.lst.  I had copied and pasted the sudo nano command and it kept telling me that nano was not recognized, so I tried gedit instead.  That appeared to work (but was kind of confusing at first), so I placed # infront of the window lines and saved it.  I'm going under the belief that this should have worked to take the window option off of the startup options.  I didn't get a chance to reboot becuase my 16 year old was standing over my shoulder at that point "mom...mom...".  -after rebooting, this worked.

Thanks for the advice HymnToLife.

Bodycoach2 - I was already in the process of using the first suggestion when you posted.  But thank you for replying.

mmm... any clues as to why nano didn't work?

should I put resolved in the subject line of the thread?

---

### Post by Dainn on 2006-11-23
steve.horsley  - would the problem you mentioned be readily apparent?  Or do I need to do more "checking" on it?  Thanks

---

### Post by steve.horsley on 2006-11-24
The /etc/fstab problem could have two symptoms:

1) If fstab is configured to perform a filesystem check on a non-existent on un-checkable partition, it can throw up an ugly warning and offer to reboot or go into single user mode. Fortunately, this isn't happening.

2) If fstab is configured to automount a partition and it can't, it can leave an error in the log saying it couldn't mount the partition. This might be happening.

3) if fstab is configured not to automount, you might still get an icon in Places or Computer, and an error when you try to mount it by hand.

---

### Post by Dainn on 2006-11-24
After looking through the log and checking in Places and Computer, this does not appear to be a problem.

Thanks :-)

---

