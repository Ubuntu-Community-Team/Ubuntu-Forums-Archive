---
title: "Navigating To An External Drive"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by CurtZX on 2007-08-05
hello,

I have been looking at this thread [http://ubuntuforums.org/showthread.php?t=515799](http://ubuntuforums.org/showthread.php?t=515799) trying to find my answers but I am still falling short

I am trying to use terminal to discover an external drive (which shows up as 'new volume') and then ultimately execute a command from terminal on a file that is contained within the external drive.

When I hook up the drive the GUI comes up with the drive no problem, and the file contained inside, but I cant seem to access it..

I have tried cd /media and then searching inside and it gives me this:

curtis@curtis-laptop:/media$ ls
cdrom  cdrom0  New Volume

So it can definately see the 'new volume', I just cant seem to get inside of it using terminal so I can execute a command... 

I am a windows guy (dont shoot me :guitar:) So forgive me if my question is a little silly.

---

### Post by wolfen69 on 2007-08-05
what you're looking for may be a hidden file. open the drive and do Ctrl+H. any hidden files will be revealed.

---

### Post by finer recliner on 2007-08-05
if a file or directory has a space in it, you need to "escape" it by putting a forward slash (\) in front of the space or wrapping the entire path in quotes
```

$cd /media/New\ Volume

$cd "/media/New Volume"


```

---

### Post by CurtZX on 2007-08-05
finer recliner! Thanks, that worked!!

NOW, it is saying THIS :

dd: opening `/dev/hda': Permission denied
curtis@curtis-laptop:/media/New Volume$

the command I am trying to run looks like this (with the exception of the file name I am copying)

dd bs-1048576 if=./filename.img of=/dev/hda

:(

---

### Post by CurtZX on 2007-08-05
I think I just screwed the external drive up.... I just ran that same command and put /sda1 instead of /hda and I think it tried to unpack the file on itself....Now the external drive wont recognize through ubuntu or terminal and is making wierd sounds....:(

---

### Post by CurtZX on 2007-08-05
does anybody have any idea what I did or why I cant access the external drive ??

---

### Post by CurtZX on 2007-08-05
nobody knows?

---

