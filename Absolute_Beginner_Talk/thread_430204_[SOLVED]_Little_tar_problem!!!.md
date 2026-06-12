---
title: "[SOLVED] Little tar problem!!!"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by victorbrca on 2007-05-01
Hi guys,


  Can anyone tell me what am I doing wrong here??? Can' t figure it out...

```
victor@victor-laptop:/media/WD Passport/backups/usb1$ sudo tar -czvf /media/usbdisk/* 2007-05-01.tar.gz
tar: /media/usbdisk/Backup: Cannot open: Is a directory
tar: Error is not recoverable: exiting now
tar: Removing leading `/' from member names
/media/usbdisk/Books/
/media/usbdisk/Books/SmoothWall Admin.pdf

```



Thanks,


  Vic.

---

### Post by Cypher on 2007-05-01
You need to flip the arguments a litle bit..
```

sudo tar -czvf 2007-05-01.tar.gz /media/usbdisk/*

```

You need to follow the "-f" option with the file you wish to "-c"reate. The files which should go into the tarball would come last.

---

### Post by victorbrca on 2007-05-01
lol ..... I'm such  a noob...... 


Thanks a lot!!!!   


Vic.

---

### Post by Cypher on 2007-05-01
We were all noobs once..;) And since you're playing with the command line, might I suggest 
```

man <any-command>

```
That is the most authoritative information you can get about a command, and a great way of learning all the intricacies of command line..

---

### Post by victorbrca on 2007-05-01
> **Cypher said:**
> We were all noobs once..;) And since you're playing with the command line, might I suggest 
```

man <any-command>

```
That is the most authoritative information you can get about a command, and a great way of learning all the intricacies of command line..

Thanks again!!!!!  :)

Vic.

---

