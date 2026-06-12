---
title: "access files from screen?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by niceguy123 on 2008-01-08
My Ubuntu desktop is down. The screen says something about fsck failed.

I have a black screen with text lines and root@mycomputer:"# at the bottom.

Can I access and backup my files from here?

Thanks. 

(I'm writing from a different computer. )

---

### Post by Sbarton on 2008-01-08
Perhaps you can try with a LiveCD and see if you can save your files through that.
regards.

---

### Post by Arador Aristata on 2008-01-08
It depends on the exact error but when this happened to me I did the following.

Boot from Live CD.
Open terminal.
sudo fsck /dev/hdd1

Not sure if that is the perfect command but was somthing like that. Depends on your hard drives name in Ubuntu.

---

### Post by niceguy123 on 2008-01-08
ran live cd and the command you gave with no result.

BTW- how can i find my files to backup before the situation gets any worse?

---

### Post by erginemr on 2008-01-08
Can you see your hard drive when you run from the Live CD and use Main Menu -> Places - Computer?

---

### Post by niceguy123 on 2008-01-08
Thanks, That was easy enough. Found the files via hard drive on cd live. Will back and continue.

---

### Post by niceguy123 on 2008-01-08
Thanks, That was easy enough. Found the files via hard drive on cd live. Will backup and continue.

I tried and again got stuck, Yes, I can see the folders via places>computer>disk>home  but it will not let me copy the files because "you are not the owner"

---

### Post by erginemr on 2008-01-08
Gosh! What exactly is the error message that fsck says?

Maybe you can still save your Ubuntu install. I believe you should download the GParted Live CD and let GParted (Gnome Partition Editor) check your problematic hard drive and try to fix it from the Live CD. The Ubuntu Live CD also has GParted but I would still suggest you to burn and use the following:

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by lswest on 2008-01-08
and fyi, in a terminal screen you can use the ls command to list files & folders, cd to change directory, cp to copy, tar to compress them to archives, rm to delete, vim to edit (or nano), and mv to move files.  Backing up doesn't need a liveCD.  i find it faster without a liveCD honestly.  But hey, to each his (or her) own.  and the fsck error happened to me once, i eventually stopped trying to fight with it and just re-installed Ubuntu.  Is the error on an XP drive?  was it shut down properly?

---

### Post by erginemr on 2008-01-08
> **niceguy123 said:**
> Thanks, That was easy enough. Found the files via hard drive on cd live. Will backup and continue.

I tried and again got stuck, Yes, I can see the folders via places>computer>disk>home  but it will not let me copy the files because "you are not the owner"

If you can run Nautilus with root permissions (Alt+F2 -> gksu nautilus) from the Live CD environment (I am not sure whether you can), then maybe you can override those permissions.

Also you may try the command chroot to really "enter" into your installed partition as I have tried to eplain in my latest post here in this thread:
[http://ubuntuforums.org/showthread.php?t=659813](http://ubuntuforums.org/showthread.php?t=659813)

---

### Post by niceguy123 on 2008-01-09
> **lswest said:**
>   Is the error on an XP drive?  was it shut down properly?

I don't think that I have xp on this drive anymore. It might have been close non-properly. Someone else shut it down last before the problem.

> and fyi, in a terminal screen you can use the ls command to list files & folders, cd to change directory, cp to copy, tar to compress them to archives, rm to delete, vim to edit (or nano), and mv to move files.  Backing up doesn't need a liveCD.  i find it faster without a liveCD honestly. 

I'd like to learn to do all of this, but I just don't have the spare time right now. Asides for enjoing learning to use Ubuntu-Linux I have real work to do.

> But hey, to each his (or her) own.  and the fsck error happened to me once, i eventually stopped trying to fight with it and just re-installed Ubuntu

If I succeed in backing up the files, it seems that I will re-install Ubuntu anew. I might end up doing that in the end even if I can't backup.

---

### Post by erginemr on 2008-01-09
Did you have any chance to try these?

> **erginemr said:**
> If you can run Nautilus with root permissions (Alt+F2 -> gksu nautilus) from the Live CD environment (I am not sure whether you can), then maybe you can override those permissions.

Also you may try the command chroot to really "enter" into your installed partition as I have tried to eplain in my latest post here in this thread:
[http://ubuntuforums.org/showthread.php?t=659813](http://ubuntuforums.org/showthread.php?t=659813)

> **erginemr said:**
> Gosh! What exactly is the error message that fsck says?

Maybe you can still save your Ubuntu install. I believe you should download the GParted Live CD and let GParted (Gnome Partition Editor) check your problematic hard drive and try to fix it from the Live CD. The Ubuntu Live CD also has GParted but I would still suggest you to burn and use the following:

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by lswest on 2008-01-09
if you need to back up your data files use this ```
To backup:

tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

To Restore:

tar xvpfz backup.tgz -C /

excluding the boot dir and fstab file will give you the ability to restore all your data/settings on a new partition

```
and i want to point out, this isn't my own idea, it's from [here]("http://ubuntuforums.org/showthread.php?t=564836")
i've used it before, and it worked fine as long as your system is up-to-date when you backed it up.  Give it a try.

---

