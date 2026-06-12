---
title: "Trouble accessing files"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by madman1611 on 2006-08-12
Hey, just ran the Ubuntu Live CD and loving it. Although, my question is, is it possible for me to view files that were saved under windows? Like music for example.

---

### Post by taurus on 2006-08-12
Yes.

---

### Post by kebes on 2006-08-12
Yes you should be able to access files that you were using in Windows.

If you're booted into the Live CD, then Ubuntu has probably automatically loaded ("mounted") your hard drive partitions. If you open up the file browser, you should be able to find them pretty easily (they may show up under a directory called "media").

I think the Live CD does not have mp3 codecs on it by default, thus you may not be able to play them right away. But OpenOffice is on the CD I believe, so you can open MS Word documents for instance.

Does that answer your question?

---

### Post by madman1611 on 2006-08-12
Thanks for the answer. Yes it does. One more question, is it possible for me to install applications while running the live cd?

---

### Post by madman1611 on 2006-08-12
I'm not able to access my hard-drive parition 1 or 2. Thus, I can't browse my files. Here's the error i receive: "The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "disks-conf-hda2."

---

### Post by TFX360 on 2006-08-12
Start a terminal session and type ```
gksu nautilus
``` (and enter password) and then try browsing to it again!

Or chown (Change Owner)


```
sudo mkdir /media/hdname
```

```
sudo chown usertohaveaccess /media/hdname
```


I have two sata disks and added these lines in /etc/fstab

Backup first!

```
sudo cp /etc/fstab /etc/fstab.bck
```

```
gksu gedit /etc/fstab
```

```
/dev/hdname       /media/hdname     ntfs    nls=utf8,umask=0222 0    0
/dev/hdname2       /media/hdname2     ntfs    nls=utf8,umask=0222 0    0

```

Remount drives if neccesary

sudo mount -a


In my case hdname = sda1 & sdb1


This makes my Windows NTFS drives readable in Ubuntu. I had to make & chown /media/sda1 and /media/sdb1.

---

### Post by madman1611 on 2006-08-12
[COLOR="Blue"][/COLOR] Hey thanks for the reply. WHen I get to the step /dev/hdname       /media/hdname     ntfs    nls=utf8,umask=0222 0    0  I replace my hd name where necessary and I get the error : "Bash: /dev/disks-conf-hda2 NO SUch file or Directory.

---

### Post by TFX360 on 2006-08-12
You need only to fill in the name of the harddisk. I think it should be /dev/hda2

Kind regards,


TFX

PS: I'm going to bed it's almost four in the morning here.

---

