---
title: "2 problems after upgrade ibook g3 from gutsy to hardy"
date: 2008-05-19
forum: Apple Hardware Users
---

### Post by TCE on 2008-05-19
There are 2 main problems i am having so far with my recent upgrade.  First of all after doing an apt-get update many of the repositories are returning with errors.  The 2nd problem is my sound has lots of noise and is greatly distorted.  Been trying to look around a little for solutions, but so far none to be found.

Thanks 
TCE

---

### Post by frog_pilot on 2008-05-19
for the changed repos, read [this thread]("http://ubuntuforums.org/showthread.php?t=784981")

for sound, please show, what driver you are using. post your /etc/modules file

---

### Post by stream303 on 2008-05-19
For sound issues, I like to take a quick peek by running alsamixer in a terminal.  Make sure that your pcm level isn't too high.  (note alsamixer m=toggle mute, b=balance, left-right, up-down keys)

Also be sure to see the release notes about the repositories in ppc:
[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

Initially I had to manually edit the /etc/apt/sources.list file too...

---

### Post by TCE on 2008-05-19
Thanks here is my /etc/modules config file

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

apm_emu
loop
sbp2
fuse
snd-powermac
snd-seq
zd1211rw
r128
i2c-dev

---

### Post by frog_pilot on 2008-05-19
your modules is ok.

often distortion comes form the pcm value

check it and make sure its beyond 70 %. Distortion should disappear then.

If the sound is too quiet after it. pump up your amp. Its a bug...

---

### Post by TCE on 2008-05-19
how to i change pcm levels I do not see that option in sound preferences or under alsamixer.  Just to let you know that thread did help me fix my repositories. Thanks for that

---

### Post by frog_pilot on 2008-05-20
> **stream303 said:**
> For sound issues, I like to take a quick peek by running alsamixer in a terminal.  Make sure that your pcm level isn't too high. 

simply type ```
alsamixer
```in a terminal

---

