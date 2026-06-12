---
title: "problems with installing OpenAL"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by Faris on 2007-09-25
hi
I am trying make OpenAL work
i tried to use s.p.m to install two packs:
libopenal0a  AND  libalut0
but s.p.m is keep showing this error message:
E: /var/cache/apt/archives/libopenal0a_1%3a0.0.8-3_i386.deb: trying to overwrite `/usr/lib/libopenal.so.0.0.0', which is also in package openal
========
by the way  i did this
sudo rm   /var/cache/apt/archives/libopenal0a_1%3a0.0.8-3_i386.deb
is that the wrong way to do it ?
========
spm (Synaptic package manager) is reporting two broken dependencies: 
libaluto AND libopen-dev
=======
my questions are:
1- how to fix the mess i made?
2- what is the best way to to get openal 
(apt-get... ,  spm , compiling the source or packs.ubuntu.com)

---

### Post by mesilliac on 2007-09-26
It sounds like you already have openal installed or partially installed somehow. To try to fix broken package installations, try typing in a terminal
```
sudo apt-get install -f
```
Apt-get and Synaptic do the same things when installing packages, just Synaptic has a nice GUI. You can also try "Fix Broken Packages" in the Edit menu of Synaptic.

The best way to get openAL was indeed through synaptic. If you install a program through synaptic that needs openAL (e.g. the python-openal package) it should install it automatically. It just seems something else got in the way.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto) might help, but post back here if you're still having trouble.

---

### Post by Faris on 2007-09-26
sudo apt-get install -f
just wont do fix it

i tried to completely remove libopenal AND libalut 
and make a fresh new install
however 
spm is still giving me the same error:
E: /var/cache/apt/archives/libopenal0a_1%3a0.0.8-3_i386.deb: trying to overwrite `/usr/lib/libopenal.so.0.0.0', which is also in package openal

---

### Post by mesilliac on 2007-09-26
That's strange, it seems you have a package called "openal" which has already installed some or all of the openal files. You can try ```
dpkg -S /usr/lib/libopenal.so.0.0.0
``` to see what the name of the package owning this file is, and then try to remove that package before continuing. I'm afraid I don't know much more about the best way of fixing this kind of problem. If noone else here can tell you the best thing to do, you might have more luck in the General Help forum :S.

---

### Post by Faris on 2007-09-26
after doing this 
dpkg -S /usr/lib/libopenal.so.0.0.0
the output is
openal: /usr/lib/libopenal.so.0.0.0
====================
i did this 
sudo rm /usr/lib/libopenal.so.0.0.0
and then tried make a new insall libopenal AND libalut
the same error pop up :
E: /var/cache/apt/archives/libopenal0a_1%3a0.0.8-3_i386.deb: trying to overwrite `/usr/lib/libopenal.so.0.0.0', which is also in package openal
=========
i just can't understand why its so difficult installing anything !!!
they told you its easy
but 
in reality it wont happen no matter who r u or what u do 
==========
  mesilliac i wanna say thanks 4 everything 
i just gave up there is nothing else 2 do 
and i dont think posting in general help will do me good

---

### Post by mesilliac on 2007-09-26
Ahh, I know there is a way to fix it because I had a similar problem once when I was testing the development version of ubuntu! But I can't remember exactly what I did to sort things out.

Most of the time installing things through synaptic is very straightforward and easy. It's not often you come across a problem like this.

There are a couple last things I think you could try:
```
sudo apt-get remove openal
sudo dpkg -C
sudo dpkg -P openal
```
Sorry I can't help more!

---

