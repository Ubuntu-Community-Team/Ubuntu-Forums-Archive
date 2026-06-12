---
title: "Linux equiv to Norton Ghost?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by boudreaujr on 2007-04-10
Are there backup/recovery programs that would be equivalent to Norton Ghost?  Any that come recommended for ease of use?

Thanks,
Denis

---

### Post by caffienefree on 2007-04-10
g4u (Ghost for Unix) or g4l (Ghost for Linux). 

[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)
[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

---

### Post by Maestro23 on 2007-04-10
Another log on the fire: [http://linuxappfinder.com/backupandrecovery](http://linuxappfinder.com/backupandrecovery)

---

### Post by calraith on 2007-04-10
[PING (PartImage Is Not Ghost)]("http://ping.windowsdream.com/")

However, the [PartImage]("http://www.partimage.org/") homepage warns against mission critical reliance on PartImage for NTFS cloning.  Apparently they haven't incorporated ntfs-3g.  0_o

---

### Post by wataboutbob on 2007-04-10
I use PartImage to make a backup of my root. Here's a real simple guide to going about making a backup of your installation.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Awesome guide for ubuntu starters.

---

### Post by johnnymac on 2007-04-10
I deploy clonezilla at work for doing full images of deployed servers...

[http://freshmeat.net/projects/clonezilla/?branch_id=68988&release_id=250159](http://freshmeat.net/projects/clonezilla/?branch_id=68988&release_id=250159)

---

### Post by boudreaujr on 2007-04-10
Wow, thanks for the quick replies.  I'll check into all the programs suggested.

Many thanks,

Denis

---

### Post by hoakz on 2007-04-10
I'm using rsync for backups but that program cannot do images, and I haven't actually done any recovery with it so I don't know how good/bad it is for doing that part.

/E

---

