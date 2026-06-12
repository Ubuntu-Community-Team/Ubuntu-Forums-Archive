---
title: "mounted windows partition: now i have a couple problems."
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by revilot on 2006-07-03
I mounted my windows partition following this guide:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

I used the script.  The partition is mounted fine, but my problem is I made a link to the partition, as outlined towards the bottom of that same how to, on my desktop and now i can't delete it.  I've only tried highlighting and hitting delete and dragging it into the trash can since I don't know the proper command, if one exists, to enter into terminal.  

Then I rebooted and now theres a hda1 icon, linking to my windows partition also, on my desktop.  Not sure where that came from and I can't delete that one either.

Any ideas? TIA.

---

### Post by mackinax on 2006-07-03
go to: System Tools -> Configuration Editor ,
then: apps -> nautilus -> desktop

uncheck "volumes_visible"

---

### Post by revilot on 2006-07-03
[QUOTE=mackinax]go to: System Tools -> Configuration Editor ,
then: apps -> nautilus -> desktop

uncheck "volumes_visible"[/QUOTE]

Thanks, but that doesn't get rid of the symlink, I'd like to know how to get rid of just the symlink.

I created it by typing 
> ln -s /media/hda1 ~/Desktop/
into terminal.

---

### Post by aysiu on 2006-07-03
```
sudo rm ~/Desktop/media/hda1
```

---

### Post by mackinax on 2006-07-03
or it might be "sudo rm ~/Desktop/hda1"

---

### Post by aysiu on 2006-07-04
[QUOTE=mackinax]or it might be "sudo rm ~/Desktop/hda1"[/QUOTE]
Yeah, good catch.

---

### Post by revilot on 2006-07-05
Thx worked like a charm.

---

