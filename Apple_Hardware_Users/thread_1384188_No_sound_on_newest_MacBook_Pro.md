---
title: "No sound on newest MacBook Pro"
date: 2010-01-18
forum: Apple Hardware Users
---

### Post by MrEbert on 2010-01-18
I've recently made my new (unibody) MacBook Pro Core 2 Duo dual boot between Mac and Ubuntu, and almost everything works great except the sound, which is completely absent.  I'm pretty new to Linux so I do not know how to fix something like this.  Could somebody help?

---

### Post by linuxopjemac on 2010-01-18
try the backported alsa module first, from the wiki:

Sound works for me on a mbp 5,4 and 5,5 after installing the ALSA modules backports package and unmuting the front speakers. To install the modules for the default kernel, run:

```
  sudo apt-get install linux-backports-modules-alsa-karmic-generic
```

Restart the computer. linux-backports-modules-alsa-karmic-generic is a meta-package and will ensure an automatic module upgrade when Ubuntu upgrades the linux kernel package.

To unmute the front speakers run alsamixer from the Terminal, or use gnome-alsamixer:

  sudo apt-get install gnome-alsamixer

In gnome-alsamixer you should obtain something like that:

To enable the optical output, check the IEC958 option, and you'll see a red light coming from your headphone jack.

Only do this if the linux-backports-modules-alsa package does not work:

Should the backports package not work on your machine, even newer ALSA drivers may be worth trying. Compare the version numbers in the backports package and the latest snapshot at the ALSA project page. If you want to upgrade manually, download the latest snapshot from [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz) and unpack it wherever you want. Then build it with these commands in the Terminal:
```

  cd alsa-driver # cd to the right directory of course
  ./configure --enable-dynamic-minors  --without-oss --with-cards="hda-intel"
  make
  sudo make install
```

After the build is complete, restart your computer.

Warning: You have to rebuild the kernel module using the commands shown above every time you upgrade the kernel.

If sound does not works again

    * Remove gnome-alsamixer and linux-backports-modules-alsa-karmic-generic 

```
  sudo apt-get remove gnome-alsamixer
  sudo apt-get remove linux-backports-modules-alsa-karmic-generic
```

type the command:

```
  uname -r
```

    * it returns your kernel release, for me: "2.6.31-17-generic-pae" Now you can reinstall linux-backports-modules like this: 

```
  sudo apt-get install linux-backports-modules-"your kernel release"
```

    * So for me, ```
"sudo apt-get install linux-backports-modules-2.6.31-17-generic-pae"
``` And just reinstall gnome-alsamixer: 
```

  sudo apt-get install gnome-alsamixer
```

    * You should now have the good alsamixer, just configure it and it should works.

Original link: [https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Sound](https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Sound)

---

