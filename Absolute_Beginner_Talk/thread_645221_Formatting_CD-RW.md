---
title: "Formatting CD-RW"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by mnb on 2007-12-19
Hi All,

In windows I can format a CD-RW with a FAT file system and then use the CD just like a large floppy or small HD.  I'd like to do the same under Ubuntu... i.e. create an ext2 file system on the CD and then use the CD as a small file system.

Has anyone done this?  If so could you please provide some specifics on how you did this?

Thanks,

Michael

---

### Post by bone2006 on 2007-12-26
I haven't, but have you tried using k3b and then erasing the rewritable with the option? I'd assume it would format it properly

---

### Post by Cariboo1938 on 2007-12-31
> **mnb said:**
> Hi All,
In windows I can format a CD-RW with a FAT file system and then use the CD just like a large floppy or small HD.  I'd like to do the same under Ubuntu... i.e. create an ext2 file system on the CD and then use the CD as a small file system.
Has anyone done this?  If so could you please provide some specifics on how you did this?
Thanks,
MichaelHello..
I 'googled' and found [THIS]("http://www.ubuntuforums.org/showthread.php?t=129093&highlight=Packet+writing"). I hope it helps.:) 
In the attachment ) is exactly what I had to do. It worked, I remember, but it was a bit tricky and I don't use it anymore.
Good luck!
PS
(in order to read the attachment you need  to  open it with AbiWord or Open office.

EDIT:
[HERE]("http://bugs.kde.org/show_bug.cgi?id=146878") is the reason why I don't use uftools right now!

---

### Post by laidback on 2007-12-31
I've understood this to be a multisession CD. If you create a CD-RW in K3b say you have the option of closing if off (single session) or leaving it open (multisession), with the later I believe that you can then add to it later until it's full up. Cannot remember whether I could use Nautilus as the file manager once it was created, but worth a go.

---

