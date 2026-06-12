---
title: "Can't start Windows after reformating"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by _61_ on 2007-04-09
Hello all,

I used to have a partition with my old Windows system. I used to have it on /media/hda1.

I have a .tgz backup of this directory in an external drive.

I've tried to change the file sytem of this partition to ext3. I have reformated the partiton to ext3 and then I've restored all the files. I couldn't start Windows then...

So I reformated to fat32 again, restored the files again, and I still couldn't start Windows. When I'm in Grub and I select Windows, it says that it isn't a bootable drive.

Can someone help me, please?

---

### Post by jhenager on 2007-04-09
What it sounds like is that you are missing the boot sector on /media/hda1. The tgz backup probably has your files, but not this boot information.
The solution wouldn't be easy, but if you had access to another hard disk the same size or smaller, you could reinstall windows to that hard drive, then ghost or Partimage it, and then ghost or partimage that back to hda1. Then use your tgz backup to restore your files. 
There may be another way. Maybe someone else could make a suggestion.

---

### Post by dstew on 2007-04-09
You need to repair the Windows boot sector. Use the Windows recovery console, select the drive, and give the command **fixboot**. When you backed up the drive, it stored the files, but the boot sector is not a file, so it got erased when you reformatted. Restoring the files will not restore the boot sector.

Do not do **fixmbr**, because that will take away grub.

---

### Post by _61_ on 2007-04-09
Thanks dstew,

How can I access to the "Windows recovery console". I don't know what it is...

---

### Post by lamalex on 2007-04-09
you need your windows cd, boot to that and it will get take you to the recovery console.

---

### Post by mand0 on 2007-04-09
When it asks you whether you want to repair or do a clean install, I believe you want to choose repair.

---

### Post by _61_ on 2007-04-09
Well...

The recovery cd that came with my computer only have one option, which restores the original contents of the c: drive . No problem. I did it and then I copied my backup above it. It worked.

Thanks to all! You are the best!

---

