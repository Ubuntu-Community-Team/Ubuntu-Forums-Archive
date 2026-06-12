---
title: "What should I format a filesystem for Windows and Ubuntu use?"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by crazybrit4967 on 2006-12-22
I tried FAT32, but I think that has some sort of limit on individual filesize - meaning I can't rip all of my DVDs onto it. (I'm not sure about this, so if anyone could confirm/refute this that would be nice as well).  What's the best filesystem that Ubuntu and Windows XP can read and write to?

---

### Post by msak007 on 2006-12-22
FAT32 has a 4 GB file limit. However it's one of 3 choices you have if you want to share files between Ubuntu and Windows:

1. FAT32 as you have already done. This comes with the limitation already mentioned (4 GB file size), but is probably the best and most reliable method.

2. Format the partition as ext3 (native Ubuntu filesystem format). Windows can't see this filesystem natively, but you can use a tool such as [Ext IFS]("http://www.fs-driver.org/"). It lets you assign driver letters to ext2 / ext3 filesystems in Windows and use them as you would any other drive. This is the method I use and it works reliably.

3. (NOT RECOMMENDED) Format the partition as NTFS. This is the Windows 2000 / Windows XP native filesystem. Ubuntu / Linux can read NTFS just fine, but write capability is still very experimental. There are some projects out there to allow Linux to write to NTFS partitions and some may argue that it's very stable, but I wouldn't trust my data on this method.

Hope this helps.

---

### Post by crazybrit4967 on 2006-12-22
Well, I already tried using NTFS and NTFS-3G, but Amarok wouldn't build my music library properly when it was stored on my NTFS partition.  I also tried ext3, but it made my computer crash every time I opened My Computer.  I guess I'll try it again and hope I'll be more lucky this time, if those are really the only three options.

---

### Post by msak007 on 2006-12-22
Yea as I said NTFS write is not very stable and I wouldn't trust it. Unfortunately those really are the only 3 options, so try the ext3 method again using Ext2 IFS. There should be a Control Panel module for setting drive letters, once you set them I think you have to reboot and then can use the drives.

---

### Post by crazybrit4967 on 2006-12-22
That's lame.  Thanks anyway, though.

---

### Post by msak007 on 2006-12-22
> **crazybrit4967 said:**
> That's lame.  Thanks anyway, though.
What's lame?

---

### Post by crazybrit4967 on 2006-12-22
The 4GB limit.

---

### Post by msak007 on 2006-12-22
Yea that's an MS thing. I found that out the hard way once, it drove me nuts trying to copy an ISO to a FAT32 partition and getting errors @ 4 GB. I was initially set on creating a FAT32 shared partition for files & shared data when I was making the switch to Linux. Once I found out about the limitation and the workarounds, I reformatted all my drives using ext3. I don't boot much into Windows anyway, so the Ext2 IFS tool works well when I need it. It's transparent and you really won't notice the difference once you've set the drive letters.

---

### Post by crazybrit4967 on 2006-12-23
The only thing is, I'd have to back everything up that I already put in there, reformat, put everything back on, and rebuild my iTunes, and Amarok libraries, along with about 11 other things it would probably screw up along the way.  Which would be a major pain.  Do you happen to know anything about whether Ext2 IFS works well with iTunes or not?

---

### Post by msak007 on 2006-12-23
> **crazybrit4967 said:**
> The only thing is, I'd have to back everything up that I already put in there, reformat, put everything back on, and rebuild my iTunes, and Amarok libraries, along with about 11 other things it would probably screw up along the way.  Which would be a major pain.  Do you happen to know anything about whether Ext2 IFS works well with iTunes or not?
That's one of the things I ran into, but I did have 2 hard drives and had enough room on both that I was able to copy the data back & forth while I was reformatting so that helped. It was a pain doing all that. Unfortunately I can't answer your iTunes question as I've never used iTunes.

---

### Post by crazybrit4967 on 2006-12-23
Okay, I reformatted the partition to ext3 but now I can't mount it.  What should the line look like in /etc/fstab?

---

### Post by crazybrit4967 on 2006-12-23
Can anyone help me out here?

---

### Post by DirtDawg on 2006-12-23
Is it possible to create more than on 4GB Fat32 partition on the same drive? So 3 partitions would be a grand total of 12GB?

To be clear, I'm assuming Windows only recognizes 4GB of Fat32. Not that you have files over 4GB in size you're trying to transfer, correct?

---

### Post by crazybrit4967 on 2006-12-23
No, I had one 70ish GB Fat32 partition, and I was trying to transfer some DVDs onto it.  I gave up on that, though, and now I reformatted it as ext3.  All I need to do now is mount it in Linux by editing /etc/fstab - it should be pretty simple, but I don't know what to put there.  Can you help?

---

### Post by crazybrit4967 on 2006-12-23
Can anyone help?  I just need the line to put in /etc/fstab so I can mount an ext3 partition!

---

### Post by Sef on 2006-12-23
Ext2 and Ext3 are the same except that Ext3 had journaling.

---

### Post by crazybrit4967 on 2006-12-23
Okay, but the partition still isn't mounted.  Don't I need to add something to fstab to get it to mount?

---

### Post by Sef on 2006-12-23
Check out [Psychocat]("http://www.psychocats.net/ubuntu/mountlinux")'s mounting linux.

---

### Post by msak007 on 2006-12-24
Sorry crazybrit4967, I was not home and could not answer your thread in a timely manner. But the instructions Sef linked to should help you out. aysiu's site is a wealth of knowledge for beginners.

---

### Post by crazybrit4967 on 2006-12-24
Thanks!  I'll try that.

---

### Post by michaeljustman on 2006-12-24
---EDIT: Oops my bad.

---

### Post by crazybrit4967 on 2006-12-24
Okay, that worked great.  Thanks a bunch!

---

### Post by crazybrit4967 on 2006-12-24
Okay, that didn't work out exactly as I had hoped it would - everything is readonly.  Here's the line I have in /etx/fstab atm:

/dev/hda1       /media/shared   ext3        rw,user,noauto  0       0

does anyone know what I need to change so I can modify the files?

---

### Post by spockrock on 2006-12-24
> **crazybrit4967 said:**
> Okay, that didn't work out exactly as I had hoped it would - everything is readonly.  Here's the line I have in /etx/fstab atm:

/dev/hda1       /media/shared   ext3        rw,user,noauto  0       0

does anyone know what I need to change so I can modify the files?

umm..... are your files set to read only or owned by root??

---

### Post by crazybrit4967 on 2006-12-24
Can't I tell it to mount the partition so that I can read and write to the files?

Edit-What I mean by that is that I don't want to edit the permissions, because I thought there was a way that Ubuntu would automatically mount it so I can read/write.  I just have to change an option in the rw,user,noauto section, but I don't know what to add.

---

### Post by spockrock on 2006-12-24
> **crazybrit4967 said:**
> Can't I tell it to mount the partition so that I can read and write to the files?

yeah you sure can, but if the files are owned by root, or were set as read only previously then thats what you get.

---

### Post by mojoman on 2006-12-24
Thought I'd just throw in another argument against the FAT32-option, and that is that FAT32 does not support owner and group. I wanted my /home to be accessible on my dual-boot with both Ubuntu and XP but FAT32 wasn't a very good solution. Imagine a /home without file ownership... Anyway, now I use EXT IFS and it work fine. (The only drawback is that in XP all users can access any users /home, which might be a huge problem depending on who uses XP. This can probably be worked out in XP but I haven't really bothered, since I only use XP to play games.)

/mojoman

---

### Post by crazybrit4967 on 2006-12-24
Okay, so I just need to change the folder permissions in Nautilus?  There's no option in Fstab?  And if that's true, how come all the files on my iPod are read/write, even though I didn't change any of the permissions?

---

### Post by coffeecat on 2006-12-24
Sorry - mistaken post deleted.

---

### Post by spockrock on 2006-12-24
> **crazybrit4967 said:**
> Okay, so I just need to change the folder permissions in Nautilus?  There's no option in Fstab?  And if that's true, how come all the files on my iPod are read/write, even though I didn't change any of the permissions?

ok well in nautilus check who owns, the folder, just rick click properties, and permissions.  You can see what other accounts can do as well.

report back with your findings.

---

### Post by rowanparker on 2006-12-24
And yes, it works fine in iTunes.

But be warned, if Linux crashes and you boot up into Windows straight away the ext3 partition wont be mounted because the Journal is empty, you must boot up Linux so the journal can mend the crash and then boot up Windows again.

---

### Post by crazybrit4967 on 2006-12-24
> **spockrock said:**
> ok well in nautilus check who owns, the folder, just rick click properties, and permissions.  You can see what other accounts can do as well.

report back with your findings.
Yeah, I already tried that; it's owned by root.  However, when I tried changing the permissions nothing happened - I think the changes were only applied to that folder and none of the subfolders.  That's why I wanted to mount it so I can read/write files, like I can with my iPod or any flash drives.

---

