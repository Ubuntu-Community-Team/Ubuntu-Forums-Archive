---
title: "Easy Ubuntu"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by an4rew on 2008-02-29
Its been a while since i used Ubuntu... i used to use scripts like Easy ubuntu or Automatix but these seem obsolete now.

Is there a new easy way of doing things?

---

### Post by jan quark on 2008-02-29
> Is there a new easy way of doing things?

what do you want to do?

[B]I strongly advice you not to use automatix
it is know to cause severe damage and heavy compatibility issues[/B]

---

### Post by Oldsoldier2003 on 2008-02-29
> **an4rew said:**
> Its been a while since i used Ubuntu... i used to use scripts like Easy ubuntu or Automatix but these seem obsolete now.

Is there a new easy way of doing things?
Automatix is still around but it's use is ***_highly_*** discouraged.

---

### Post by Het Irv on 2008-02-29
If you are looking to install programs, .deb's and Synaptic are the easiest ways.

---

### Post by an4rew on 2008-02-29
I'm looking to setup graphics and install flash, play mp3.

thanks.

---

### Post by xeth_delta on 2008-02-29
> **an4rew said:**
> Its been a while since i used Ubuntu... i used to use scripts like Easy ubuntu or Automatix but these seem obsolete now.

Is there a new easy way of doing things?

If what you want is install programs, it couldn't be easier. If you want a graphical interface you can use synaptic (for Gnome) or adpet (for KDE).

There is always the posiblity to use the command line. To search for programs:
```
aptitude search package_name_or_word_in_short_description
```
or
```
apt-cache search  package_name_or_word_in_short_description
```
To install:
```
sudo apt-get install package_name
```
or
```
sudo aptitude install package_name
```

---

### Post by jan quark on 2008-02-29
for flash and mp3 run this in terminal

```
sudo apt-get install flashplugin-nonfree ubuntu-restricted-extras -y
```

---

### Post by forrestcupp on 2008-02-29
For video drivers, it couldn't be any easier than the include Restricted Drivers Manager.  But if you need newer drivers than what is in the repos, try [Envy](http://albertomilone.com/nvidia_scripts1.html) for the latest nvidia and ATI drivers.  Envy is like Automatix2 for video card drivers, only Envy is not discouraged.

---

### Post by aysiu on 2008-02-29
> **an4rew said:**
> I'm looking to setup graphics and install flash, play mp3.

thanks.
This tutorial will explain how to do that:
[http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree)

---

