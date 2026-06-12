---
title: "chmod use"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by javatrumpet on 2005-11-27
How do I change permissions on a folder?  I have my windows partitions mounted in a folder, but I created that folder with sudo, so only root has write permissions to it.  I know the command I need is chmod, but I'm stumpted on getting the right syntax to make the partitions read/write.  It would be best if you included the exact command I need.

---

### Post by aysiu on 2005-11-27
That's not a *chmod* issue. It's a mounting issue.
Follow these directions:
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

It assumes your FAT partition is /dev/hda1
To find out what it really is, type ```
sudo fdisk -l
``` in a terminal

---

### Post by paulmilliken on 2005-11-27
[QUOTE=javatrumpet]How do I change permissions on a folder?  I have my windows partitions mounted in a folder, but I created that folder with sudo, so only root has write permissions to it.  I know the command I need is chmod, but I'm stumpted on getting the right syntax to make the partitions read/write.  It would be best if you included the exact command I need.[/QUOTE]

An example would be
"chmod 777 -R /home/username/foldername" or "sudo chmod 777 -R /home/username/foldername"

Note that the -R flag means recursive so all the sub-folders/files will have their permissions changed too.  For more help type "man chmod".

Furthermore, to change ownership of a folder use the "chown" command.  Type "man chown" for more help on this command.

Paul

---

### Post by aysiu on 2005-11-27
[QUOTE=paulmilliken]An example would be
"chmod 777 -R /home/username/foldername" or "sudo chmod 777 -R /home/username/foldername"

Note that the -R flag means recursive so all the sub-folders/files will have their permissions changed too.  For more help type "man chmod".

Furthermore, to change ownership of a folder use the "chown" command.  Type "man chown" for more help on this command.

Paul[/QUOTE] These are great instructions for chmod on a folder, but mounted Windows partitions are really an /etc/fstab (i.e., mounting) issue.

---

### Post by javatrumpet on 2005-11-27
OK, well, none of the above have helped.  I had already consulted the man pages before I posted my question.  Maybe  a better explanation is in order.

I have my windows partitions properly mounted from /etc/fstab.  The problem is, I can read that folder, but I cannot write to it, which is critical.  I have created a user group called windows which has a ID of 1001.  Maybe there's a way to change the fstab to include those permissions?  Here's my lines for the windows partitions

```
/dev/hda1       /media/win-c    vfat    defaults        0       0
/dev/hda5       /media/mp3      vfat    defaults        0       0
/dev/hda6       /media/mydocs   vfat    defaults        0       0
```

---

### Post by aysiu on 2005-11-27
[QUOTE=javatrumpet]OK, well, none of the above have helped.  I had already consulted the man pages before I posted my question.  Maybe  a better explanation is in order.[/quote] Actually, it would have helped if you'd read the link I linked to earlier. It is not "the man pages." It is a helpful guide to getting your FAT partition mounted so you can read and write from it as user. Please look at it again.

> 
I have my windows partitions properly mounted from /etc/fstab.  They mount into the /media/win-c folder. No, you don't. You have them mounted with *defaults*--that means only root can read them.  

> The problem is, I can read that folder, but I cannot write to it, which is critical. See?  

> I have created a user group called windows which has a ID of 1001.  Maybe there's a way to change the fstab to include those permissions?  Here's my lines for the windows partitions

```
/dev/hda1       /media/win-c    vfat    defaults        0       0
/dev/hda5       /media/mp3      vfat    defaults        0       0
/dev/hda6       /media/mydocs   vfat    defaults        0       0
``` Yes, there's a way to change it. Look at my earlier post, and follow the instructions.

---

### Post by javatrumpet on 2005-11-27
OK, that solved the majority of what I needed.  I changed the fstab accordingly, and I can write to *most* of the folders.  For some reason, 2 folders (My Pictures and My Music) insist they are still root only to write to them, but all other folders on the drive are as I expect.  Why might this be/how do I change that?

---

### Post by aysiu on 2005-11-27
Can you post the output of these three commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

