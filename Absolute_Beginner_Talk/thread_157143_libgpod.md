---
title: "libgpod?"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by darksc00by on 2006-04-08
I cant figure out how to install it, sorry im a n00b, but I cant install it, can someone tell me how to install when the file is downloaded?

---

### Post by darksc00by on 2006-04-08
oh btw, i have gtkpod, but if i sync and add my new files, i dont think it will keep the old files without libgpod, is this true, because I have so many files on the ipod, i couldnt dl them all. hah.

---

### Post by angkor on 2006-04-08
If you installed gtkpod from the repositories I think you already have libgpod. Try:

```
apt-cache policy libgpod0
```

to see if it's installed.

---

### Post by darksc00by on 2006-04-09
it says i dont have libgpod or libgpod0 installed. and i might need updated repositories then? cause i installed it from repositories... and i cant find libgpod on repositories

---

### Post by angkor on 2006-04-09
[QUOTE=darksc00by]it says i dont have libgpod or libgpod0 installed. and i might need updated repositories then? cause i installed it from repositories... and i cant find libgpod on repositories[/QUOTE]

Are you on Breezy or Dapper? I'm using Dapper right now and the package in the repos is:

```
apt-cache search libgpod
libgpod-dev - a library to read and write songs and artwork to an iPod
libgpod0 - a library to read and write songs and artwork to an iPod
libgpod-common - a library to read and write songs and artwork to an iPod
```

Don't know if it's in the breezy repositories as well. I'll check later.

---

### Post by angkor on 2006-04-09
Couldn't find it in the standard Breezy repositories either.
You can always get the source here:

[http://www.gtkpod.org/libgpod.html](http://www.gtkpod.org/libgpod.html)

Or download a .deb here:

[http://www.ubuntuforums.org/showthread.php?t=104937&highlight=libgpod](http://www.ubuntuforums.org/showthread.php?t=104937&highlight=libgpod)

(at the bottom of the page someone posted gtkpod and libgpod .debs)

And see if you can install the package.

```
sudo dpkg -i libgpod_0.3.0-1_i386
```

---

