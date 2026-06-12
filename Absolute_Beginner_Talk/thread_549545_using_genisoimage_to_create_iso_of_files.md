---
title: "using genisoimage to create iso of files"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by Lelouch on 2007-09-12
I heard that genisoimage is able to create an iso image of specific files and dir...

I checked my synaptic, and it appeared to be already installed..

Where can i find it, and how can i use it?

---

### Post by ThrobbingBrain66 on 2007-09-12
give this a shot:
[http://www.blindhog.net/linux-create-an-iso-image-from-a-directory/](http://www.blindhog.net/linux-create-an-iso-image-from-a-directory/)

---

### Post by aldenhg on 2007-09-12
To make an iso out of a directory, file up a terminal and punch in
```
mkisofs -o *nameofiso.iso* */directory/you/want/to/make/into/an/iso*
```

---

### Post by Lelouch on 2007-09-12
It is a good tutorial... but a there is a problem with it..

i extracted super grub disk (.iso) and recreated it just for experiment...

iso is created, but it is not bootable... although all files are copied...

Why is that?

---

### Post by Lelouch on 2007-09-12
Found the answer...
> 
herman@red:~$ genisoimage -R -b boot/grub/stage2_eltorito  \
-input-charset iso8859-1  \
-V "SUPERGPARTPUPPY"  \
-no-emul-boot \
-boot-load-size 4 -boot-info-table -o supergpartpuppy.iso supergpartpuppy

Thanks for ur help

---

### Post by aldenhg on 2007-09-15
I didn't realize you wanted it to be bootable. Those instructions should work just fine. This is what I love about Linux - the same functionality on Windows would require scouring Google and possible some cash, but it's already installed and ready to go here.

---

