---
title: "[SOLVED] SiS MIrage graphics problem"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by travismoore on 2008-02-08
I have SiS Mirage (build into motherboard) 128MB

When i have it on standard res (what i intend to use 1024X68 or something)

I am getting lots of graihcs errors its hard to describe and doesn't show up in screeshots.

And the errors get very very bad if i put the res up.

Any ideas?

Also any chance compiz-fusion will work? Doesn't matter if it doesn't but it would be awesome if it did.


Cheers,

Travis

---

### Post by spydon on 2008-02-08
I think you will have to look for some driver or something, is it currently using vesa?

---

### Post by travismoore on 2008-02-08
I'm  not sure really i don't know how to check that.

---

### Post by travismoore on 2008-02-08
bump

---

### Post by travismoore on 2008-02-09
10 hour bump

---

### Post by overdrank on 2008-02-09
> **travismoore said:**
> 10 hour bump

HI and the sis graphics are not that great in ubuntu. If you can check your xorg and you may change the default depth from 24 to 16 this may help. YOu can use the command ```
gksudo gedit /etc/X11/xorg.conf
``` and this will allow you to edit and save your xorg.

---

### Post by travismoore on 2008-02-09
K cheers will give that a go =D

---

### Post by spydon on 2008-02-09
Give this one a try too:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by travismoore on 2008-02-18
Cheers guys that god rid of graphical errors, haven't tried compiz yet because I'm working on getting my internet functional but even if compiz doesn't work i dont really mind.

---

