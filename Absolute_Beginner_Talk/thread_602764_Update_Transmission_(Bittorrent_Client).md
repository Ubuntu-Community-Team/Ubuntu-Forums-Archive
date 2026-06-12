---
title: "Update Transmission (Bittorrent Client)"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Kaji on 2007-11-04
Ok, I have the old version (.72 i believe) from the repositories. The newest version is 0.91 (i believe) I have tried updating and all the time it failed at one point or another.

Any help out there Ubuntu brethren?

Thanks,
Kaji.

---

### Post by lolindrath on 2007-11-04
Hi Kaji,

0.72 seems to be the newest in the repository, you can alway download and compile the latest version, just make sure you do:

```
sudo apt-get build-essential libssl-dev libgtk2.0-dev
```

Once you have the source code extracted you would do:

```

./configure
make
sudo make install

```

--Lolindrath

---

### Post by wounded on 2007-11-05
[http://www.getdeb.net/app.php?name=Transmission](http://www.getdeb.net/app.php?name=Transmission)

Or you can install the .deb :)

---

