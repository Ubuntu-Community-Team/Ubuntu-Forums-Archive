---
title: "I want to rip a CD iso to my hard drive..."
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2008-01-28
I'm trying to rip the image off my PS1 games so that psX might play them better. I used to do the same thing in Windows; emulators just work better when they don't have to read my cd drive.

Anyway, I've tried:
cp /media/cdrom0 sagafrontier2.iso

and I get "input/output error"

then I googled and tried:

sudo mkisofs -r -o /sagafrontier2.iso /dev/cdrom

which told me I needed to install mkisofs, which I did. Then it told me:

Setting input-charset to 'UTF-8' from locale.
Total translation table size: 0
Total rockridge attributes bytes: 281
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 0
175 extents written (0 MB)

Which makes a 16kb file that doesn't do anything...

Also, when I browse with my file manager, the CD is named "CD-Rom Disc" but appears to have nothing in it. I know the CD works, because I can play psx off of it.

Then I tried a program called xcdroast, but it told me that I had to enable scsi emulation in the kernel, which I don't know how to do.

I don't want to download a KDE app, just because I don't have any other KDE apps and K9copy would require about 100MB in libs, just for one program. Plus there is no guarantee that it would even work.

What can I do?

---

### Post by mikewhatever on 2008-01-28
You could use Graveman, a smaller non-KDE application from the repositories. In the programs's window, select 'Duplicate CD' and select iso file in 'Write to'. Hope that helps.

---

### Post by Pogeymanz on 2008-01-28
I installed graveman and when I attempted to copy the CD I received this error:

Cannot create image: /usr/bin/readcd: Input/output error. read_g1: scsi sendcmd: no error
CDB:  28 00 00 00 00 00 00 00 40 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 03 00 00 00 00 0A 00 00 00 00 11 05 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x11 Qual 0x05 (l-ec uncorrectable error) Fru 0x0
Sense flags: Blk 0 (valid) 
cmd finished after 2.780s timeout 40s
/usr/bin/readcd: Input/output error. Cannot read source disk
/usr/bin/readcd: Retrying from sector 0.

---

### Post by PilotJLR on 2008-01-28
Also try dd... simple and works well.
```

sudo umount /dev/cdrom
sudo dd if=/dev/cdrom of=~/sagafrontier2.iso

```

---

### Post by Pogeymanz on 2008-01-28
dd: reading `/dev/cdrom': Input/output error
32+0 records in
32+0 records out
16384 bytes (16 kB) copied, 2.74626 seconds, 6.0 kB/s

That's what I get from that. It makes a 16kb useless file.

What the heck error is it getting?

---

