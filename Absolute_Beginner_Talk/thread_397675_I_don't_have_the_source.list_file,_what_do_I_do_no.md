---
title: "I don't have the source.list file, what do I do now? [Resolved]"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Parasitesss on 2007-03-30
From what you can see below, I obviously don't have the source.list file.


[PHP]john@john-desktop:~$ cd /etc/apt/
john@john-desktop:/etc/apt$ ls
apt.conf    secring.gpg          sources.list.d     trustdb.gpg  trusted.gpg~
apt.conf.d  sources.list_backup  sources.list.save  trusted.gpg
john@john-desktop:/etc/apt$[/PHP]

1. Could someone tell me why?
2. Is there I way I can fix this so I can actually look at my repositories?

---

### Post by NyteGeek on 2007-03-30
> **Parasitesss said:**
> From what you can see below, I obviously don't have the source.list file.


[PHP]john@john-desktop:~$ cd /etc/apt/
john@john-desktop:/etc/apt$ ls
apt.conf    secring.gpg          sources.list.d     trustdb.gpg  trusted.gpg~
apt.conf.d  sources.list_backup  sources.list.save  trusted.gpg
john@john-desktop:/etc/apt$[/PHP]

1. Could someone tell me why?
2. Is there I way I can fix this so I can actually look at my repositories?

rename your sources.list_backup or sources.list.save to sources.list

---

### Post by aysiu on 2007-03-31
Paste these commands into the terminal: ```
sudo mv sources.list_backup sources.list
sudo aptitude update
``` If you get any errors, post them back here.

You can also get a fresh sources.list [here](http://www.psychocats.net/ubuntu/sources).

---

### Post by Parasitesss on 2007-03-31
[PHP]john@john-desktop:~$ sudo mv sources.list_backup sources.list
mv: cannot stat `sources.list_backup': No such file or directory
john@john-desktop:~$[/PHP]

---

### Post by martinw89 on 2007-03-31
Hey John,
It looks like you just forgot to move to /etc/apt before running the commands.

---

### Post by aysiu on 2007-03-31
> **martinw89 said:**
> Hey John,
It looks like you just forgot to move to /etc/apt before running the commands.
Yes, I'd assumed you were continuing off the last command (where you were in /etc/apt). Try this instead: ```
sudo mv /etc/apt/sources.list_backup /etc/apt/sources.list
```

---

### Post by Parasitesss on 2007-03-31
oh thanks :] Im an idiot!

btw, the command above, did that just erase the source.list_backup because look:
[PHP]
john@john-desktop:~$ cd /etc/apt
john@john-desktop:/etc/apt$ ls
apt.conf    secring.gpg   sources.list.d     trustdb.gpg  trusted.gpg~
apt.conf.d  sources.list  sources.list.save  trusted.gpg[/PHP]

---

### Post by tonyr1988 on 2007-03-31
That command simply "moved" (mv = move) the sources.list_backup file (your backup sources.list file) to the sources.list file.

In other words, it renamed it. sources.list_backup became sources.list. You may want to re-do a backup, just in case something happens:

> sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

---

### Post by martinw89 on 2007-03-31
Yeah it erased the backup, it's like cutting and pasting.  In the future, if you want to do the same but with leaving the old file you can use "cp" instead of "mv".  If you want the backup back you can just copy the file into a backup ```
sudo cp sources.list sources.list_backup
```
And we all do silly things like being in the wrong directory:)

---

### Post by Parasitesss on 2007-03-31
Thanks for the help you guys, much appreciated.

---

