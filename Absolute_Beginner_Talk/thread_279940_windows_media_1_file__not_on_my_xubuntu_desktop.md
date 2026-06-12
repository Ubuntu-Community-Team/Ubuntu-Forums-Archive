---
title: "windows media 1 file ?? not on my xubuntu desktop?"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-18
Hello, I just installed an ubuntu 6.06 with a dual booted WinXp, and then installed the xubuntu desktop. Then my media 1 (WinXp) icon disappreared from the desktop, and i don't see it in the thunar file system. Where can I access that.

I also was hoping someone could explain to me how I can access the media 1 windows partition files. When I tried to click on the icon on ubuntu desktop it said I need to be the "root" user. I have had trouble with this problem in other instances like trying to drag and drop folders. I am the only user on this computer. Is "sudo" my command as the root user, or working in the root?

Any quick explainations would be cool.

Thanks,
-c.

---

### Post by taurus on 2006-10-18
I don't believ XFce4 will display icons on your desktop without using idesk!  However, you can still access your Windows from a terminal or other file manager.  If you want to know where your Windows partition is, open a terminal and type

```
df -h
```
but chances are it's probably in /media.  And if you paste your /etc/fstab here, then people can tell you why you can't access your NTFS.  It's probably about permissions...

```
more /etc/fstab
```

---

### Post by crimesaucer on 2006-10-18
yes, I would like to know about the permissions if anyone can explain it to me, thanks.

also, the xfce in the xubunut-desktop install isn't the new xfce 4.4 yet right, is it the 4.2 or am I wrong.

---

### Post by taurus on 2006-10-18
Gonna paste the output of your /etc/fstab here!!!

```
more /etc/fstab
```

---

### Post by d3v1ant_0n3 on 2006-10-18
For gnome, to be able to file-browse as root, run 'sudo nautilus' -This will allow you to move files into non user directories etc...I unfortunately have NO idea how to do it in xubuntu, although if nautilus is the file browser, then the same will apply.

Hope you're still having fun:D

---

### Post by crimesaucer on 2006-10-18
this is what it reads:

:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              13G  3.8G  8.5G  31% /
varrun                248M   84K  248M   1% /var/run
varlock               248M  4.0K  248M   1% /var/lock
udev                  248M  120K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   19M  230M   8% /lib/modules/2.6.15-27-386/volatile
/dev/hda3             9.2G  197M  8.6G   3% /home
/dev/hda1              33G  5.8G   27G  18% /media/hda1
me@me:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


So could you explain the permissions to me, thanks.

---

### Post by crimesaucer on 2006-10-18
I have thunar as the file system. If I am in the ubuntu desktop, use nautilus then? Thanks.

I'm having a lot of fun learning this desk top, plus the smooth and quick web browseing is SOOOO much better then Windows. I watch the cpu of my xfce when I browse pages and I see it jump to 100 so fast and load the pages so fast compared to waiting for windows to load the same pages, and I haven't even configured Firefox's about:config yet.

I still could use some help with the VLC.

thanks for asking.

---

### Post by taurus on 2006-10-18
In your /etc/fstab, try to make your NTFS to look something like this!

```
/dev/hda1 /media/hda1 ntfs defaults,umask=0222 0 0
```
"umask=0222" mean you as a user can read to it but can't write to it...

---

### Post by crimesaucer on 2006-10-18
Thank you, so I'm about to install the Beta into my 3rd partiton,  when I install the Beta 6.10, will I change this code:

 /dev/hda3 /home ext3 defaults 0 2

into this: /dev/hda3 /home ext3 defaults,umask=0222 0 0

just like the NTFS below:

/dev/hda1 /media/hda1 ntfs defaults,umask=0222 0 0

...so the code unmask=0222 will work for the xubuntu Beta partition or would I need a different code so it can "write" to the different partition.

Thanks,
-c.

---

### Post by taurus on 2006-10-18
Actually, if your /home partition is ext3, the don't need to add "umask=0222" after the defaults.  The reason you want to add "umask=0222" after the defaults for NTFS is so that you can at least read from it.  But if it's a vfat/fat32, then you would use "umask=0000" to give you read and write permissions to it.  Therefore, only add "umask" if you want to mount NTFS or VFAT filesystems...

---

### Post by crimesaucer on 2006-10-18
Thank you for the info, am I able to add a Fat32 in gparted if I need some file transfer, and how small can a Fat32 partition be?

Thanks,
-c.

---

