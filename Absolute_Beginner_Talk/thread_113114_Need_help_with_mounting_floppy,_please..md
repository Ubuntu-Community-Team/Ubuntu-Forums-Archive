---
title: "Need help with mounting floppy, please."
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2006-01-05
Until today, I have been typing ' sudo mount /media/floppy0 ' and my disk gets mounted.

Today, when I enter this same command, I get, "You must specify the filesystem type".

Could someone suggested what I might have screwed up, or how I might fix this situation, please?

Thanks.

---

### Post by proventech on 2006-01-05
did you leave a disk in the floppy :confused:

---

### Post by kairu0 on 2006-01-05
Is the floppy disk that you are trying to mount this time of the same filesystem as the floppies that you have mounted in the past?

---

### Post by L Campbell on 2006-01-05
[QUOTE=proventech]did you leave a disk in the floppy :confused:[/QUOTE]
........................

I have a disk in the drive when I do the ' sudo mount ' and AFAIK, I always do the 'sudo umount ' before I shut down.

_Could_ I have shut down with the disk still in the drive?  Well, yes but I doubt it.

Had I done so, would that be a likely result?

Thanks.

---

### Post by kairu0 on 2006-01-05
[QUOTE=L Campbell]
Had I done so, would that be a likely result?[/QUOTE]

No. There is probably a difference in the floppies that you are using AKA the one you are mounting now has a different filesystem, sector problems, is a bad disk, etc. Can you access this floppy on another computer?

---

### Post by proventech on 2006-01-05
i don't know, just brainstorming...      could the floppy be corrupted?

---

### Post by proventech on 2006-01-05
[QUOTE=kairu0]No. There is probably a difference in the floppies that you are using AKA the one you are mounting now has a different filesystem, sector problems, is a bad disk, etc. Can you access this floppy on another computer?[/QUOTE]

we smacked heads there :smile:

---

### Post by L Campbell on 2006-01-05
[QUOTE=kairu0]Is the floppy disk that you are trying to mount this time of the same filesystem as the floppies that you have mounted in the past?[/QUOTE]
>>>>>>>>>>>>

Yes, its the same disk that I was using early in the day but during the afternoon I began seeing the problem.

Thanks.

---

### Post by L Campbell on 2006-01-05
[QUOTE=kairu0]No. There is probably a difference in the floppies that you are using AKA the one you are mounting now has a different filesystem, sector problems, is a bad disk, etc. Can you access this floppy on another computer?[/QUOTE]
................................

I have a dual boot machine (98SE & Ubuntu) and I use the floppy to move information from one system to the other so, yes, the floppy also works in 98SE.

Thanks.

---

### Post by kairu0 on 2006-01-05
What filesystem does /etc/fstab say that the floppy disk will be mounted as?

---

### Post by Sef on 2006-01-05
This other post of mine tells how I got my floppy drive to automatically boot:

> There is a bug in Breezy, so often the floppies won't automount. To get them to automount, go to this site:

[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/](http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/)

1) Download pmount_0.9.6-1~breezy1_i386.deb

2) Install --> sudo dpkg -i pmount_0.9.6-1~breezy1_i386.deb

3) enter password

4) After it finishes installing, your floppy should mount and umount automatically.

I found that bug and fix from this thread: [http://ubuntuforums.org/showthread.php?t=93139&page=2](http://ubuntuforums.org/showthread.php?t=93139&page=2)

---

### Post by L Campbell on 2006-01-06
[QUOTE=Sef]This other post of mine tells how I got my floppy drive to automatically boot:[/QUOTE]
>>>>>>>>

Thanks very much.

This worked perfectly for me, I appreciate it.

Kind regards.

---

