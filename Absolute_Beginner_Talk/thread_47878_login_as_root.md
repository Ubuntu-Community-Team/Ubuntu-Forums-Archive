---
title: "login as root?"
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by Snitz on 2005-07-10
I just installed ubuntu on a new partition that I just made using partition magic
but the thing is, when I run "pppoeconf" in the terminal, it tells me:

```
login as a root to be able to do this
```

I don't know what this means, and how can I login as root?

and another thing, I'm not being able to access drive C and D. ubuntu is installed on drive G. so how can I access the other drives?

---

### Post by Ride Jib on 2005-07-10
to do anything as "root" in ubuntu, you need to use the "sudo" command (or "gksudo" for graphical apps). For example: "sudo pppoeconf" or "gksudo pppoeconf"

As for accessing your Windows partitions... first make a directory to "mount" the drives to... 
```
sudo mkdir /media/windows
```
Then modify your fstab file
```
sudo gedit /etc/fstab
```
At the very end add the following line:
```

/dev/hda1       /media/windows  ntfs    umask=0222      0       0

```
Where hda1 is your windows partition. If you have 2 drives you want mounted, you will have to make a separate mount point for each of them (e.g. /media/windows/c_drive and /media/windows/d_drive) and 1 line for each in the /etc/fstab file.

Once the fstab file is modified, reboot. Then browse to the directory you mounted the drive to ..

**Edit:** Here is a reference link that should cover everything I just mentioned: [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by Snitz on 2005-07-10
I will try what u suggested and get back at you!!

---

### Post by Snitz on 2005-07-10
this is exactly what I wrote:

```
/dev/hda1       /media/windows  ntfs    umask=0222      0       0
/dev/hda1       /media/windows/c_drive  ntfs    umask=0222      0       0
/dev/hda1       /media/windows/d_drive  ntfs    umask=0222      0       0
```

I rebooted and nothing happened
my drive D is ntfs
my drive C is FAT32
where did I go wrong?

---

### Post by Bite_me_Bill on 2005-07-10
Go into your system folder then go to the media directory and see if they are there.

---

### Post by Ride Jib on 2005-07-10
For your FAT partition, you need to use this instead:

```
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
```

Also, hda1 is only one partition. You need to figure out which mount is associated with which drive.

Here is what my /etc/fstab looks like

```

/dev/hda2       /boot           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /storage        ext3    defaults        0       0
/dev/hda1       /media/windows  ntfs    umask=0222      0       0

```
as you can see... hda1 is only listed once.

---

### Post by Snitz on 2005-07-10
[QUOTE=Bite_me_Bill]Go into your system folder then go to the media directory and see if they are there.[/QUOTE]
 there are many folders but all empty:

cdrom
cdrom0
cdrom1
floppy
floppy0
windows

all empty

---

### Post by Ride Jib on 2005-07-10
ok, post up your /etc/fstab on here, and also the results of this:

```
sudo fdisk -l
```

---

### Post by Snitz on 2005-07-10
[QUOTE=Ride Jib]ok, post up your /etc/fstab on here, and also the results of this:

```
sudo fdisk -l
```[/QUOTE]
 this is not working :\
the command u gave me ain't working

---

### Post by aysiu on 2005-07-10
Can you post your /etc/fstab?

And can you post what appears after you type *df* into the terminal?

---

### Post by Snitz on 2005-07-10
[QUOTE=aysiu]Can you post your /etc/fstab?

And can you post what appears after you type *df* into the terminal?[/QUOTE]
 I don't know how to post my /etc/fstab
the commands ur giving me ain't working

I'm being able to see my drive C, but all "read only"
I can't write in it!!
but drive D is still missing!

---

### Post by Ride Jib on 2005-07-10
in console:
```
 more /etc/fstab
```
use mouse to highlight, right click, copy the output
open web browser
right click in reply box > paste.
submit post.

---

### Post by aysiu on 2005-07-10
[QUOTE=Snitz]
the commands ur giving me ain't working[/QUOTE] When you say a command "ain't working," can you be more specific? What happens when you type it into the terminal? Can you copy and paste the output?

---

### Post by Snitz on 2005-07-10
> use mouse to highlight, right click, copy the output
open web browser
right click in reply box > paste.
submit post.
u want me to copy/paste it into my browser or the terminal ?

> When you say a command "ain't working," can you be more specific? What happens when you type it into the terminal? Can you copy and paste the output?
nothing happens, a quick terminal window shows up and disappear in matter of seconds

I know converted my C drive into NTFS 
so both Drive C and D are ntfs

what should I do?

---

### Post by Snitz on 2005-07-10
[QUOTE=Snitz]u want me to copy/paste it into my browser or the terminal ?


nothing happens, a quick terminal window shows up and disappear in matter of seconds

I know converted my C drive into NTFS 
so both Drive C and D are ntfs

what should I do?[/QUOTE]
 it seems that NTFS are read only while FAT32 are read/write, is that true?

---

### Post by bored2k on 2005-07-10
[QUOTE=Snitz]it seems that NTFS are read only while FAT32 are read/write, is that true?[/QUOTE]
Yes. I could have said maybe r/w also, but for your own sake, that is true. NTFS is read only, FAT32 allows r/w mojo power.

---

### Post by Snitz on 2005-07-10
[QUOTE=bored2k]Yes. I could have said maybe r/w also, but for your own sake, that is true. NTFS is read only, FAT32 allows r/w mojo power.[/QUOTE]
 so I better reconvert both C and D to FAT32, right?
but what should I do after I convert?

just the regular mount controls that are mentioned on ubuntuguide ?

---

### Post by bored2k on 2005-07-10
[QUOTE=Snitz]so I better reconvert both C and D to FAT32, right?
but what should I do after I convert?

just the regular mount controls that are mentioned on ubuntuguide ?[/QUOTE]
Yeah you should if you want RW support.
Just follow ubuntuguide and you'll be fine ;). I've got my fat partitions working wonders and I got my code there (I didn't like the utf part, but that's just me, follow the guide tidily),.

---

### Post by Snitz on 2005-07-10
I will do the conversion when I fix my other problem

thx mate!

---

### Post by Snitz on 2005-07-10
I've converted all my partitions to NTFS
hda3 and hda4 are used by ubuntu
hda1 and hda2 are supposed to be drive C and D that I can't access

so I added the following in fstab:

```
/dev/hda1       /media/windows  ntfs    umask=0222      0       0
/dev/hda2       /media/windows  ntfs    umask=0222      0       0
/dev/hda1       /media/windows/c_drive  ntfs    umask=0222      0       0
/dev/hda2       /media/windows/d_drive  ntfs    umask=0222      0       0
```

is it too much?
of course it's wrong, so please tell me where did I go wrong and how to fix it?

---

### Post by aysiu on 2005-07-10
Well, it looks as if the two are in conflict with each other. A partition has to be either NTFS or FAT--it cannot be both.

Now when you say the commands we're giving you "ain't working," where are you putting these commands? No new terminal should launch and shut down right away. You should be putting these commands *in* the terminal.

Let's not assume anything.
Okay. Step by step.

1. All right. So in your panel, there should be system, applications, and places, right? 
2. Go to Applications. A menu should pop up or drop down. 
3. In that menu, you'll see a submenu called "System Tools." 
4. Within that menu, there should be something call "Terminal." Select that one.
5. A new window should open that looks a bit like DOS. The screen should be more or less blank except for this: 

*snitz@ubuntu:~$*

I'm assuming, of course, that your Ubuntu username is snitz. It could be whatever. It doesn't matter. When people say "Type this in the terminal" or "Enter this in the console," the *snitz@ubuntu:~$* is where you're supposed to be entering these things.

In other words, your terminal should be completely blank except for these words:

***snitz@ubuntu:~$**sudo fdisk -l*

And the part that's in bold isn't something you type. It'll just be there. What you type goes after the part that's in bold. That *-l* is a hyphen and a lower-case L (it isn't a capital i).

When I enter *sudo fdisk -l* at this prompt, I'm then prompted for my password. After that, this comes up:
[i]
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1911    15350076    7  HPFS/NTFS
/dev/hda2            1912       18494   133202947+   f  W95 Ext'd (LBA)
/dev/hda3   *       18495       19457     7735297+  83  Linux
/dev/hda5            1912       18362   132142626    b  W95 FAT32
/dev/hda6           18363       18494     1060258+  82  Linux swap / Solaris
[/i]

We can't know whether your /dev/hda1 is NTFS or FAT or whatever unless you type in this command and show us what comes up. You can copy stuff from the terminal by highlighting it, right-clicking, selecting *copy*, then putting your cursor into one of these posts, right-clicking, and selecting *paste*.

---

### Post by Snitz on 2005-07-11
this is it:

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *        1006        2551    12418213+   c  W95 FAT32 (LBA)
/dev/hda2            2552        4998    19655527+   f  W95 Ext'd (LBA)
/dev/hda3               1         959     7703136   83  Linux
/dev/hda4             960        1005      369495   82  Linux swap / Solaris
/dev/hda5            2552        4998    19655496    b  W95 FAT32

Partition table entries are not in disk order

---

### Post by aysiu on 2005-07-11
[QUOTE=Snitz]
/dev/hda1   *        1006        2551    12418213+   c  W95 FAT32 (LBA)
/dev/hda5            2552        4998    19655496    b  W95 FAT32 [/QUOTE] Well, based on that, and according to these instructions

[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

You should probably add these two lines to your /etc/fstab file:

/dev/hda1       /media/windows_c  vfat    iocharset=utf8,umask=000   0       0
/dev/hda5       /media/windows_d  vfat    iocharset=utf8,umask=000   0       0

Make sure you actually create the /media/windows_c and /media/windows_d folders, too!

All the instructions are in here:
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

---

### Post by Snitz on 2005-07-11
so I should create these to commands:

sudo mkdir /media/windows_c
sudo mkdir /media/windows_d

and then add the 2 lines into fstab file!!

right?

---

### Post by Ride Jib on 2005-07-11
[QUOTE=Snitz]so I should create these to commands:

sudo mkdir /media/windows_c
sudo mkdir /media/windows_d

and then add the 2 lines into fstab file!!

right?[/QUOTE]

yes. Add those lines to your *original* /etc/fstab. Remove any changes you have made since you started this thread.

Also, instead of rebooting your machine, you can issue the following command in a terminal:
```
sudo mount -a
```

---

### Post by Snitz on 2005-07-11
[QUOTE=Ride Jib]yes. Add those lines to your *original* /etc/fstab. Remove any changes you have made since you started this thread.

Also, instead of rebooting your machine, you can issue the following command in a terminal:
```
sudo mount -a
```[/QUOTE]
 I did it and it worked
by all files are read only :confused:

---

### Post by kvidell on 2005-07-11
[QUOTE=Snitz]I did it and it worked
by all files are read only :confused:[/QUOTE]
 NTFS _MUST_ be ReadOnly.
Write support in Linux for NTFS is very poor.
Do _NOT_ try to write to anything NTFS.

Also; you shouldn't try to convert it from NTFS -> FAT, it will erase all of your data when you do this.
- Kev

---

### Post by Snitz on 2005-07-11
all my drives all fat32
and when I converted, not a single file got lost
but I can only read on fat32
how come?

---

