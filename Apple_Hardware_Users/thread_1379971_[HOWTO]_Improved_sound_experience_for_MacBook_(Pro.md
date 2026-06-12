---
title: "[HOWTO] Improved sound experience for MacBook (Pro) 5,1 / 5,2"
date: 2010-01-13
forum: Apple Hardware Users
---

### Post by alexmurray on 2010-01-13
Whilst sound works for MBP5,1 / 5,2 under Karmic, it could definitely be better - mainly the master volume does not affect the headphone output, and the speakers don't automute when headphones are plugged in.

However, I've finally got around to writing a [patch]("http://dl.dropbox.com/u/174251/alsa-driver-1.0.22.1-mb5.patch") for alsa which fixes this - the patch is against the latest version of alsa-drivers (1.0.22.1).

If you want to test it (since so far I've only tested it on my MBP5,1 - any feedback from MacBook 5,1 / MB(P) 5,2 owners would be great too) follow these instructions: 

First make sure you don't have any versions of linux-backports-modules-alsa installed:
```

apt-cache --names-only search linux-backports-modules-alsa | cut -f 1 -d ' ' | xargs sudo apt-get remove --purge

```

Now download alsa driver source and the patch, and compile and install a patched version of the driver:
```

cd ~
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.1.tar.bz2
wget http://dl.dropbox.com/u/174251/alsa-driver-1.0.22.1-mb5.patch
tar xjf alsa-driver-1.0.22.1.tar.bz2
patch -p0 < alsa-driver-1.0.22.1-mb5.patch
cd alsa-driver-1.0.22.1
./configure
make
sudo make install

```

Now you need to reboot your machine and can enjoy the awesomely improved sound goodness!

---

### Post by linuxopjemac on 2010-01-13
can you send this patched Alsa to the Alsa team, hopefully it will end up there.

---

### Post by alexmurray on 2010-01-13
Just sent it upstream now to [alsa-devel]("http://mailman.alsa-project.org/pipermail/alsa-devel/2010-January/024465.html").

---

### Post by linuxopjemac on 2010-01-14
Great work Alex!

---

### Post by alexmurray on 2010-01-14
This just got accepted [upstream]("http://git.kernel.org/?p=linux/kernel/git/tiwai/sound-2.6.git;a=commit;h=a76221d47ef2b73ff16c0fef00a784026308ea02") so should be available in the 2.6.33 kernel (unfortunately lucid won't ship this, but hopefully by then linux-backports-modules-alsa will contain this patch).

---

### Post by linuxopjemac on 2010-01-15
Nice to hear that your patch was accepted.

---

### Post by Aybara on 2010-02-01
I also have an MBP5.1, but I still want to say this works great and offer my humble thanks :)

---

### Post by butters014 on 2010-02-04
I have a MBP5.1 as well and this worked wonders. Thanks a lot, I tried a ton of different thinks with no success.

---

