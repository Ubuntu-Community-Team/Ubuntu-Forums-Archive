---
title: "Helping noobs to use ipodlinux in Ubuntu"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by vfm on 2007-01-04
Hi there... i'm trying to use ipodlinux in my ipod 5g 30g (The new ipod 5g isn't supported by the ipodlinux installer in any OS)

But seems that the installer for windows and linux cant detect the ipod .
The installation guid provided by the wikipodlinux community seems good ([http://ipodlinux.org/5g#Linux_Installation](http://ipodlinux.org/5g#Linux_Installation) )... but only to people that are kinda advanced in linux.

I tried to follow the guide but there are some commands that don't work in ubuntu (edgy).
If possible.. any of you ubuntu experts could review the installation guide and publish a installation guide for ubuntu. (i searched a lot in here but just cant that much things about ipodlinux in ubuntu).

If anyone helps it could really help the ipodlinux community and people like me (i've seen tons of people with the same problem).

Ill keep trying!!!! But it would be better if somebody more advanced could help!

Happy new year for everyone!
Thanks in advance ppl!
(ubuntu is getting better than windows 'cause of its simplicity...now let's just make it simpler)

---

### Post by pay on 2007-01-04
Most of the commands would require you to be the superuser. Try ```
sudo su
```beforehand. Other than that it doesn't seem to hard, just read through it a few times. Make sure that you have the required tools```
sudo aptitude install build-essential fdisk
```

---

### Post by vfm on 2007-01-04
what about the svn cant put it workin 

and the Nightly kernel builds... cant figure it out... do i need to download it?

what should i do with it?

---

### Post by pay on 2007-01-04
To download svn you need to install subversion```
sudo aptitude install subversion
```Yeah it wants you to download a nightly build

---

