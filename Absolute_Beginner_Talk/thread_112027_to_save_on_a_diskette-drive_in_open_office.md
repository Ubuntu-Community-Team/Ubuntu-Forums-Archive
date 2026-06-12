---
title: "to save on a diskette-drive in open office"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by digi_taal on 2006-01-03
can't manage!
when I click "save as", I see no option to save on a diskette?
what am I to do?
s.y.
digi

---

### Post by ubuntuuser on 2006-01-03
Change to the folder /media/floppy and save the file there. be sure to mount a disk before writing.

---

### Post by digi_taal on 2006-01-03
:) thx for y're quick reply... but there's more amis!
so thanks to you I found it where to klik, but my pc pretends there is no floppy!

sth happened during installation perhaps?

---

### Post by Sef on 2006-01-03
I think the default is not to mount the floppy.  I sometimes use a floppy and have to mount and unmount it each time i use it.

Edit: here's how to mount and unmount a floppy [http://ubuntuforums.org/showthread.php?t=110132&highlight=floppy]("http://ubuntuforums.org/showthread.php?t=110132&highlight=floppy")

---

### Post by Sef on 2006-01-05
Eventually I stumbled across a post (like on page 29 (at the time) of desktop forums.)  Thread to the post is at the bottom of the page.

This other post of mine tells how I got my floppy drive to automatically boot:

Quote:
There is a bug in Breezy, so often the floppies won't automount. To get them to automount, go to this site:

[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/](http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/)

1) Download pmount_0.9.6-1~breezy1_i386.deb

2) Install --> sudo dpkg -i pmount_0.9.6-1~breezy1_i386.deb

3) enter password

4) After it finishes installing, your floppy should mount and umount automatically.

I found that bug and fix from this thread: [http://ubuntuforums.org/showthread.php?t=93139&page=2](http://ubuntuforums.org/showthread.php?t=93139&page=2)

---

