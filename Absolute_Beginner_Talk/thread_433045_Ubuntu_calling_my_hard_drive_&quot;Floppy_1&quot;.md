---
title: "Ubuntu calling my hard drive &quot;Floppy 1&quot;?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by David the Gnome on 2007-05-04
I don't have a floppy drive hooked up to this system. For some reason it has called my main hard drive "Floppy 1" and I can't open it or rename it. Does Ubuntu require a floppy drive to be hooked up? If I hook up my old floppy drive will it fix the problem or will I then have a Floppy 1 and Floppy 2 (Only one of which being an actual floppy drive)?

I'm running the AMD64 version of Ubuntu.

Quick edit: I originally had two hard drives hooked up, only the 300GB drive is hooked up right now.

---

### Post by compmodder26 on 2007-05-04
So if you go to Places->Home Folder, you can't view anything?

BTW, glad to see a fellow Lexingtonian using Ubuntu. :)

---

### Post by David the Gnome on 2007-05-04
I can open the Places-> Home Folder.

On the Places-> Computer screen my hard drive is called "Floppy 1". I can't rename it or open it or do anything with it. Any ideas why it's doing that?

---

### Post by compmodder26 on 2007-05-04
In Places->Computer, do you see "Filesystem"?

---

### Post by David the Gnome on 2007-05-04
Yes this is what I can see:

Floppy 1 
CD-RW/DVD+/-RW Drive
Filesystem

---

### Post by compmodder26 on 2007-05-04
Filesystem is your hard drive.

---

### Post by David the Gnome on 2007-05-04
Ok, thanks. What is this 253.7 GB Floppy 1 drive?

---

### Post by compmodder26 on 2007-05-04
:confused: I couldn't tell you.  That is a bit odd.  Open up a terminal and type "cat /etc/fstab" and post the output.

---

### Post by David the Gnome on 2007-05-04
Ok, gimme a sec to come up with a schnazzy way to copy that from my Linux box to my Vista machine :P

---

### Post by David the Gnome on 2007-05-04
# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# /dev/hda1 
UUID=13c31eea-9a62-4aba-8518-a485b2832b40 /               ext3    defaults,errors=remount-ro 0       1 
# /dev/hda5 
UUID=7ca378f7-c90c-43a6-95ab-c1572ef3dcb1 none            swap    sw              0       0 
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

If that makes any sense to you, it certainly doesn't to me lol.

---

### Post by compmodder26 on 2007-05-04
Interesting how Ubuntu seems to think you have a floppy drive (note the line that reads "/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0").  Simple/Permanent fix is to place a "#" in front of that line.  Here is how to edit it:

First, open it in a text editor:
```
gksudo gedit /etc/fstab
```

Place the "#" in front of the /dev/fd0 line.

Save the file.

Then in the terminal again, type:
```
sudo mount -a
```

Then look at Places->Computer again.  The floppy drive should be gone.

---

### Post by Churnd on 2007-05-04
Another fellow kentuckian!  Welcome!

I'd also like to see the output of:

```
fdisk -l
```

I noticed you have the same Mobo I do... do you have "emulate floppy" enabled in the BIOS?  That might be causing the confusion with Ubuntu.

---

### Post by compmodder26 on 2007-05-04
> **compmodder26 said:**
> Interesting how Ubuntu seems to think you have a floppy drive (note the line that reads "/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0").  Simple/Permanent fix is to place a "#" in front of that line.  Here is how to edit it:

First, open it in a text editor:
```
gksudo gedit /etc/fstab
```

Place the "#" in front of the /dev/fd0 line.

Save the file.

Then in the terminal again, type:
```
sudo mount -a
```

Then look at Places->Computer again.  The floppy drive should be gone.

Okay, scratch that.  I attempted that on my own machine just a second ago and didn't do anything.  Churnd's idea sounds logical.  If neither work, then I guess just ignore it?  It isn't hurting anything.

---

### Post by David the Gnome on 2007-05-04
> **Churnd said:**
> Another fellow kentuckian!  Welcome!

I'd also like to see the output of:

```
fdisk -l
```

I noticed you have the same Mobo I do... do you have "emulate floppy" enabled in the BIOS?  That might be causing the confusion with Ubuntu.

I'm using the "optimized defaults" so I don't think so. I looked around in the bios and didn't see any option for "emulate floppy". I've been spending the past hour just trying to install the nvidia drivers for my video card (unsuccessfully).

I'll get that fdisk screen for you in a sec.

---

### Post by David the Gnome on 2007-05-04
Ok, fdisk -1 gives me "fdisk: invalid option -- 1". Then it gives me some Usage options bellow that.

---

### Post by Churnd on 2007-05-05
> **David the Gnome said:**
> Ok, fdisk -1 gives me "fdisk: invalid option -- 1". Then it gives me some Usage options bellow that.

That's an L, not a 1:

```
fdisk -l
```

I'm on my machine at home now, and mine reports 12.1 GB.  I have emulate floppy enabled in BIOS.  I promise, it's there... you just have to dig for it.

---

### Post by David the Gnome on 2007-05-05
Ok, this is what fdisk -l gives me:

david@David-Linux:~$ fdisk -l
david@David-Linux:~$ 

Nothing =/

---

### Post by Lucifiel on 2007-05-05
> **David the Gnome said:**
> Ok, this is what fdisk -l gives me:

david@David-Linux:~$ fdisk -l
david@David-Linux:~$ 

Nothing =/

Erm, you need to run "sudo fdisk -l" to get the output.

---

### Post by Najand on 2007-05-05
Comment the line starting with /dev/fd0 with a "#" mark. Then restart your computer and see if anything has changed or not.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=13c31eea-9a62-4aba-8518-a485b2832b40 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5
UUID=7ca378f7-c90c-43a6-95ab-c1572ef3dcb1 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
[COLOR="Blue"]# /dev/fd0 /media/floppy0 auto rw,user,noauto 0 0[/COLOR]

```

---

### Post by David the Gnome on 2007-05-05
> **Lucifiel said:**
> Erm, you need to run "sudo fdisk -l" to get the output.

My bad.. :p

```
Disk /dev/hda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       35733   287025291   83  Linux
/dev/hda2           35734       36483     6024375    5  Extended
/dev/hda5           35734       36483     6024343+  82  Linux swap / Solaris

```

---

### Post by David the Gnome on 2007-05-05
> **Najand said:**
> Comment the line starting with /dev/fd0 with a "#" mark. Then restart your computer and see if anything has changed or not.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=13c31eea-9a62-4aba-8518-a485b2832b40 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5
UUID=7ca378f7-c90c-43a6-95ab-c1572ef3dcb1 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
[COLOR="Blue"]# /dev/fd0 /media/floppy0 auto rw,user,noauto 0 0[/COLOR]

```

I hate to sound like a total noob but how do I go about doing that?

---

### Post by Najand on 2007-05-05
Open gnome editor with root privilages by opening a terminal and type:
```

gksu gedit /etc/fstab

```
And push Enter.

---

### Post by Lucifiel on 2007-05-05
Remember to backup your fstab file before you edit it, though.

You can do that by copying it to another directory.

---

### Post by David the Gnome on 2007-05-05
Ok, I commented the line about the floppy drive and now it's gone from the list. Is there some way to get it to display my hard drive now? I think what I really need to do it find some way to tell it that my hard drive is actually a hard drive and not a floppy drive.

[IMG]http://img375.imageshack.us/img375/7978/compbrowseyx0.png[/IMG]

---

### Post by Churnd on 2007-05-05
> **David the Gnome said:**
> Ok, I commented the line about the floppy drive and now it's gone from the list. Is there some way to get it to display my hard drive now? I think what I really need to do it find some way to tell it that my hard drive is actually a hard drive and not a floppy drive.

[IMG]http://img375.imageshack.us/img375/7978/compbrowseyx0.png[/IMG]

"Filesystem" is your hard drive.  Unless you mean get it to display on the desktop?

---

