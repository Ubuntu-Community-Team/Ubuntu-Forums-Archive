---
title: "install a bunch of deb packages all at once"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Xorg.conF on 2007-12-23
Ok I just formatted my 2 partitions and I now have a fresh install with all my programs gone.  Luckily I used APTonCD and it coped them all to a directory.  Great so I have all 240 packages just sitting there waiting for me to use apt-get install for every time I need one of then installed, it will just install it locally with no downloading.  But It will take forever for me to install them through the manager, so I'm asking for a way, possibly a command I can use that will automatically  install  multiple .deb packages from a directory with me having to do as little as possible.  


THX for all the help.

---

### Post by Rocket2DMn on 2007-12-23
According to man dpkg
> dpkg -i | --install package_file...
              Install the package. If --recursive or -R option  is  specified,
              package_file must refer to a directory instead.
So if you put the cd in, running this might work:
```
sudo dpkg -i -R /media/cdrom0
```
assuming /media/cdrom0 is your disc drive.

---

### Post by jaybombalous on 2007-12-23
> **Rocket2DMn said:**
> According to man dpkg

So if you put the cd in, running this might work:
```
sudo dpkg -i -R /media/cdrom0
```
assuming /media/cdrom0 is your disc drive.


very nice, I will have to remember this trick in the future.

---

### Post by TheOm3ga on 2007-12-23
Doing dpkg -i * in the directory where the .deb files are should work.

Edit: Damn, I wasn't fast enough lol

---

