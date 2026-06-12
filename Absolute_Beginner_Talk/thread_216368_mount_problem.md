---
title: "mount problem"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-07-15
Hi all! With a dual boot system, (XP & Ubuntu) I have mounted xp fat32 on each bootup. However, I cannot seem to mount windows NTFS on bootup. Following the wiki 'dapper/windows guide I have modified the code in fstab to try to achieve this but onlt the 'fat'is mounted. Any suggestions please on how to achieve mounting. I have included fstab attachment.
Thanks
Regards

---

### Post by Sbarton on 2006-07-15
Seems the attachment was missing from above post?
Anyway I have uploaded again.

---

### Post by autocrosser on 2006-07-15
There is a thread on Fuse--which is the ability to mount NTFS--this is expermental stuff--if you write to your NTFS, you can scramble your Windows install.  See  [http://www.ubuntuforums.org/showthread.php?t=142481](http://www.ubuntuforums.org/showthread.php?t=142481)  for more info--

All that being said--I sometimes write to my NTFS--mostly read from it.

---

### Post by digby on 2006-07-15
The problem is that you are mounting both the fat32 partition and the ntfs partition to /media/windows.  You have to mount them in different places.  The ntfs is being mounted, just when it gets to the next line, it mounts the fat32 over top.  I don't know if this actually unmounts the ntfs, but in either case, it won't be accessible.  

All you have to do is change one of your /media/windows lines in /etc/fstab to something else (make sure you make that folder first) and run```
sudo mount -a
```Then all will be well.

---

### Post by Sbarton on 2006-07-16
> **digby said:**
> The problem is that you are mounting both the fat32 partition and the ntfs partition to /media/windows.  You have to mount them in different places.  The ntfs is being mounted, just when it gets to the next line, it mounts the fat32 over top.  I don't know if this actually unmounts the ntfs, but in either case, it won't be accessible.  

All you have to do is change one of your /media/windows lines in /etc/fstab to something else (make sure you make that folder first) and run```
sudo mount -a
```Then all will be well.

Thanks for all replies! digby I have tried changing fstab to '/media/hda5' but this does not work. Any idea what the entry should look like that is different from the attachment above? I only want to read ntfs not write.
The fat icon is mounted and I can read/write to that.
Thanks
Regards:)

---

### Post by Denis on 2006-07-16
I see a line (|) between the dump and pass parameters, delete it if there is one in the text file. 

You also have to create the directory where you want to mount. If you want to mount at /media/hda5, create this "hda5" directory in /media.

---

### Post by Sbarton on 2006-07-17
> **Denis said:**
> I see a line (|) between the dump and pass parameters, delete it if there is one in the text file. 

You also have to create the directory where you want to mount. If you want to mount at /media/hda5, create this "hda5" directory in /media.

Thanks for your reply Denis. All sorted now a change in fstab done the trick.By the way the character between the dump & pass was the curser line captured in the screenshot, well observed though.
Also thanks to everyone who input into the post
Thanks:) 
Regards

---

