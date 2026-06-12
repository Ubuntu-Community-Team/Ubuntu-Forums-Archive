---
title: "Virtual mount of .bin files."
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-03-11
How is this done? I've tried installing cdemu but the readme is horrible.

---

### Post by bernied on 2007-03-11
What is this .bin file?
If it were a cd or dvd image (usually .iso), you would use something like
```
sudo mount -o loop /path/to/file /path/to/mount/directory
```
Does this help?

---

### Post by auraithx on 2007-03-11
> **bernied said:**
> What is this .bin file?
If it were a cd or dvd image (usually .iso), you would use something like
```
sudo mount -o loop /path/to/file /path/to/mount/directory
```
Does this help?

That's for mounting, isos. not .bins. 

even if it were an iso the correct command is

```
sudo mount isofile.iso /mount/path/ -t iso9660 -o loop
```

---

### Post by SishGupta on 2007-03-11
This likely isn't the best answer to your problem, but if you only need to do this a few times then I am sure it will suffice.

[http://users.andara.com/~doiron/bin2iso/](http://users.andara.com/~doiron/bin2iso/)

edit: ah sorry it looks like the linux version is down. you can probably find it on google.
or try the source which is there...

---

