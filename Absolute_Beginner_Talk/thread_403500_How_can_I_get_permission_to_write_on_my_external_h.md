---
title: "How can I get permission to write on my external harddisk? [Resolved]"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by sdyx on 2007-04-07
Here is the problem: I have an external harddisk (named: [COLOR="DeepSkyBlue"]My Book[/COLOR]). 
I can read all files on the external harddisk and copy them to my desktop,
but when I try to write on it ubuntu tells me that I don't have permission to do so.

I tried this:
> sdy@sdy-desktop:~$ sudo chown /media/My Book sdy
chown: `/media/My': invalid user
but as you can see it didn't work.

What am I doing wrong? Can someone please help me?
(I'm a complete ubuntu-noobie)
A step-by-step-tutorial would be highly appreciated. 
(sorry for my bad english)

---

### Post by Famicommie on 2007-04-07
```
sudo chown <user name> /media/My\ Book\ sdy/
```

You have to use those slashes before spaces in the terminal, otherwise it won't understand what you're saying.
Also, make sure to specify WHO you intend to change the owner to ;)

---

### Post by livingtarget on 2007-04-07
Often tab completion is brilliant in situations like these, type the first few letters like /media/My and press tab and it should complete the directory for you with all the correct escape characters (slashes).

Assuming that tab completion is enabled.

---

### Post by aysiu on 2007-04-07
What filesystem is the external hard drive?

If it's Ext3, you should be able to *chown* it, but if it's NTFS or FAT32, you may have to change your mount options--you will not be able to change ownership in the traditional fashion.

---

### Post by sdyx on 2007-04-07
**Famicommie**,** livingtarget** - Thank you very much,

Now I only have to know how to make my "My Book" writeable. :) 

I tried :
> sdy@sdy-desktop:~$ sudo chown sdy /media/My\ Book\ sdy/

But then I got this:
> chown: cannot access `/media/My Book sdy/': No such file or directory


so I typed:
> sdy@sdy-desktop:~$ sudo chown sdy /media/My\ Book
chown: changing ownership of `/media/My Book': Read-only file system

What do I have to do now? (Like I said: Total noobie :-P )

---

### Post by sdyx on 2007-04-07
I think it is FAT32.

---

### Post by aysiu on 2007-04-07
> **sdyx said:**
> I think it is FAT32.
FAT32 external drives usually automount with the correct permissions, but it looks as if something's wrong, and you may have to manually specify your mount options. This should help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Post back any questions you might have.

---

### Post by Famicommie on 2007-04-07
Aysiu brings up a very good point. Is it NTFS, VFAT, or ext3? If it's NTFS, then you need to install something that will allow you to write to drives. [There is a how-to for ntfs-3g here](http://ubuntuforums.org/showthread.php?t=217009)

If it's ext3, then all you have to do is type the command
```
sudo chmod 777 /media/My\ Book\ sdy/
```

---

### Post by sdyx on 2007-04-07
**aysiu**, **Famicommie** - Thank you! I'll give it a try.

---

### Post by aysiu on 2007-04-07
If it works, great. If it doesn't, please post back the output of these [terminal](http://www.psychocats.net/ubuntu/terminal) commands: ```
sudo fdisk -l
df -h
cat /etc/fstab
``` With the terminal, copy and paste is always the way to go. It's easier, faster, and more accurate than retyping.

---

### Post by sdyx on 2007-04-07
**Famicommie **- I installed ntfs-3g. 

**aysiu** - That's what I got when I typed in the terminal command:
> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS
sdy@sdy-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              72G  3.4G   65G   5% /
varrun                252M   92K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  116K  9.9M   2% /proc/bus/usb
udev                   10M  116K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  235M   7% /lib/modules/2.6.17-11-generic/volatile
/dev/sda1             233G  231G  2.0G 100% /media/My Book


---

### Post by aysiu on 2007-04-07
Looks as if it's NTFS, so you will need NTFS-3G. Unfortunately, I don't know how to use that program. This may help you, though:
[HOWTO: NTFS with read/write support using the ntfs-3g (easy & safe method)](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by sdyx on 2007-04-07
I already installed NTFS-3G and strolled through the FAQ but I don't have no clue what to do next.

---

### Post by sdyx on 2007-04-08
Aaawwright! I did it! 
Thank you very much for your support!

---

