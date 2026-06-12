---
title: "iMac G3"
date: 2008-08-27
forum: Apple Hardware Users
---

### Post by clipeuh on 2008-08-27
I have an iMac G3.
According to wikipedia, there's 32 MB of memory and a 4g hard drive.
What's the best linux distro ?

---

### Post by heroes_on_a_half_shell on 2008-08-28
hey bud,

eh, i'm workin on some b&w g3's i've had for a while.  if you only have a cd drive, (which i'm assuming is correct), you might better try your hand at a command line install of ubuntu off of the alternate installation cd.  then add the desktop environment of your choice from the command line.

to do the command line install.  get the alternate cd and at the "boot:" prompt type cli.  the rest of the install shouldn't be that bad.  but if you have problems, don't hesitate to ask.

once your cl system is installed, you need to install a graphical environment.  i would suggest xfce or possibly fluxbox for your machine.  (i don't know if fluxbox exits for ppc, but i don't see why it wouldn't).


```

$ sudo apt-get install xfce4

```

or


```

$ sudo apt-get install fluxbox

```


xfce is quite lightweight but i believe fluxbox may be faster. hope this helps.  for more detailed instructions, try here first:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

