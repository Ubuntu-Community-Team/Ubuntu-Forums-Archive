---
title: "[SOLVED] headphone jack not working"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by rkakkar on 2008-04-15
I have a Sony Vaio VGN-FZ240E laptop. My headphone jack isn't working, as Ubuntu still plays sound through my laptop speakers even after inserting the headphone. Any help?

---

### Post by aeiah on 2008-04-15
and in windows it switches off the internal speakers? perhaps this is normally done in software in windows, which may mean you've got two audio outputs. type 'asoundconf list' in the terminal and see if it gives you more than one soundcard

---

### Post by rkakkar on 2008-04-15
> **aeiah said:**
> and in windows it switches off the internal speakers? perhaps this is normally done in software in windows, which may mean you've got two audio outputs. type 'asoundconf list' in the terminal and see if it gives you more than one soundcard

Nope. Just one.

```
~$ asoundconf list
Names of available sound cards:
Intel

```

I think this is a Vaio-Ubuntu issue. Unfortunately Ubuntu has a looooooooooooooooooooooong way to go as far as laptop support is concerned. :(

Any other work arounds? :)

---

### Post by rkakkar on 2008-04-15
I'm not getting any sound through the headphones and continue to get sound through the internal speakers.

---

### Post by Tews on 2008-04-15
This is how I fixed the same problem for my Vaio..

```
gksudo gedit /etc/modprobe.d/alsa-base
```

And in the last line of the file, add this line:

```
options snd-hda-intel model=vaio position_fix=0
```

Make SURE that you have the latest version of ALSA installed
Follow the instructiions in this guide .. its very quick a simple..
[http://http://ubuntuforums.org/showpost.php?p=4298894&postcount=24]("http://ubuntuforums.org/showpost.php?p=4298894&postcount=24")

---

### Post by aeiah on 2008-04-15
it seems this is a recognised bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/109838](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/109838)

try
```
sudo apt-get install linux-backports-modules
```

or try what this guy did:

[http://ubuntuforums.org/showpost.php?p=3878002&postcount=6](http://ubuntuforums.org/showpost.php?p=3878002&postcount=6)

---

