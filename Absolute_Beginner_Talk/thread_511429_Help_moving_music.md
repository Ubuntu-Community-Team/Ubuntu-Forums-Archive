---
title: "Help moving music"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Specter043 on 2007-07-27
I just reinstalled Ubuntu onto my 120 GB Hard drive.  I have all my music/media on my 80 GB hard drive, but i'd like to move it all to the 120 GB.  ( Just a preference thing)  When I try to drag it onto the 120 GB, it says I don't have permission to read and write, or something similar.  I also noticed there's no obvious place, like my music/my pictures/my videos.  So does anyone know how to move the music and other media, as well as make the folders to put it in, where other users can access it?  The music especially, because me and my girlfriend listen to the same thing, no point in two folders.

---

### Post by benx009 on 2007-07-27
what type of file system does the 80gb drive use?  if it's ntfs, you'll have to have the ntfs-3g driver to move the files.

---

### Post by Specter043 on 2007-07-27
The 80 GB has FAT32, because I wanted to be able to write to it from my windows partition and my Ubuntu Partition.  But since iv'e decided to go complete Ubuntu, I no longer have the Windows Partition to worry about.  Actually, formatting the 80 GB after I move the music would be nice, but I feel like I'm asking way too much.

---

### Post by Blutack on 2007-07-27
Could you try and copy one of the files using a terminal (cp /media/whatever/file /home/username) and post the output?

---

### Post by Specter043 on 2007-07-27
I don't know what that means. :P

---

### Post by Blutack on 2007-07-27
OK, open a terminal
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)
and type in 
cp /media/drive /home/your_username

Literally CoPy from /media/drive/Music/somerandomfile (find out the drive by hitting tab after typing /media, it will list the possibilities and it should be obvious to /home/your_username (your home folder)

---

### Post by Specter043 on 2007-07-27
drive didn't exist, but Ubuntu refers to it as disk and I put disk in place of drive.  It told me cp: omitting directory `/media/disk'

---

### Post by Specter043 on 2007-07-27
I just figured out what was wrong, thanks for the help.

---

