---
title: "Writing to media 1 Win xp partition"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-20
Hello, I would like to be able to change the "UUID=B444EE8344EE47A6 /media/hda1 ntfs defaults 0 0" to "UUID=B444EE8344EE47A6 /media/hda1 ntfs defaults 0222 0 0"

would the proper terminal code be?: sudo /dev/UUID=B444EE8344EE47A6 /media/hda1 ntfs defaults 0222 0 0

this is my df -h and more /etc/fstab


me@me:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             9.2G  2.9G  5.9G  33% /
varrun                248M   80K  248M   1% /var/run
varlock               248M  4.0K  248M   1% /var/lock
procbususb             10M  128K  9.9M   2% /proc/bus/usb
udev                   10M  128K  9.9M   2% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   18M  230M   8% /lib/modules/2.6.17-10-386/volatile
/dev/hda1              33G  5.8G   27G  18% /media/hda1
/dev/hda2              13G  3.8G  8.5G  31% /media/hda2
me@me:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=14d5392f-bc2a-4a0e-bbb5-410d6410172e / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=B444EE8344EE47A6 /media/hda1 ntfs defaults 0 0
# /dev/hda2 -- converted during upgrade to edgy
UUID=e3f559c9-f006-4a21-9398-23d4c4bb5ad8 /media/hda2 ext3 defaults 0 2
# /dev/hda5 -- converted during upgrade to edgy
UUID=4210b1ee-905e-40be-8676-707ea3095150 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

Thank you,
-c.

---

### Post by .t. on 2006-10-20
I think you mean you want to edit your fstab (filesystem table).
Also, the code you want is "uid=0222", not just "0222". If you are hoping for write support, sorry mate. That's too dangerous at the moment and so isn't implemented for NTFS. However, to edit your fstab, run: "sudo nano /etc/fstab", or for a GUI editor, "sudo gedit /etc/fstab". Then change the line you want. Note that if you mess it up, your system may not boot, so be careful!

---

### Post by kidders on 2006-10-20
Hi there,

Unfortunately, what you've posted isn't quite right. I'm guessing "0222" is a umask, in which case, your fstab entry would be:

**UUID=B444EE8344EE47A6 /media/hda1 ntfs umask=0222 0 0**

Typing "sudo /dev/UUID=B444EE8344EE47A6 /media/hda1 ntfs defaults 0222 0 0" won't do much more than complain at you ... you'll need to update your /etc/fstab and remount any devices you change with **mount -o remount /media/hda1** for example.

**Edit:** Oops... too slow hehe.

---

### Post by Kateikyoushi on 2006-10-20
Why do you want to edit it ?
Just start the live with the /dev/hdx and it will be replaced.

To edit the fstab

```
sudo nano /etc/fstab
```

---

### Post by crimesaucer on 2006-10-20
I'm sorry, I wrote that wrong, the code that I was wondering about was for permission to read the Xp partition and it was this:

/dev/hda1 /media/hda1 ntfs defaults,umask=0222 0 0

do I have to change it to:

/dev/UUID=B444EE8344EE47A6 /media/hda1 ntfs defaults,unmask=0222 0 0

and do I need the sudo command before it? like this?:

sudo /dev/UUID=B444EE8344EE47A6 /media/hda1 ntfs defaults,unmask=0222 0 0

sorry for the confusion.

---

### Post by crimesaucer on 2006-10-20
Yeh, I meant reading the xp partiton, however, would I be able to add a Fat32 partition through gparted, or is it to late now that I have 4 partitons (xp, 6.06, 6,10, and swap)?

I'm still not sure about the command, do I want unmask unmask=0222 0 0, or the other command, UID=2220 0 0

and does "nano" edit it in terminal, and is it easier than mousepad.

***funny, after re-reading this I think I understand it now, I'm just not clear on whether I want the UID or the unmask.

---

### Post by kidders on 2006-10-21
> **crimesaucer said:**
> would I be able to add a Fat32 partition through gparted, or is it to late now that I have 4 partitons
It's too late :-( Usually, people create their third or fourth filesystem inside an extended partition, giving them the option of adding more, if they ever need to. Your only option now would be to pack up the biggest one, put it someplace else temporarily, and reorganise that part of your partition table a bit :-(

> **crimesaucer said:**
> I'm still not sure about the command, do I want unmask unmask=0222 0 0, or the other command, UID=2220 0 0

The command you're after is **mount -t ntfs -o umask=0222 /dev/hda1 /media/hda1**, or you can add **UUID=B444EE8344EE47A6 /media/hda1 ntfs umask=0222 0 0** to your /etc/fstab.

If you need to check what the various mount options do, take a look at the man page for "mount". It's quite long though ... there's a section for every supported filesystem.

---

### Post by crimesaucer on 2006-10-21
Thanks, my windows ntfs is readable now, but now I have a problem with my hda2 (ubuntu/xubuntu 6.06 LTS 14gb) partition.

I am not sure why I can't log in to my partition 2 of ubuntu/xubuntu 6.06.

I'm going to post a new thread about it so, don't worry about it on this thread.

Thanks for the info,
-c.

---

