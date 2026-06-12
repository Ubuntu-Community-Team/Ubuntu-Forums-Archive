---
title: "Mounting a Windows partition after installation (Solved)"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Antexter on 2006-11-01
So how would i go about accessing my windows partition? (i've installed it now)

---

### Post by aysiu on 2006-11-01
> **Antexter said:**
> So how would i go about accessing my windows partition? (i've installed it now)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Antexter on 2006-11-01
ahhh, i dont get it
> 
  GNU nano 1.3.10             File: /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0



                                [ Read 6 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

what do i do at that point :S

---

### Post by aysiu on 2006-11-01
What was the output of ```
sudo fdisk -l
```?

---

### Post by Antexter on 2006-11-01
no it was 
```
sudo nano /etc/fstab
```

---

### Post by aysiu on 2006-11-01
I know, but we can't know what to *add* to the /etc/fstab file until we see the output of ```
sudo fdisk -l
``` That lists the partition table.

---

### Post by Antexter on 2006-11-01
Oh sorry
```
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        3582       19733   129740908+   7  HPFS/NTFS
/dev/sda2             151        3581    27559507+  83  Linux

Partition table entries are not in disk order

```

---

### Post by aysiu on 2006-11-01
I'll give you the commands to copy and paste.

Whenever possible, copy and paste--do not retype. Retyping takes longer and is more prone to errors.

Make a mount point: ```
sudo mkdir /media/windows
``` Edit your /etc/fstab ```
sudo nano -B /etc/fstab
``` Add this line: ```
/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0
``` Save (Control-x, y, Enter). Remount ```
sudo mount -a
```

---

### Post by Antexter on 2006-11-01
I done that ```
mike@mike-desktop:~$ sudo mkdir /media/windows
Password:
mkdir: cannot create directory `/media/windows': File exists
mike@mike-desktop:~$ sudo nano -B /etc/fstab
mike@mike-desktop:~$ sudo mount -a
mike@mike-desktop:~$
```
When i click on it says cannont mount.
[http://img170.imageshack.us/img170/5730/screenshot1za9.png](http://img170.imageshack.us/img170/5730/screenshot1za9.png)

---

### Post by aysiu on 2006-11-01
> **Antexter said:**
> I done that ```
mike@mike-desktop:~$ sudo mkdir /media/windows
Password:
mkdir: cannot create directory `/media/windows': File exists
mike@mike-desktop:~$ sudo nano -B /etc/fstab
mike@mike-desktop:~$ sudo mount -a
mike@mike-desktop:~$
```
When i click on it says cannont mount.
[http://img170.imageshack.us/img170/5730/screenshot1za9.png](http://img170.imageshack.us/img170/5730/screenshot1za9.png)
Don't access it through the Computer menu. Go to /media/windows through the file browser.

---

### Post by Antexter on 2006-11-01
Theirs nothing in the windows folder.
[http://img155.imageshack.us/img155/9532/screenshotwindowsfilebrso0.png](http://img155.imageshack.us/img155/9532/screenshotwindowsfilebrso0.png)

---

### Post by aysiu on 2006-11-01
All right. Let's take it from the top and see if we missed a step along the way, shall we?

Can you--now that we've done everything (or what we think is everything)--post the output of these commands? ```
cat /etc/fstab
df -h
sudo fdisk -l
```

---

### Post by Antexter on 2006-11-01
```
mike@mike-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
mike@mike-desktop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda2              26G  2.0G   23G   9% /
varrun                252M   92K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  144K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-26-386/volatile
/dev/sdb              245M  202M   44M  83% /media/usbdisk
mike@mike-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        3582       19733   129740908+   7  HPFS/NTFS
/dev/sda2             151        3581    27559507+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 257 MB, 257802752 bytes
8 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 496 * 512 = 253952 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     1568823     3870254   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(1568822, 3, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(3870253, 0, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      340100     4243383   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(340099, 6, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(4243382, 4, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?     3769923     7673205   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(3769922, 2, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(7673204, 7, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?     5817906     5818018       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(5817905, 4, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(5818017, 3, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
mike@mike-desktop:~$

```
Hope that all makes sense to you all jargon to me.

---

### Post by aysiu on 2006-11-01
You're missing a line in your /etc/fstab. There's nothing in there referring to your NTFS partition.

This is what it looks like now: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
``` This is what it should look like ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
**/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0**
``` After that, you do the ```
sudo mount -a
``` command to have the change take effect.

I know this all looks like gibberish to you, but there's a logic to it.

In order for your Windows partition to be accessible, it has to appear somewhere. This is what we call a mount point, which is really just a folder. In this case, that folder is /media/windows. Really, we could have made it anything. It could have been /windows. It could have been /home/*username*/windows. It could have been /mnt/extrafiles. The point is that there's *somewhere* you have to look to actually see your windows file. The ```
sudo mkdir /media/windows
``` command creates that folder.

Then, the command ```
sudo fdisk -l
``` lets us know the physical location of the Windows partition and its filesystem. So from that output, we learn that the Windows partition lives at /dev/sda1 and that its filesystem is NTFS. This comes in handy when we edit the /etc/fstab file.

We edit the /etc/fstab file to tell Ubuntu, "Hey, we want this Windows partition to show up, okay?" So we put in the line ```
/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0
``` Without going into all the details of the numbers involved, the basic gist is this: Mount this physical location (/dev/sda1) to this folder (/media/windows). The physical location is of this filesystem (ntfs), and I want to make sure anyone can read it (umask=0222).

Once you save the file, you actually have to mount it the first time (next time it will be automatically mounted at boot-up). That's what the ```
sudo mount -a
``` command does.

Does that make any more sense to you?

---

### Post by Antexter on 2006-11-01
Sorry i dont really understand you.
```
sudo nano -B /etc/fstab
```
You mean when i put that in :s ?

---

### Post by aysiu on 2006-11-01
> **Antexter said:**
> Sorry i dont really understand you.
```
sudo nano -B /etc/fstab
```
You mean when i put that in :s ?
```
sudo nano -B /etc/fstab
``` is the command that allows you to edit the /etc/fstab file.

/etc is the directory the fstab file lives in.
nano is a text editor.

Translation:
**sudo** - with administrative privileges (since this is a system-wide file)
**nano** - edit with the Nano text editor
**-B** - and make a back-up copy before I edit it
**/etc** - within the /etc directory
**fstab** - the fstab file

Does that make more sense now?

After you enter that command, you can add in the appropriate line: ```
/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0
```

To save the file after you edit it, press Control-X, Y, and then Enter.

---

### Post by Antexter on 2006-11-01
Absolutly excelent, its working.
And now i understand some more commands :D.

Thanks for the help!

---

### Post by aysiu on 2006-11-01
No problem.

I hope Ubuntu fixes this soon. Knoppix and Mepis have been doing one-click mounting of partitions (with the proper permissions) for years...

---

### Post by Antexter on 2006-11-02
Yeah thats why i carry knoppix around with me very handy if someones pc messes up and they cant get their stuff :D

---

