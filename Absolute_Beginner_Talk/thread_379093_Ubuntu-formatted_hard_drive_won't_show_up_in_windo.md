---
title: "Ubuntu-formatted hard drive won't show up in windows"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by have2p on 2007-03-08
I used the LiveCD to format my 250bg drive and install Ubuntu on it. Worked great. (my first Linux experience evar!)

Now, however, the drive will not show up in Vista. When I go to device manager, I can see it there and it says that its working fine. But when I go to My Computer, it's nowhere to be found. 

How can I get this drive to show up in windows?

---

### Post by Malac on 2007-03-08
> **have2p said:**
> I used the LiveCD to format my 250bg drive and install Ubuntu on it. Worked great. (my first Linux experience evar!)

Now, however, the drive will not show up in Vista. When I go to device manager, I can see it there and it says that its working fine. But when I go to My Computer, it's nowhere to be found. 

How can I get this drive to show up in windows?
Windows by default has no driver to read ext3fs system drives. You will need to install a driver, there are a few about. I recommend ext2 IFS which is available for download here:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Hope this helps.

---

### Post by have2p on 2007-03-08
Looks perfect, but will it work for vista?

---

### Post by rajeshgautam on 2007-03-08
refer to this thread [http://ubuntuforums.org/showthread.php?t=358241](http://ubuntuforums.org/showthread.php?t=358241)

---

### Post by go2dell on 2007-03-08
Device Manager shows you physical disks, or what the computer hardware can find.  When you're using *My Computer* you're looking at disk partitions, rather than whole disks.

The problem is that, unlike Linux distributions which are all smart enough to recognize, read, and even write many different kinds of filesystems, Windows is a complete idiot.  This is by design, as Microsoft doesn't see any point in using anything but their own filesystems, therefore why could you possibly want to read them?  :-)  NTFS and FAT are fine, but anything else will be utterly meaningless to Windows.

If you allowed the Ubuntu installer to do its own thing, then your partition is an ext3 ("third extended") filesystem.  This means it's also an ext2 filesystem, since ext3 is just ext2 with a journal.  So how can you read it?  Here's [one method]("http://www.fs-driver.org/download.html").  Will it work?  I don't know, as I've never bothered to try to read an ext3 partition from Windows.

Good luck!

---

### Post by Archmage on 2007-03-08
Or you use the ntfs-3g driver than you can read and write NTFS in both OS.

Or you use a swap partition (FAT32 if you don't have files larger 2 GB) to exchange data between both OS.

---

### Post by have2p on 2007-03-08
I'm running Vista 64bit. Ext2IFS says that it doesn't support 64 bit processors (so I haven't tried it) and I cannot seem to get Ext2fsd to work at all. It installs fine and starts up fine but there is still no hard drive to be seen in windows. I'm not sure what I'm supposed to do.

*EDIT* It turns out that it won't let me install the driver because its not digitally signed. Sweet. I booted up with F8 a selected "disable driver signature checking" but it still gives me the same error: "This driver is not digitally signed." What gives?

---

### Post by have2p on 2007-03-08
Does anyone know why it won't let me disable digital signature requirements?

---

### Post by dstew on 2007-03-08
Unfortunately, you cannot load an unsigned kernel-module into Window Vista. This is a security feature. Even if you have administrative privleges, you cannot load an unsigned driver. Whoever publishes the driver must obtain a signature certificate from Microsoft in order for the driver to load. Microsoft is doing this as a security measure. They don't want anyone to publish a module that might create a security hole when installed in their systems. The certificate makes it possible to track back to the source of any module, in case they have problems, and get it fixed. See the White Paper on module signing.
[http://www.microsoft.com/whdc/system/platform/64bit/kmsigning.mspx](http://www.microsoft.com/whdc/system/platform/64bit/kmsigning.mspx)

---

### Post by Ptero-4 on 2007-03-08
[QUOTE=have2p]Does anyone know why it won't let me disable digital signature requirements?[/QUOTE]

Simple. Because Windoze "Vista" is designed to betray it's users and obey only M$.

---

