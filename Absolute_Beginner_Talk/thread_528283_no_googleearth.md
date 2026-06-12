---
title: "no googleearth"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by jon zendatta on 2007-08-17
on  ubuntu 7.04 cannot open  /home/jon/Desktop/GoogleEarthLinux.bin

---

### Post by wormser on 2007-08-17
How did you install Google Earth?  I just installed from the repositories and it worked fine.

```
sudo apt-get install googleearth
```

---

### Post by por100pre1 on 2007-08-17
If you can't find Google Earth add the [Medibuntu repositories]("http://medibuntu.org/repository.php") then try to install it with above method again.

---

### Post by gn2 on 2007-08-17
Or just use this freebie from Uncle Bill: [http://local.live.com/](http://local.live.com/)

---

### Post by logos34 on 2007-08-17
> **por100pre1 said:**
> If you can't find Google Earth add the [Medibuntu repositories]("http://medibuntu.org/repository.php") then try to install it with above method again.

Yes, but how up to date is it?  I used the .bin installer and I'm running the latest beta build (May) and it's works better than ever!  Fantastic, all the former glitches and bugs gone...

try right-clicking on the .bin file>properties>permissions>allow executing file as program

---

### Post by por100pre1 on 2007-08-17
> **logos34 said:**
> Yes, but how up to date is it?  I used the .bin installer and I'm running the latest beta build (May) and it's works better than ever!  Fantastic, all the former glitches and bugs gone...

try right-clicking on the .bin file>properties>permissions>allow executing file as program

I think the issue was Google Earth not running. You can provide instructions on how to install the latest version, I'm sure it'll be very appreciated. :)

---

### Post by mgmiller on 2007-08-17
> Yes, but how up to date is it?

I am using the version from the repositories:

Google Earth
4.0.2735
Build Date
Jan 30 2007
Build Time
14:31:57
Renderer
OpenGL
Operating System
Linux (2.6.20.0)
Video Driver
NVIDIA Corporation
Max Texture Size
4096x4096
Server
kh.google.com
User

License Key

I have absolutely no problems running this.  No bugs that I can find and I even have it running with compiz turned on in Feisty.  I assume it will update when I upgrade to Gutsy in October if not sooner, but for now it works great.

---

### Post by rfruth on 2007-08-17
install from the repos or from Google [http://earth.google.com/support/bin/answer.py?answer=44713&topic=1135]("http://earth.google.com/support/bin/answer.py?answer=44713&topic=1135")

---

### Post by Ragnar Bocephus on 2007-08-17
It looks like the OP has already downloaded GoogleEarthLinux.bin, he's just having trouble installing it.  Seems like all he needs to do is open the terminal, change directory to Desktop, and execute the following code:

```
sh GoogleEarthLinux.bin
```

---

