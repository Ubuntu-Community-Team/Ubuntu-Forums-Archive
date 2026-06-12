---
title: "looking for iso mounting and burning software."
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-02-11
Hello
im looking for some software that will let me mount iso files of various types, and burn them to cd / dvd, something along the lines of nero or alcohol, i dont know if there is a program like this for linux ? the 2 i mentioned above also install a virtual drive, is that possible with ubuntu ?
cheers.

---

### Post by meng on 2007-02-11
Mounting and burning are different, of course, so I'm a little confused by how you phrased the question.

Mounting is easy!
sudo mount  -t iso9660 -o loop example.iso /media/mountpoint

If you use this, you don't need to burn a CD, which you can do anyway with gnomebaker, k3b, etc.

---

### Post by camorri on 2007-02-11
For burning ISO files install K3B. It will burn CD's and DVD's. The user interface is like Nero.

---

### Post by techno-mole on 2007-02-11
appologies.
i meant it as separate things, eg - i want to be able to mount the iso file on a virtual drive, like with nero image drive, and i also want to be able to burn iso's to disc, so a prgram like nero burning rom for example.
is there software for doing the mounting ? rather than using the command line that is ?
cheers.

---

### Post by meng on 2007-02-11
The "virtual drive" functionality is not special in Linux, it's the default behavior.
Also, even Nautilus can burn ISO to CD/DVD without requiring additional software.

These functions don't work by default in Windows, you need special software, but in Linux it works "out of the box". You have to change the way you think!

I don't really see the point of having a GUI frontend to mount individual isos.

---

### Post by techno-mole on 2007-02-11
the reason i want to burn is for backup, i like to keep my discs safe (i have kids) so being able to make copies of them is handy as i can keep the originals in their boxes, i see what you mean about not needing to burn if you can mount on a virtual drive type thing.
does that command work the other way ? eg - to unmount the iso - sudo  unmount -t iso9660 -o loop example.iso /media/mountpoint ? or does that require a different command ? 
cheers.

---

### Post by meng on 2007-02-11
To unmount, simply
sudo umount /media/mountpoint

Note the command is umount not unmount

---

### Post by taurus on 2007-02-11
If you want to make a backup copy of a disc, k3b can do that too.

If you want to unmount it, you just run

```
sudo umount /media/**mountpoint**
```

---

### Post by techno-mole on 2007-02-11
cheers.
its probably easier just to use those 2 commands rather than opening up a program and doing it that way.
cheers.

---

### Post by fakiro on 2007-02-11
Try this [http://www.kde-apps.org/content/show.php?content=44805]("http://www.kde-apps.org/content/show.php?content=44805")

---

