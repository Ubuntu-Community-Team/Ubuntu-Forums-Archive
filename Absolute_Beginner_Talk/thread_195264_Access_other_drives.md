---
title: "Access other drives?"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-06-12
How can I make Ubuntu see and access other drives and folders? I went to
/mnt and nothing is visible, howdo I mount them?  Thanks !  :o

---

### Post by aysiu on 2006-06-12
If they're external media, they should automount and show up on your desktop.

If they're internal, you'll have to mount them manually or add them to your /etc/fstab file so they'll mount on boot.

Are these Windows or Linux drives?

---

### Post by Drakkor on 2006-06-12
"add them to your /etc/fstab file so they'll mount on boot."
Need help with this !  I have drive 1 (80Gb) with Windows XP four partitions altogether NTFS, and drive 2 (60Gb) with Ubuntu 6.06 Dapper. Ext3. Dual boot. 
Thanks :confused:

---

### Post by catlett on 2006-06-12
Aysiu must have forgotten to post the link to psychocats. Aysiu wrote the guide posted there. Here it is  [http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

This is another good guide   [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by aysiu on 2006-06-12
And if they're Windows drives:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Drakkor on 2006-06-12
I did this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /windows        ntfs    nls=utf8,unmask=0222        0       0

But still hda1 is not in the windows folder,or accessible. Also tried rebooting. :confused:

---

### Post by aysiu on 2006-06-12
After you modified the /etc/fstab file, did you ```
sudo umount /dev/hda1
sudo mount -a
``` or reboot?

---

### Post by Drakkor on 2006-06-12
ya,but got this;

drakkor@drakkor:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by aysiu on 2006-06-12
I don't know if this has anything to do with your error, but your /etc/fstab line should read *umask=0222* instead of *unmask=0222*.

---

### Post by catlett on 2006-06-12
Is this your exact entry? Because the entry in red is wrong 
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hdb1 / ext3 defaults,errors=remount-ro 0 1
/dev/hdb5 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda1 /windows ntfs nls=utf8,[COLOR="Red"]unmask[/COLOR]=0222 0 0
It should be umask not unmask 
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hdb1 / ext3 defaults,errors=remount-ro 0 1
/dev/hdb5 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda1 /windows ntfs nls=utf8,[COLOR="Red"]umask[/COLOR]=0222 0 0 Edit your /etc/fstab and see what happens on reboot. Hopefuly that is it.


Edit: Must have been posting at the same time. Didn't see your reply when I started to post.

---

### Post by Drakkor on 2006-06-12
Thanks,aysiu and catlett :o 
Yep,that did the trick,thought it was unmask,as in unhide or something,lol
So I can mount the other partitions,like this?
/dev/hda2 /windows ntfs nls=utf8,umask=0222 0 0

---

### Post by aysiu on 2006-06-12
As long as they're NTFS and you create separate mount points for them, yes.

FAT32's mount options are slightly different: ```
iocharset=utf8,umask=000 0 0
```

---

### Post by Drakkor on 2006-06-12
Seperate mount points,I'm lost. Tried to mount all the other partitions to the windows folder,but I guess that's no good,lol. Please explain  Thanks

---

### Post by aysiu on 2006-06-12
So basically...

**Bad**:
/dev/hda2 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hda3 /windows ntfs nls=utf8,umask=0222 0 0

**Good**:
/dev/hda2 /windows1 ntfs nls=utf8,umask=0222 0 0
/dev/hda3 /windows2 ntfs nls=utf8,umask=0222 0 0

Two partitions cannot appear as the same folder.

---

### Post by Drakkor on 2006-06-12
Ahh, here's my configuration:
Disk /dev/hda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1431    11494476    7  HPFS/NTFS
/dev/hda2            1432        9732    66677782+   f  W95 Ext'd (LBA)
/dev/hda5            1432        4621    25623643+   7  HPFS/NTFS
/dev/hda6            4622        5861     9960268+   7  HPFS/NTFS
/dev/hda7            5862        9732    31093776    7  HPFS/NTFS

Disk /dev/hdb: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7112    57127108+  83  Linux
/dev/hdb2            7113        7299     1502077+   f  W95 Ext'd (LBA)
/dev/hdb5            7113        7299     1502046   82  Linux swap / Solaris

---

### Post by aysiu on 2006-06-12
So, being wholly uncreative about it, you could create mount points for /dev/hda1, /dev/hda5, /dev/hda6, /dev/hda7 as /windows1, /windows5, /windows6, /windows7...

... or you create more fun names like /bert, /ernie, /molly, /ringwald...

---

### Post by Drakkor on 2006-06-12
LOL !  I had to mkdir for windows2 3 4 etc.but tried to sudo mount -a  but got this: 
                                              drakkor@drakkor:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222        0       0
/dev/hda2       /windows1       ntfs    nls=utf8,umask=0222        0       0
/dev/hda5       /windows2       ntfs    nls=utf8,umask=0222        0       0
/dev/hda6       /windows3       ntfs    nls=utf8,umask=0222        0       0
/dev/hda7       /windows4       ntfs    nls=utf8,umask=0222        0       0

---

### Post by Drakkor on 2006-06-12
Ya, maybe it's this; (aren't you trying to mount an extended partition,
instead of some logical partition inside?)
Yes ! That was it. Now how come the Rename and Move to Trash buttons are greyed out, I wanted to get rid of that one folder and  rename them, guess go back to edit the /etc/fstab file again,lol

---

### Post by aysiu on 2006-06-12
Yeah, /dev/hda2 is an extended partition.

You want /dev/hda1, /dev/hda5, /dev/hda6, and /dev/hda7 only.

---

### Post by Drakkor on 2006-06-12
Hey,Thanks, aysiu couldn't have done it without you !  Cheers !! :D

---

### Post by puterboy on 2006-06-13
[QUOTE=Drakkor]ya,but got this;

drakkor@drakkor:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/QUOTE]

this thread helped me mount my ntfs 500gb hd, but now i wanna mount my cdrom. it gives me this error message when i specify udf format, but it tells me:

mount: i could not determine the filesystem type, and none was specified

when i try to use auto detect for the filesystem. any help?

---

### Post by aysiu on 2006-06-13
CD-ROMs should mount automatically. The only line in my /etc/fstab that relates to CD-ROMs is: ```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
``` And I didn't have to add that in manually.

---

### Post by Russty of Oz on 2006-06-13
[QUOTE=aysiu]And if they're Windows drives:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)[/QUOTE]

[B]Hi, I am trying to access my windows from Dapper, and have been trying the above link, but when I get to this bit;
[/B]
Next, let's edit the fstab file:
sudo nano /etc/fstab

This is what it might look like before we change it:
proc /proc proc defaults 0 0
/dev/hda6 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 /home ext3 defaults 0 2
/dev/hda1 /media/hda1 ntfs defaults 0 0
/dev/hda7 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0  

**all I get is this;**


NU nano 1.3.10             File: /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

[B]There is no mention of /dev/hda1   

So what do I do now?

Russty.[/B]

---

### Post by aysiu on 2006-06-13
You add it.

The bottom line is that it needs to be there *correctly*.

If it's there incorrectly, you change it to be correct.
If it isn't there at all--as is your case--you add the line in.

You can add it in the middle. You can add it at the end. It's up to you where you put it.

---

### Post by Russty of Oz on 2006-06-13
[QUOTE=aysiu]You add it.

The bottom line is that it needs to be there *correctly*.

If it's there incorrectly, you change it to be correct.
If it isn't there at all--as is your case--you add the line in.

You can add it in the middle. You can add it at the end. It's up to you where you put it.[/QUOTE]

Sorry for being so dense!  But how do I insert it an save it?  I have tried some of the commands but I just can't seem to get it to edit.

---

### Post by aysiu on 2006-06-13
```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
``` if you're using Ubuntu

```
sudo cp /etc/fstab /etc/fstab_backup
gksudo mousepad /etc/fstab
``` if you're using Xubuntu

```
sudo cp /etc/fstab /etc/fstab_backup
kdesu kwrite /etc/fstab
``` if you're using Kubuntu

---

### Post by Russty of Oz on 2006-06-13
WOW!  Thanks aysiu!

Now it all works.  Fantastic!!

Russty.

---

### Post by Russty of Oz on 2006-06-18
Something has gone wrong.  In **Places > Computer **I no longer have the windows partition showing up.  It was there and I was able to access its data from Ubuntu but now I only have **Floppy, CD/DVD drive and Filesystem**.  I tried to do the whole process again but it says it is already there.  

Where can I find Windows?

Russty

---

### Post by aysiu on 2006-06-18
Bookmark it in Nautilus. It'll show up in Places, then.

---

### Post by Russty of Oz on 2006-06-18
Sorry, I don't know how to do that.  What and where is Nautilus?

---

### Post by aysiu on 2006-06-18
[QUOTE=Russty of Oz]Sorry, I don't know how to do that.[/QUOTE] This is how you do it.

---

### Post by Russty of Oz on 2006-06-18
The problem is I cant find Windows at all.  Where could it have gone?

---

### Post by aysiu on 2006-06-18
I don't know. If it's in the /etc/fstab, it should automount.

Can you post the output of these three commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by Russty of Oz on 2006-06-18
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8094    65015023+   7  HPFS/NTFS
/dev/hda2            8095        9822    13880157   83  Linux
/dev/hda3            9823        9964     1140615    5  Extended
/dev/hda5            9823        9964     1140583+  82  Linux swap / Solaris

dapper@dapper-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              14G   11G  2.1G  84% /
varrun                379M   92K  379M   1% /var/run
varlock               379M  4.0K  379M   1% /var/lock
udev                  379M  184K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   19M  361M   5% /lib/modules/2.6.15-25-386/volatile
/dev/hda1              63G   32G   31G  52% /windows

dapper@dapper-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0

---

### Post by aysiu on 2006-06-18
I don't know why it would be not appearing... Everything looks in good order. It appears to be /dev/hda1: ```
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
**/dev/hda1 * 1 8094 65015023+ 7 HPFS/NTFS**
/dev/hda2 8095 9822 13880157 83 Linux
/dev/hda3 9823 9964 1140615 5 Extended
/dev/hda5 9823 9964 1140583+ 82 Linux swap / Solaris
```

It appears to be mounted: ```
Filesystem Size Used Avail Use% Mounted on
/dev/hda2 14G 11G 2.1G 84% /
varrun 379M 92K 379M 1% /var/run
varlock 379M 4.0K 379M 1% /var/lock
udev 379M 184K 379M 1% /dev
devshm 379M 0 379M 0% /dev/shm
lrm 379M 19M 361M 5% /lib/modules/2.6.15-25-386/volatile
**/dev/hda1 63G 32G 31G 52% /windows**
```

And it appears to be properly entered into your /etc/fstab: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
**/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0**
``` Can you do one more thing for me? Can you type the output of these commands? ```
cd /windows
ls -a
```

---

### Post by Russty of Oz on 2006-06-18
dapper@dapper-desktop:~$ cd /windows
dapper@dapper-desktop:/windows$ ls -a
.             CONFIG.SYS              Enlish.lng    NVIDIA
..            debug.log               hiberfil.sys  pagefile.sys
AUTOEXEC.BAT  Documents and Settings  IO.SYS        Program Files
boot.ini      DVD                     MSDOS.SYS     RECYCLER
BOOTWIZ       dvdfabexpress_burn.log  NTDETECT.COM  System Volume Information
bootwiz.sys   DVDFabExpress_Temp      ntldr         WINDOWS

---

### Post by aysiu on 2006-06-18
So, you're good. Windows is mounted, and all the normal Windows stuff appears.

I'm not sure what the problem is. Click on Places. Then click on Home Folder.

The Nautilus file manager will open.

Press Control-L and type ```
/windows
``` You should see Windows. Then you can bookmark it to have it appear in the Places menu.

---

### Post by Russty of Oz on 2006-06-18
[QUOTE=aysiu]So, you're good. Windows is mounted, and all the normal Windows stuff appears.

I'm not sure what the problem is. Click on Places. Then click on Home Folder.

The Nautilus file manager will open.

Press Control-L and type ```
/windows
``` You should see Windows. Then you can bookmark it to have it appear in the Places menu.[/QUOTE]

[B]That did it!  :D 

Thanks for all the help, I can't understand why it disapeared, it used to be there.  Still all is well now.

Thanks again!

Russty[/B]  :)

---

