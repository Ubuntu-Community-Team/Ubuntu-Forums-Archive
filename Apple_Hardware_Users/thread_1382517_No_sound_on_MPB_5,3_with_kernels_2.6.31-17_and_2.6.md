---
title: "No sound on MPB 5,3 with kernels 2.6.31-17 and 2.6.31-18"
date: 2010-01-16
forum: Apple Hardware Users
---

### Post by WindPower on 2010-01-16
Hi, I've been using the [instructions on the Wiki](https://help.ubuntu.com/community/MacBookPro5-3/Karmic#Sound) to compile audio drivers for the Macbook Pro 5,3, and it has worked for a while. But I tried doing the same thing with kernels 2.6.31-17 and 2.6.31-18, but it seems to have no effect: alsamixer only shows one channel (Master) which does nothing, just like a fresh install.
Does anyone have updated instructions for these kernels?

---

### Post by linuxopjemac on 2010-01-17
If you installed the backports alsa module I would expect the backports module to automatically adapt the kernel module after a kernel update, at least, that's my understanding of a backport module.

you might want to check which alsa version you are running in all the different kernel versions:


```
cat /proc/asound/version
```

I am on Advanced Linux Sound Architecture Driver Version 1.0.20 _without_ the backport in Karmic.

If you see different versions with the backport, it should be reported as a bug report I guess.

---

### Post by linuxopjemac on 2010-01-17
what you can do for the newer kernels is to compile the alsa module yourself. You can follow the same wiki

> Only try this if the above steps did not work for you

The following needs to be re-run each time new kernel is installed. (you can save it as a script in your home directory as "reinstall_alsa.sh" ):

```
sudo rm -rf /lib/modules/`uname -r`/kernel/sound
sudo aptitude reinstall linux-headers-`uname -r` linux-image-`uname -r`
rm alsa-driver-snapshot.tar.gz
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz
tar xf alsa-driver-snapshot.tar.gz
cd alsa-driver
sudo ./configure --enable-dynamic-minors --without-oss --with-cards="hda-intel"
sudo make
sudo make install

```
Reboot.

And then, install gnome-alsamixer

sudo apt-get install gnome-alsamixer

and run gnome-alsamixer in a terminal. Unmute and raise the volume to 100% for "frontspeaker" and "surround" (which enables the bass speaker). For some reason it is not possible to change these from the standard volume control.

Warning: future kernels may not play well with this fix. Hopefully this will be updated if something breaks

PS how can you be in 2.6.31-18? I have an updated version of Karmic Koala and I am on 2.6.31-17....

---

### Post by WindPower on 2010-01-17
Apparently the wiki was updated between my post and your reply. Only the compilation instructions were there before.
So I tried installing the linux-backports-modules-alsa-karmic-generic package and it fixed the sound... for kernel 2.6.31-17 only. I still have no sound for 2.6.31-18.
I also tried the compilation instructions again, and still no sound.
```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Jan  9 2010 for kernel 2.6.31-18-generic (SMP).
```
The 2.6.31-18 kernel is in the karmic-proposed repository :o

---

### Post by linuxopjemac on 2010-01-17
1.0.22.1 is the latest version, that's all I know. It should work with that one. Stupid question, but did you unmute everything with alsamixer?

---

### Post by WindPower on 2010-01-17
> **linuxopjemac said:**
> 1.0.22.1 is the latest version, that's all I know. It should work with that one. Stupid question, but did you unmute everything with alsamixer?

As said in the first post, alsamixer reports only one sound channel rather than the usual half-dozen that there are on the other kernels. I've set that channel to 100%, without effect.

---

### Post by proycon on 2010-01-18
I have the same issue, on 2.6.31-17 .. Compiling alsa from scratch didn't work for me like it used to with earlier kernel upgrades, but the backports package that was mentioned fortunately does fix the problem for me.

---

### Post by viktara on 2010-01-19
Same here - the backports package works with 2.6.31-17 but the snapshot doesn't seem to.

---

### Post by emrys on 2010-02-26
Any advances here or we are stuck with .17?

In .18, .19 and .20 still no sound.

Tried the backports and compilation with no luck.

In my case, AlsaMixer shows nothing.

---

### Post by WindPower on 2010-02-26
The backport module did work for me on .19 (but not any other)

---

