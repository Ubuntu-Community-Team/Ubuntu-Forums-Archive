---
title: "Mounting the floppy drive"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2007-02-28
Hi!  Could someone please tell me how to mount my floppy disk drive from the terminal?  Thanks!

---

### Post by steven8 on 2007-02-28
I found this from an old post:

> I think this is a bug. After installing Ubuntu Edgy this seems to be the default setting for the floppy drive(s).

Open your fstab as root and locate the floppy drive entry. It should like this:

/dev/ /media/floppy0 auto rw,user,noauto 0 0

Add fd0 after /dev/ and i should look like this:

/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

Save the changes to fstab and do one the following:
1)use drive mounting plugin to mount /dev/fd0
**2)open terminal and type "mount /dev/fd0"**
3)reload fstab
4)restart ubuntu

After the procedures above, the floppy drive should be able to load properly with read and write access.

I don't know if you are this whole bit of trouble, so I bolded the line I thought you might need most.

---

### Post by Darklighter137 on 2007-02-28
Thanks!  But, before I try it, what is the command to unmount? ^_^

---

### Post by steven8 on 2007-02-28
I've never done this through the terminal, but I'd imagine it would be:

"unmount /dev/fd0"

---

### Post by yabbadabbadont on 2007-02-28
> **steven8 said:**
> I've never done this through the terminal, but I'd imagine it would be:

"unmount /dev/fd0"

Actually, it is : 

umount /media/floppy0

OR

umount /dev/fd0

NOTE: umount, not unmount

---

### Post by steven8 on 2007-02-28
> **yabbadabbadont said:**
> Actually, it is : 

umount /media/floppy0

OR

umount /dev/fd0

NOTE: umount, not unmount


You know, I'm kicking myself.  This sounds lame, but I know the umount command, and still typed unmount.  Thanks yabba.

---

### Post by Darklighter137 on 2007-02-28
Thanks guys, but I tried it both ways and got some error each time:
justin@justin-desktop:~$ sudo mount /dev/fd0
Password:
mount: can't find /dev/fd0 in /etc/fstab or /etc/mtab
justin@justin-desktop:~$ sudo mount /media/fd0
mount: can't find /media/fd0 in /etc/fstab or /etc/mtab

---

### Post by yabbadabbadont on 2007-02-28
> I think this is a bug. After installing Ubuntu Edgy this seems to be the default setting for the floppy drive(s).

Open your fstab as root and locate the floppy drive entry. It should like this:

/dev/ /media/floppy0 auto rw,user,noauto 0 0

Add fd0 after /dev/ and i should look like this:

/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

Save the changes to fstab and do one the following:
1)use drive mounting plugin to mount /dev/fd0
2)open terminal and type "mount /dev/fd0"
3)reload fstab
4)restart ubuntu

After the procedures above, the floppy drive should be able to load properly with read and write access. 
Did you read and follow these instructions?

---

### Post by Darklighter137 on 2007-02-28
Read, yes... Follow or understand, not really.  I was hoping that there wasn't a bug in the latest release, because I don't understand how to edit that thing called "fstab".

---

### Post by steven8 on 2007-02-28
This is a link to the whole thread.  I have never edited the fstab either.

[http://ubuntuforums.org/showthread.php?t=341359&highlight=mount+floppy+drive+terminal]("http://ubuntuforums.org/showthread.php?t=341359&highlight=mount+floppy+drive+terminal")

---

### Post by Darklighter137 on 2007-02-28
Thanks, I'll see what I can do about it later. =)

---

