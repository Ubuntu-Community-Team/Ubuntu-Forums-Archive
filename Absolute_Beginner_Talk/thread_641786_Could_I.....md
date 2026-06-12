---
title: "Could I...."
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Tristicus on 2007-12-15
I want to know. How many Linux distros can I run on my system? If I used Ubuntu as main, but still had some other distros on there, how many could I have in the GRUB boot menu, and would it work if I had enough space?

Thanks!

---

### Post by skymera on 2007-12-15
im sure its as many as can fit :)

---

### Post by spai on 2007-12-15
Well I was wondering the same thing.
And I also want to know how can I install different flavors.
My idea is that if the kernel, GNOME and many things being same, cant we just install the remaining utilities specific to the flavor. Thereby save space and time in installing?

---

### Post by Tristicus on 2007-12-15
To install different flavors, you can just type (this is probably wrong..)

```
sudo aptitude get kubuntu
```

Because I did that for Xubuntu and Fluxbox.

---

### Post by skymera on 2007-12-16
sudo apt-get install kubuntu-desktop

etc

---

### Post by jken146 on 2007-12-16
Aysiu's site ([psychocats.net/ubuntu](psychocats.net/ubuntu)) has a nice little section on installing different desktop environments (KDE, XFCE) and on removing them.

As for multiple distros, the problem that arises is that every distro tries to store its config files (the hidden directories starting with . in /home/<username>), and these tend to overwrite each other all the time.  So if you are going to have a shared /home directory, you need to use a different user name for each distro.

---

### Post by rickycodie on 2007-12-16
i agree with jken, installling different distros is harder. the easiest way to do it is to install all the distros that you want first and then ubuntu last. other than that you have to do alot of grub editing and that can get confusing.

---

