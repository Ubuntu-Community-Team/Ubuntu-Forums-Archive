---
title: "how to restore the back_up"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by lazyazn on 2007-03-22
Hi
I was trying to set up my dual screen then i F***ed up something.  Now i can't even go to the login screen.  Does anyone know how i can restore my backed up file?

Thanks

---

### Post by moffa on 2007-03-22
DId you edit your xorg file?

the backups would be in /etc/X11/ and called xorg.conf.somedate or xorg.conf~

you need root access to overwrite it.
```

sudo mv xorg.conf xorg.conf.notworking
sudo mv xorg.conf.somedate xorg.conf

```

---

### Post by cowlip on 2007-03-22
if all else fails run:

sudo dpkg-reconfigure xserver-xorg

and choose "vesa" as the video driver, or you could try to edit /etc/X11/xorg.conf to use vesa

---

### Post by lazyazn on 2007-03-22
So do i enter this exact code? when i am in the root access

sudo mv xorg.conf xorg.conf.notworking
sudo mv xorg.conf.somedate xorg.conf

---

### Post by lazyazn on 2007-03-24
sorry to ask such a dumb question.  Some help please.

---

### Post by lazyazn on 2007-03-25
help please.

---

### Post by cowlip on 2007-03-26
when you're doing "sudo mv xorg.conf xorg.conf.notworking" your moving out xorg.conf.  SO what you want to do is move back one of your backups.  The 'somedate' "sudo mv xorg.conf.somedate xorg.conf" just means look for a date after the period, which should be a backup. 

What is the output of "ls /etc/X11/" ?

---

### Post by lazyazn on 2007-03-26
thanks for all the help guys.  I figured it out myself. 
the code was

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

---

