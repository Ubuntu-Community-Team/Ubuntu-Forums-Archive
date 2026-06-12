---
title: "A little help for a total newbie please?"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by essenby on 2006-12-12
Hi,

I wonder if someone out there can give a moment of their time to help a total newbie with 2 seemingly enormous challenges with Ubuntu?  I am using Ubuntu 6.10 and running the Live CD version to check out compatibility, ease of use etc and have 2 main issues.

1.  I would like to be able to mount my windows partitions so that I can read/use the media files I have already stored.  I have read through [psychocats guide]("http://www.psychocats.net/ubuntu/mountwindows") and although it makes sense, isn't there another way?  Maybe a GUI method?  In other distros I've looked at (PC LinuxOS for example) this is extremely simple via a "point and click" interface.  I thought Ubuntu was touted as the "easiest to use"?

2. My ancient Dell laptop uses a wireless card with Broadcom chipset.  In PCLOS I have managed to get this working perfectly using ndiswrapper.  My Linspire Live CD picks this up automatically (albeit by using ndiswrapper( and I can us it "out of the box".  However, Ubuntu does not even recognise ndiswrapper as a command and it would appear that I  need to make/compile and install it before I can use it. Again - not exactly ammunition for the "easy to use" tag.

Are my problems simply because the Live CD version is a "cut down" version or will I face similar issues if install?  If it is a cut down version, is there another, more representative version I can try.  Otherwise, the Live CD does not really give a realistic impression of the final install.

Thanks in advance

---

### Post by hyper_ch on 2006-12-12
If your windows partition is FAT32 it's also point and click. Somewhere in the Gnome System menu there should be an entry "disks" or something similar... in there you can r/w mount FAT32 very simple.
However if you have a ntfs windows partition I recommend mounting as read-only only. Writing to NTFS is still considered experimental and while 100s of people have no problems with it, in your case it may f*** everything up...

---

### Post by dorcssa on 2006-12-12
> **essenby said:**
> Hi,

I wonder if someone out there can give a moment of their time to help a total newbie with 2 seemingly enormous challenges with Ubuntu?  I am using Ubuntu 6.10 and running the Live CD version to check out compatibility, ease of use etc and have 2 main issues.

1.  I would like to be able to mount my windows partitions so that I can read/use the media files I have already stored.  I have read through [psychocats guide]("http://www.psychocats.net/ubuntu/mountwindows") and although it makes sense, isn't there another way?  Maybe a GUI method?  In other distros I've looked at (PC LinuxOS for example) this is extremely simple via a "point and click" interface.  I thought Ubuntu was touted as the "easiest to use"?

2. My ancient Dell laptop uses a wireless card with Broadcom chipset.  In PCLOS I have managed to get this working perfectly using ndiswrapper.  My Linspire Live CD picks this up automatically (albeit by using ndiswrapper( and I can us it "out of the box".  However, Ubuntu does not even recognise ndiswrapper as a command and it would appear that I  need to make/compile and install it before I can use it. Again - not exactly ammunition for the "easy to use" tag.

Are my problems simply because the Live CD version is a "cut down" version or will I face similar issues if install?  If it is a cut down version, is there another, more representative version I can try.  Otherwise, the Live CD does not really give a realistic impression of the final install.

Thanks in advance
1, I was a total newbie too when I encountered this problem, but I don't think it's too hard to mount it using the terminal. What's the big deal? You should accept that you cannot do everything with gui in linux. And there are a lot of guides out there, so it's really easy.

The live CD in not a "cut down" version, you see what'll you get.(At least with the basics.)

---

### Post by xyz on 2006-12-12
How about this:
[Mount NTFS Using Live CD]("http://www.ubuntuforums.org/showthread.php?p=1828429")
Let us know...
or
[Mounting a partition from Live CD [Resolved]]("http://ubuntuforums.org/showthread.php?p=1832604")

---

### Post by John E on 2006-12-12
This might be just specific to me - but if your Windows partitions are FAT32, I found them to be quite unreliable. They're easy enough to mount (I'll give you instructions if you want) but on my machine, they would ony work for a week or so, then I'd get errors like "only 1 or 2 FAT's allowed, not 246". After this, the Windows partitions became unmountable.

If you have a 2nd PC (laptop etc) I'd recommend that you use networking to share files. Networking seem to be very solid under Ubuntu.

---

### Post by xyz on 2006-12-12
You could also repartition your HD...if it's big enough:
1. NTFS
2. Fat 32 for file sharing between Windows and Ubuntu
3. Ubuntu
I have it set up that way and find it quite practical...in my case!

---

### Post by John E on 2006-12-12
You could read my tips for trouble free partitioning....

[http://ubuntuforums.org/showthread.php?t=317300]("http://ubuntuforums.org/showthread.php?t=317300")

---

