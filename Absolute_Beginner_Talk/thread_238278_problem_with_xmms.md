---
title: "problem with xmms"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2006-08-17
hi!
i have a problem with Xmms, i'd be very tankful if you'd help me coz i feel i die without this program :D ... i dont know why, when im trying to run this  program it appears in my taskbar for about 3-4 seconds and then it disappear. ive tryied to completly remove it from synaptic manager and to reinstall it... but the same thing :( has anyone ideea why? :(  thanx

---

### Post by Kobalt on 2006-08-17
This is quite wierd. 
Maybe you don't know this prgram : Beep Media Player. It's just like Xmms, but the version in the repos is newer than the Xmms version. I think I read somewhere that the Xmms project was over now, there won't be any updates... Anyway, I use Beep Media Player and I have no problems at all (you can even use your xmms skins on BMP). You can find it with Synaptic. 

Cheers !

---

### Post by powder on 2006-08-17
Could be a configuration problem.  Try renaming the .xmms directory in your home directory to something else and start XMMS.

---

### Post by Perfect Storm on 2006-08-17
Try start xmms through the terminal, check the output there if its revealing any error.

You might also try Audacious the new thing. Both xmms and bmp havn't been developed on or bug fixed for quiet awhile. bmp is a fork of xmms and audacious is a for of bmp.

[http://audacious-media-player.org/Main_Page](http://audacious-media-player.org/Main_Page)

---

### Post by the_nomad on 2006-08-17
thanx i got bmp and seems to work as good as xmms worked.

ps. how do i run through terminal?](*,)

---

### Post by Perfect Storm on 2006-08-17
type xmms in the terminal.

---

### Post by the_nomad on 2006-08-17
> thbk4u@thbk4:~$ xmms
libmikmod.so.2: cannot open shared object file: No such file or directory
Segmentation fault
thbk4u@thbk4:~$
thbk4u@thbk4:~$

](*,)

---

### Post by Perfect Storm on 2006-08-17
```
sudo apt-get install libmikmod2
```

Should clear up your problem.

---

### Post by the_nomad on 2006-08-17
> thbk4u@thbk4:~$ xmms
Segmentation fault

what that means?

---

### Post by Perfect Storm on 2006-08-17
uuhhh...that could be anything. Xmms is a bit buggy. Try start bmp up

---

### Post by sean_ on 2006-08-17
```
segmentation fault: n.

    [Unix] 

    1. [techspeak] An error in which a running program attempts to access memory not allocated to it and core dumps with a segmentation violation error. This is often caused by improper usage of pointers in the source code, dereferencing a null pointer, or (in C) inadvertently using a non-pointer variable as a pointer. The classic example is:


       int i;
       scanf ("%d", i);  /* should have used &i */
```

Taken from [http://www.catb.org/jargon/html/S/segmentation-fault.html](http://www.catb.org/jargon/html/S/segmentation-fault.html) My suggestion is to trying to install XMMS.

---

### Post by Perfect Storm on 2006-08-17
But he have xmms installed, which baffles me.

---

