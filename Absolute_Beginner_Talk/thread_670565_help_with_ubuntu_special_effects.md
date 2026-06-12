---
title: "help with ubuntu special effects"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by livi on 2008-01-17
just can't get special desktop effects to run on gutsy.  i think my video card is too old..though i've seen 
posts which insist in will handle it....i'm running an old nvidia geforce fx 5200 card.. have tried everything to get the special effects up and running--to no avail.  i used wubi installer to give gutsy a try on my win xp pro system.  all help welcome and appreciated.

---

### Post by Het Irv on 2008-01-17
Do you know how much onboard memory your card has?
Also which Drivers are you useing?

---

### Post by PinkFloyd102489 on 2008-01-17
[http://us.download.nvidia.com/XFree86/Linux-x86/169.07/NVIDIA-Linux-x86-169.07-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/169.07/NVIDIA-Linux-x86-169.07-pkg1.run)


Download that file and then do this:


#Replace gdm with kdm or xdm depending on what you have.
```

sudo /etc/init.d/gdm stop

```
#cd to the directory with the file you downloaded.

#switch to root
```

sh NVIDIA-Linux-x86-169.07-pkg1.run

```

It'll compile and install the kernel module. When it's done, do this:

#Once again, replace gdm with kdm or xdm accordingly
```

sudo /etc/init.d/gdm start

```


That should do it.

---

### Post by forestpixie on 2008-01-17
should work with the restricted driver manager I would have thought

> i'm running an old nvidia geforce fx 5200 card I can run it an older geforce4 mx400

will compiz actually work in a wubi install?

---

