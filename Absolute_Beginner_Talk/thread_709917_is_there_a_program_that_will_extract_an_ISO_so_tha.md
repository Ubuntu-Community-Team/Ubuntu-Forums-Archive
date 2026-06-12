---
title: "is there a program that will extract an ISO so that you can burn it as a data CD?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Sorandal on 2008-02-27
The computer that has a burner isn't mine, so I can't download progams to burn ISO images, so I'd like to unpack the iso onto a thumb drive and burn it as data files.  Is there such a program, and if so would I still be able to boot from the CD?
Thanks

---

### Post by spiderbatdad on 2008-02-27
If I'm not mistaken, the nautilus cd burner, installed with ubuntu offers the option just prior to writing the disk.

---

### Post by glennric on 2008-02-27
You can mount the iso and then copy the files from there to the thumb drive.  To mount the iso create a directory in your home directory, say "iso" and then type
```
sudo mount -o loop -t iso9660 isofile.iso ~/iso
```
To unmount the iso after you are done type
```
sudo umount ~/iso
```

---

### Post by glennric on 2008-02-27
By the way a much slower method than mounting the iso is to extract it as you said.  This can be done with "Archive Manger," which can be found in the Applications->Accessories menu.  This is actually file-roller if you want to run it from a terminal.

---

### Post by asmoore82 on 2008-02-27
> **Sorandal said:**
> The computer that has a burner isn't mine, so I can't download progams to burn ISO images, so I'd like to unpack the iso onto a thumb drive and burn it as data files.  Is there such a program, and if so would I still be able to boot from the CD?
Thanks

an ISO image and a data CD are the same thing.
Is the computer you want to burn with Ubuntu??

No, the data CD you create will not be bootable unless you make it so.

---

### Post by Sorandal on 2008-02-28
Hi there, both my computer and the one I'm burning on are running XP.  I'm no guru, but my understanding is that multiple files meant for a CD are combined into a single iso file, and that when you burn it as an image it separates these the iso back into the individual files.  I'm hoping that if I separate these files and then burn them as a data CD that it would have the same effect.  I was able to separate an ISO into the individual files using Winrar, so now I just need to know whether the second part of this idea will work.

---

### Post by myddewji13 on 2008-02-28
as stated above it is not the same....however for winxp..try the following

[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

---

