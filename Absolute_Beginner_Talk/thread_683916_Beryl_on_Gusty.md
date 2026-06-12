---
title: "Beryl on Gusty"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by polomaan on 2008-01-31
How do I install Beryl on Gusty?...it looks really cool.  I didn't see it as any of the options for add/remove programs, so I went to the Beryl webpage and saw 10 or so .tar files which I could download.  What are .tar files, how do I use them, and how do I get Beryl on my system?  If there's another way please let me know.  I am going for simplicity.  I am dual booting Vista and Ubuntu Gusty (7.).  I have an intel GMA graphics "card".  Let me know if any more info is necessary.  Thanks!

---

### Post by LowSky on 2008-01-31
Compiz Fusion has replaced Beryl

Gutsy comes with Compiz already installed, to add the same effect your seeing with Beryl

```
sudo apt-get install ccsm
```

the willl create a menu you can get to from System>Preferences> Advanced Desktop settings

---

### Post by Alx c on 2008-01-31
I know this isnt ansewirng your question but get compiz fusion, its berly with compiz (a wicked theme) and if you find a .deb package download that one, it installs automaticly, .tar ones you need to use terminal witch is a bit of a bother.

---

### Post by Crumpets and Jam on 2008-01-31
> **LowSky said:**
> Compiz Fusion has replaced Beryl

Gutsy comes with Compiz already installed, to add the same effect your seeing with Beryl

```
sudo apt-get install ccsm
```

the willl create a menu you can get to from System>Preferences> Advanced Desktop settings

Can you use Emerald themes using this technique?

---

### Post by polomaan on 2008-01-31
Thanks for the great replys.  I will type sudo apt-get install ccsm into the terminal and all will be good....or so I hope.  Getting wireless to work with my card was ....er, a learning experience, haha.  Do you reccommend any other software to enhance the experience?  I have not made the complete switch from vista, but still trying it out...

---

### Post by LowSky on 2008-01-31
well if you want to run MP3s and DVDs you will need to do a bit more installing

just copy and paste all this into terminal and it will get every thing working, or at least should

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

```
sudo apt-get install libdvdcss2

```

```
sudo apt-get install w32codecs

```

if you want to check out some free programs check out Add/remove under programs

---

### Post by sk1pp3r on 2008-02-01
I tried installing the ccsm but this is what I got:

sk1pp3r@HP:~$ sudo apt-get install ccsm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ccsm
sk1pp3r@HP:~$ 

I'm new at this whole thing.  Any help would be greatly appreciated.  Do I need to add another repository to my sources list.  I did the medibuntu one but thats all. This is also the first thing I have tried from a fresh install.
Thanks again!

---

### Post by emarkd on 2008-02-01
Yeah, you got some well-meaning but incomplete advice.  The software we refer to as ccsm is actually installed by running:

```
sudo apt-get install compizconfig-settings-manager
```

You can also find it through Synaptic if you want to avoid the command line.  That's under System > Administration > Synaptic Package Manager

---

### Post by bpasham on 2008-02-17
> **LowSky said:**
> 
```
sudo apt-get install w32codecs

```

if you want to check out some free programs check out Add/remove under programs

instead of win32codecs use **non-free-codecs**. This will work for both x86 and 64bit computers as well.

As suggested try using Synaptic package manager.

---

