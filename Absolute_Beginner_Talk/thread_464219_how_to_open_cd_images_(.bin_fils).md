---
title: "how to open cd images (.bin fils)"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-06-04
Hi
Thank you for reading my post
Can some one please let me know how i can open .bin files?
I have some cd images in .bin format and i just want to use them and not burn them on another CD to use them.

Thanks

---

### Post by pizzutz on 2007-06-04
First give them executable privleges

sudo chmod a+x <filename>.bin

then run them 

./filename.bin

(you need the ./ because the current directory is not included in the path by default, so you need to specify a relative path to the file)

---

### Post by gerscht on 2007-06-04
There's a 'click way' as well:
[http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html](http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html)

---

### Post by gerscht on 2007-06-04
> **pizzutz said:**
> First give them executable privleges

sudo chmod a+x <filename>.bin

then run them 

./filename.bin

(you need the ./ because the current directory is not included in the path by default, so you need to specify a relative path to the file)
I think he want's to browse the file, not execute it (which wouldn't have an effect anyway, or?!)

---

### Post by pizzutz on 2007-06-04
ugg, that looks like way to much work :P

---

### Post by pizzutz on 2007-06-04
Actually, I guess I'm not sure. I've executed bin files before, they were self extracting archives.  I assumed his were something similar.

---

### Post by pizzutz on 2007-06-04
My mistake. I was thinking of a bin file as the linux executable, not the iso type cd-image...

[http://filext.com/file-extension/bin](http://filext.com/file-extension/bin)

Ignore my post.

---

