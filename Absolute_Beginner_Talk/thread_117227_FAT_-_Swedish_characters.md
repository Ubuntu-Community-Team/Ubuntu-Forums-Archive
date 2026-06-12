---
title: "FAT - Swedish characters?"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by Garyu on 2006-01-14
Well, I haven't upgraded from 5.04 to 5.10 yet, but I don't think it matters regarding this question.

I have a dual-boot system with WinXP and Ubuntu 5.04 64-bit version for my AMD64 processor. It works great in most respects, but I have one problem that I haven't figured out yet. 

I use a 100GB FAT partition to share files between OS:s, like MP3s and documents. However, while Ubuntu will list all of the disc content, files and folders created in WinXP containing swedish characters returns a message that the file or folder cannot be opened. Rather annoying since I have to keep switching back to windoze and rename files or folders when I forget to use "a" instead of "å" or "ä". I imagine that this is because Ubuntu uses a different character map, but I just can't figure out how to change to the correct one, or even which caracter map WinXP is using. :???: 

Anyone who knows how to fix this, I would be very grateful.

---

### Post by Mr_Grieves on 2006-01-14
You should use the iso8859-1 keyboard map.

Read more here:
[http://www.ubuntulinux.se/node/82](http://www.ubuntulinux.se/node/82)

---

### Post by Garyu on 2006-01-16
My fstab looks like this:

```
/dev/hda5       /FAT            vfat    iocharset=iso8859-1,umask=000	0	0
```

but I still have errors reading files with åäö (swedish characters)...

---

### Post by pertti on 2006-01-16
I have Spanish characters on my FAT and NTFS partitions, and I solved that problem with the utf8 flag:

```
/dev/hda5       /media/hda5     vfat    rw,utf8,umask=0000        0       0
```

Give it a try.

---

### Post by Garyu on 2006-01-16
nope... that did not do the trick. instead of å/ä/ö I get "?" in the file names.

One strange thing though... I can't open any files with swedish caracters... but I can send them with GAIM to users on my contact list??? Weird... But that is not the problem, the problem is that Linux and Windows speak different languages. One would think that this should be easier than this to solve...

---

### Post by Garyu on 2006-01-17
Come on you guys... Ubuntu is supposed to be the one distro you can run with any language...

Is there any way for me to just "reformat" my FAT partition to force WinXP to use a certain character set?

---

### Post by Karma_Police on 2006-01-17
try with "nls=utf8" in the options


something like:
> /dev/hda1       /media/hda1     vfat    rw,nls=utf8,user        0       0

unmount and mount again, and everything should work.

---

### Post by Garyu on 2006-01-18
[QUOTE=Karma_Police]try with "nls=utf8" in the options


something like:


unmount and mount again, and everything should work.[/QUOTE]

I tried that, and this is what I got as a reply:

```
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
and "dmesg | tail" says: FAT: Unrecognized mount option "nls=utf8"

---

### Post by Garyu on 2006-01-18
Well, once again I am amazed at how something small can make a huge difference. IT'S WORKING! =))

/dev/hda5       /FTP            vfat    utf8,umask=000	0	0

this is what my /etc/fstab looks like now. I just trimmed it a bit. I guess it is best to provide as little information as possible. Because I have tried "utf8" in the options section I don't know how many times with different combinations, and it has never worked before. And now, ka-ching. :)

Thank you all for your help though. Even though I figured it out by myself this time. :cool: Or maybe Linux just decided to wake up from all the rustle made by "nls=utf8", who knows?

---

### Post by Karma_Police on 2006-01-19
Humm... Sorry. nls is a ntfs option. "iocharset=utf8" seems to be the correct option for vfat.

But, since you got it working, no need to mess arround any more. :)

---

