---
title: "@#@! Build-Essential bug"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by hdensley on 2007-06-10
I'm trying to stay cool here, so ignore the title.  I've just wasted a good portion of a day working on a wireless networking configuration, as if it wasn't hard enough, I think I just found a bug in 7.04

- 7.04 will not find packages on the installation CD
- build-essential is not found, nor many of the dependencies without a painful manual search
- gcc-4.1 and another dependency have circular dependencies on eachother -- hence I'm stalled out and extremely frustrated
- sorry I didn't write down the other package, as stated above, I'm just trying to get my dang wireless to work

If anyone has a solution for this, that would be great, otherwise I might revert to the * relative* (relative to this experience) - stability of windows 2000

For more details on my WIRELESS problem - [http://ubuntuforums.org/showthread.php?t=470096](http://ubuntuforums.org/showthread.php?t=470096)

---

### Post by taurus on 2007-06-10
Insert the installer CD into a drive, open a terminal, and run

Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by hdensley on 2007-06-11
Mounting CD-ROM
E: Failed to mount the cdrom

---

### Post by stchman on 2007-06-11
> **hdensley said:**
> I'm trying to stay cool here, so ignore the title.  I've just wasted a good portion of a day working on a wireless networking configuration, as if it wasn't hard enough, I think I just found a bug in 7.04

- 7.04 will not find packages on the installation CD
- build-essential is not found, nor many of the dependencies without a painful manual search
- gcc-4.1 and another dependency have circular dependencies on eachother -- hence I'm stalled out and extremely frustrated
- sorry I didn't write down the other package, as stated above, I'm just trying to get my dang wireless to work

If anyone has a solution for this, that would be great, otherwise I might revert to the * relative* (relative to this experience) - stability of windows 2000

For more details on my WIRELESS problem - [http://ubuntuforums.org/showthread.php?t=470096](http://ubuntuforums.org/showthread.php?t=470096)

Yes, this is silly.  The build-essential package is not installed by default and it should be.  You need it for make as make compiles programs using gcc.  Just install the build-essential package.  I have included a bunch of must have programs in a script I wrote.

[http://www.stchman.com/feisty_script.html](http://www.stchman.com/feisty_script.html)

---

