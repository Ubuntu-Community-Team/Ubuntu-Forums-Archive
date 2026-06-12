---
title: "[SOLVED] Disk usage does not add up"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by atsyed on 2007-11-24
I do not understand why the free disk space on my (53GB) HD is only 5.2GB while the root and its subdirectories occupy a total of 9.3GB. I am using ktorrent for downloading some files - maybe this software has saved a lot of temporary stuff somewhere on my HD which is not visible to me. 

I hope someone will point me in the right direction - thanks

---

### Post by bluepowder7 on 2007-11-24
have you started downloading some torrents already?  in some downloaders, you can set them to pre-allocate the entire space for the file it's downloading, so even if it's only gotten 1meg of a movie, it'll reserve the whole 700megs or whatever for it and report it as "used and unavailable space"

---

### Post by atsyed on 2007-11-24
thanks for the quick reply! yes, the pre-allocation of disk space was enabled. I have restarted ktorrent and will observe disk usage closely.

I still do not understand why the available disk space on my 53GB HD is only 5GB while the root (the ultimate file system parent) is using 9.3GB only. what happened to my 42GB of space? its a mystery to me for now. 

thanks again to everyone for helping me.

---

### Post by forestpixie on 2007-11-24
that's a lot of space to lose :) I expect there's a way to get the info from the terminal, I know that du does - but I don't get how to get it to look at whole disc

I expect as soon as I post this it'll show up, think I've got it now - in the meantime run the disk analyser in accessories and see what it says

Edit

```
 sudo du -sh /* -h
```

gives a total directory I believe, at least it looks ok on mine

and ```
du --max-depth=1 -h
``` should be home's directory - if terminal is at home

---

### Post by atsyed on 2007-11-24
thanks forestpixie!

Your comments are very helpful. I am slowly getting closer to solve the mystery. There is ./archives directory that is holding up 39G with many tar.gz files. these are listed in red color. What does that mean? are these orphaned files? and if so, can these be removed without destabilizing the OS? i look forward to reading your thoughts - thanks!

---

### Post by atsyed on 2007-11-24
thanks forestpixie

Yay!!! I recovered 38GB.. I logged in as root and erased the orphaned files using the command line "rm *.gz"

thanks again forestpixie ... you are a rockstar!!!

---

### Post by forestpixie on 2007-11-24
good news I'd say then  - I've not got a ./archive dir myself - so I assume it's not critical :)

We both learned something today - I'd never used the command myself, once I found it and had a look at the man page - it became as clear as mud! 

can you mark thread as solved if you're happy

---

### Post by atsyed on 2007-11-24
thanks again forestpixie ... just marked my problem solved ...you are a great help!
ciao!

---

