---
title: "How to verify the update from 7.04 --&gt; 7.10?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by jonnan on 2007-10-21
In a blaze of idiocy, I upgraded my house 'server' (Ie, an old system with Samba on it that store the windows installs/patchs for the rest of the household and downloads torrent files. Not a server in terms of any competent linux user I'm sure - <G>) and it proceeded to go through, eventually crashing, ejecting a number of items as not upgradable, and explaining that my computer may not be in a usable condition.

On reboot, I fiddled around with apt-get, and got it to reinstall synaptic and aptitude, and upgraded some timezone data, and now it acts like it has upgraded perfectly happily doesn't know what I'm talking about when I try to find out what went wrong. 

Much as I would love to trust it's happy attitude, since It kicked out a couple dozen errors, I find it odd that it's happy and joyful now. Is there any simple way to verify the information against something to see what may still be waiting to bite me, or should I just be happy the gods were kind in punishing me, back everything up, and reinstall from ISO?

Skill Level ~ marginally competent, can run sed and some bash - <G>

Thanks - Jonnan

---

### Post by ruibernardo on 2007-10-21
Don't mess with it if it is happy, but if apt failed anywhere, you could try

```
 sudo apt-get -f install
```to end some package installation that didn't finish, or

```
 sudo dpkg-reconfigure -a

```Just use this last one if apt or dpkg tell you to (when you try "apt-get update" or install something). Don't use it if it don't (it may take a while to complete)

---

### Post by jonnan on 2007-10-21
It *acts* as if it's happy now - It just bothers me that it acted dead in the water, I reinstalled two things that had nothing to do with the errors I was getting, and now it's acting like there was never an issue.

Bluntly, I'm neither that smart nor that lucky - <G>

Jonnan

---

