---
title: "File Backup Application?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Sleestack on 2007-10-21
I'm using Gutsy with existing external NTFS drives created using XP. They contain some pretty critical data I would like to backup/copy across the drives for safe keeping. What is the best backup application to use with this configuration, and am I asking for any trouble doing this with native NTFS volumes?

---

### Post by kevdog on 2007-10-21
Depends how complex you want to make your backups.

It could be as simple as running a cron job to copy the files everynight to a destination (one way sync)

or you could use complex tools such as rsync or unison (which I think is better).  Both rsync and unison can allow for two way syncs (if needed).  Ive run both on both linux and windows (through install cygwin on windows).

There probably exist other methods, however Im pretty happy with unison, although it did take me a while to figure out how to use this, and it requires that you compile the program (easy, but if you have never compiled from source, this is yet something else you need to figure out)

---

### Post by robin.w on 2007-10-21
If u wanna do only files backup u can simply use tar although i have never tried it on NTFS fs. According my experience it's always good to have hda image. Try dump or dd commands - very useful. For more info check man.

tar -cf [backupname.tar] [folders_for_backup]
tar -czvf ... with gzip compression

dd if=/dev/hda |gzip > [output_file.gz]
dump -0Lauf - / | gzip -2 | dd of=[output_file.gz]

Do not forget to save your MBR (first 512 bytes on your hard drive).
dd if=/dev/hda of=[output] bs=512 count=1

---

