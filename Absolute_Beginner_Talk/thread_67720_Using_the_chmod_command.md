---
title: "Using the chmod command"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by mwdowns on 2005-09-21
Hello folks.

I thought I had this figured out.  My storage drive (FAT32) can be read by ubuntu, but not written to by ubuntu.  So, I figured I'd just use the chmod command like so```
sudo chmod u+w storage
```However, that doesn't seem to work.  The permission hasn't changed and I am still unable to write to that drive.

Any ideas about what I'm doing wrong?

Thanks.

---

### Post by davmac on 2005-09-21
How have you mounted the partition? If you have a look at [http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat) it gives the instructions for mounting a FAT32 partition so that all users get read/write access. Does this solvce your problem?

HTH,

Dave Mac

---

### Post by mwdowns on 2005-09-21
[QUOTE=davmac]How have you mounted the partition? If you have a look at [http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat) it gives the instructions for mounting a FAT32 partition so that all users get read/write access. Does this solvce your problem?

HTH,

Dave Mac[/QUOTE]

Thanks for the reply, Dave.  I mounted the partition when I installed Breezy the other day.  I just tried to click on the ubuntuguide.org link, but it seems to be down.  I've checked my fstab, and it's there.  Under System->Administration->Disks, the partion is enabled.  I can read it and copy from it.  But can't write to it.  Hmmmm.... :???:

---

### Post by xmastree on 2005-09-21
[QUOTE=mwdowns] I've checked my fstab, and it's there.[/QUOTE]How does it look in there? Here's mine:
```
/dev/hdb3	/mnt/shared	vfat	umask=0000	0	0
```Look at the umask section in yours.

---

### Post by mwdowns on 2005-09-22
[QUOTE=xmastree]How does it look in there? Here's mine:
```
/dev/hdb3	/mnt/shared	vfat	umask=0000	0	0
```Look at the umask section in yours.[/QUOTE]

Changed my fstab to look like yours, but that didn't seem to help either.

I'm surprised, though, that the chmod command isn't working.  I thought when you do a sudo chmod, you chould change anything.

Any more ideas?

---

### Post by aysiu on 2005-09-22
[QUOTE=mwdowns]Changed my fstab to look like yours, but that didn't seem to help either.[/QUOTE] Exactly like xmastree's? Or similarly, but with your particular folders and devs? And did you reboot after editing the /etc/fstab?

---

### Post by Wolki on 2005-09-22
[QUOTE=aysiu] And did you reboot after editing the /etc/fstab?[/QUOTE]

"sudo mount -a" should be enough, no need to reboot.

---

### Post by mwdowns on 2005-09-22
[QUOTE=aysiu]Exactly like xmastree's? Or similarly, but with your particular folders and devs? And did you reboot after editing the /etc/fstab?[/QUOTE]

Hehehe! :D  No, I didn't enter it exactly...only the umask=0000 part.

Looking at my Linux Pocket Guide, I see that umount -a means I'm going to unmount all my drives.  How do I get them back?

---

### Post by davmac on 2005-09-23
I don't think you have to unmount everything. A simple "sudo mount -a" will refresh 'em.

Dave Mac

---

### Post by fordfan753 on 2005-09-23
[QUOTE=mwdowns]Hehehe! :D  No, I didn't enter it exactly...only the umask=0000 part.

Looking at my Linux Pocket Guide, I see that umount -a means I'm going to unmount all my drives.  How do I get them back?[/QUOTE]

It should only be ```
umask=000
```
You have one too many 0's in there, this may be your problem.
mount -a does unmount your drives, kinda, it more just forces remounts on all of them, so you do not need to worry about remounting, because this is essentially what it does.

---

### Post by xmastree on 2005-09-23
[QUOTE=fordfan753]It should only be ```
umask=000
```
You have one too many 0's in there,[/QUOTE]I just double checked mine, four zeroes. All my Windows drives have four digits in the umask section, and all work fine.

---

### Post by fordfan753 on 2005-09-23
[QUOTE=xmastree]I just double checked mine, four zeroes. All my Windows drives have four digits in the umask section, and all work fine.[/QUOTE]

OK, I always use three 0's, but maybe four is ok, that's my learning for today :)

---

### Post by xmastree on 2005-09-23
[QUOTE=fordfan753]OK, I always use three 0's, but maybe four is ok, that's my learning for today :)[/QUOTE]Dunno where I got four from. The guide only has three...

---

