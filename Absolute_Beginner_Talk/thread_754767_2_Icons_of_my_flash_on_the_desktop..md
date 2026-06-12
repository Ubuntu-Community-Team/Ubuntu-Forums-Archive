---
title: "2 Icons of my flash on the desktop."
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Mosaab on 2008-04-14
hello, 

When I plug my flash memory 2 icons show in the desktop, why does this happen? how can I make it one.?

---

### Post by rjmoerland on 2008-04-14
I might be wrong, but it seems that some flash drives really have two partitions. Mounting them also gives you two drive letters with Windows. Might be for emulating a floppy? Would be 'the right thing' then to give you two icons when using this drive with Ubuntu, so you can access both partitions.

---

### Post by Mosaab on 2008-04-14
Thanks for replying but No, I dont think so... because I have been using that flash for a long time and when I first installed ubuntu there was only one icon.
I guess I messed alot with mounting (manually) that I cant get until now.

---

### Post by Michael.Godawski on 2008-04-14
Check in the Configuration Editor if there are duplicated entires:
```
gksudo gconf-editor
```
apps> nautilus > desktop

---

### Post by Mosaab on 2008-04-14
No, there are no duplicates!

---

### Post by rjmoerland on 2008-04-14
What is the output of the mount command?
```

mount

```

---

### Post by Mosaab on 2008-04-16
Actually  Every thing went good suddenly!, I dont know what happened , but now there is only one icon, though i restarted many times.

---

### Post by timcredible on 2008-04-16
most newer flash drives have 2 partitions, one for you to use and the other for the U3 nonsense.  linux automounts them both, which is what it should do.  if you want it to be one, just delete both partitions and then make the whole flash drive 1 single partition - make it fat32 if you want to use it with windows, ext3 if you want it to preserve file permissions.

---

### Post by renfrew on 2008-04-16
I had a similar experience with my own flash drive, it also happened sometimes with my cdrom drive.. I suspect it's a slight glitch in the gnome-mount manager applet, maybe the hal daemon is misreporting to gnome-mount ?   I usually unmounted the drives and rebooted and it seemed to clear the 'ghost drive'... while its true that some flash drives present 2 partitions, I don't think that's the case here.... wait a couple weeks for hardy to come out.. it should clear the problem.... since I've been running the Hardy beta I haven't had that problem....

---

