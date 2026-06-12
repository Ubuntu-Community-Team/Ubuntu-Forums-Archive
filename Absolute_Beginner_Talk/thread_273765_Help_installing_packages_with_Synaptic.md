---
title: "Help installing packages with Synaptic"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by TTTodd on 2006-10-08
I am trying to install some packages and get the following error:

E: ubuntu-desktop: failed in buffer_read(fd)

It gives this error no matter what package I try to install.  This is a fresh install and I got the same error when I tried to update as well.

AMD 64 x 2, not dual booted.  Trying to use Ubuntu instead of buying Windows, any help would be great. thanks! Todd

---

### Post by TTTodd on 2006-10-08
Here is the same type of error when using add/remove as well:

E: /var/cache/apt/archives/libgtk1.2-common_1.2.10-18_all.deb: failed in buffer_read(fd)

heellllpppppp

---

### Post by thornomad on 2006-10-08
I don't know much, but I can offer: have you tried installing the packages from the Terminal ?

```
sudo aptitude update
sudo aptitude install nameofthepackage
```

Maybe you will get the same error, but worth a shot ?

---

### Post by TTTodd on 2006-10-08
thanks, but no luck.  Says it cannot find any file by the name.  Very frustrating.

---

### Post by thornomad on 2006-10-08
Is the file you are looking for in the Universal repositories (not the default repositories), by chance ?  And, if it is, have you enabled yours ?

---

### Post by TTTodd on 2006-10-08
trying packages from both. And yes I have enabled them. thanks!

---

### Post by gn2 on 2006-10-08
Have you got 64-bit Ubuntu?

It can be problematic...

---

### Post by TTTodd on 2006-10-08
Yes, I was just seeing that in that in the 64bit forum.  I might be better off going with a 32bit version instead?  First time Linux user here.  So will take any advice I can get on that topic. thanks, todd

---

### Post by gn2 on 2006-10-08
32-bit is absolutely the way to go, no question...

You can always have a go with 64 down the track a bit.

---

