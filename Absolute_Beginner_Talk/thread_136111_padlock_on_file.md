---
title: "padlock on file??"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by dude of wonders on 2006-02-25
i copied a couple of videos from my dvd and put them on my computer and for some reason they have a little padlock in the top right corner of the file, anyone know what this is.

---

### Post by madddonkey255 on 2006-02-25
It means they're read-only.  You can change that if you want by right clicking and going to properties then the permissions tab.

---

### Post by ajgreeny on 2006-02-25
I think it means the file is locked and you can't even read it except as root.  I'm not sure what the reasons for this is but no doubt someone else will let you know in more detail.

---

### Post by wylfing on 2006-02-25
> I think it means the file is locked and you can't even read it except as root.
No, this is wrong. **madddonkey255** explained it correctly.

---

### Post by cilynx on 2006-02-25
The padlock means that you do not have permissions to write to the file.

It could be that the file is owned by someone else.

In the case of copying from CD/DVD, it's because the file was set to be read-only on the disc and it brought its permissions with it when you copied it.

If you right-click on it and check properties, you should be able to adjust the permissions (assuming your user owns the file)

---

### Post by dude of wonders on 2006-02-25
thanks i changed the permission and it got rid of the padlock.

---

### Post by ajgreeny on 2006-02-25
[QUOTE=wylfing]No, this is wrong. **madddonkey255** explained it correctly.[/QUOTE]

I did admit I was not certain about the padlock on a file icon but why is it that when I try just to read a file with a padlock that an error message tells me, for example

"You do not have enough permissions to read **file:///etc/group-**"

but if I try as root then I am able?

---

### Post by Jucato on 2006-02-25
maybe because it is owned by root AND not writeable/readable by others.

---

### Post by cilynx on 2006-02-25
The padlock show up "at a minimum" when you don't have write access.  You may not have read access either.  I thought that not having read-access put a red X on the icon, but I could be wrong.  It works as root because as you know, root can do just about anything.

---

### Post by ajgreeny on 2006-02-27
OK, Thanks folks.  I stand corrected.
This is exactly what I like about linux and this ubuntu forum in particular; if you get something wrong, there is none of the "You stupid idiot" type of response but a reasoned explanation of the right answer.
I'm very grateful and learning fast, (perhaps not quite fast enough, but getting there!).

---

### Post by Installer36 on 2006-02-27
When I access my XP computer via Samba the files show a lock on them but when I copy them over to my Ubuntu computer the lock is no longer there..Is this normal?  Do I want the lock present? Iam the only one who uses this computer so I am not worried about user privalages. Should I be?....Thanks Installer36

---

### Post by Edward The Bonobo on 2006-02-27
Is there any way of changing this...ie, when you copy over read-only files from DVD/CD/whatever, you automatically have write priveleges?  I find it a bit of a pain - especially when I'm copying over directory structures.  You have to re-set the properties for the directory *and *the files.

---

### Post by F W Adams on 2007-11-05
I've having trouble mounting a FAT32 partition correctly. In Nautilus it comes up with a padlock, it reads fine but will not write so I need to make it write enabled. I've tried right click, properties, permission but cannot make any changes because  I need to be root to do it.

Also this partition, and also another that is mounted during FSTAB are showing the owner as root and I feel this should be <user>, in fact this may be the problem. How do I get the files recognised as belonging to <user> rather than root, or at least get the FAT32 write enabled?

I enclose FSTAB
/dev/hdc1 is the FAT32 that I can't write. /dev/hdc2 works fine though it has the wrong owner?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc3
UUID=3b97f49a-638a-43ef-93ef-dbc2036fe83d /               ext2    defaults,errors=remount-ro 0       1
# /dev/hda1
#felix UUID=A6C0F132C0F108F7 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
#felix UUID=0A74427974426811 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc1
#felix UUID=444C-0E08  /media/hdc1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdc2	mount Felix's shared data about 30.10.07
/dev/hdc2 	/home/felix/share	ntfs-3g	     defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc1	mount Felix's shared MSDOS data ( within shared ) 4.11.07
/dev/hdc1 	/home/felix/share/MSDOS.and.data	vfat
# /dev/hdc5
UUID=6f3358df-a8c5-4fa6-8565-7a89a7370199 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

