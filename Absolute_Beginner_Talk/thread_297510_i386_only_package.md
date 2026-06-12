---
title: "i386 only package"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by rlowrance on 2006-11-11
I am trying to install Emacs 21 (x11) on my ubuntu 6.10 edgy eft system, which is an IBM Thinkpad. Add/Remove Applications tells me that its for i386 systems only and will not install it.

What's gone wrong? 

How do I install and run emacs 21?

Thanks, Roy

---

### Post by Ecthelion on 2006-11-11
Check if your architecture is on [this page]("http://packages.ubuntu.com/dapper/editors/emacs21")

If it's not, then I'm afraid that you have a problem...
Only compiling from source is possible then.
You can download the source code [here]("http://packages.qa.debian.org/e/emacs21.html"), but please only do it if you have no other option. Also make sure to download the right source code: make sure you don't get anything of unstable

If there is a package for your architecture then you can download it.
Install the downloaded package by doing:
```
sudo dpkg -i <path to the location of the .deb package>
```
It is possible that you get an error saying you need some dependencies, which you have to install...

---

### Post by rlowrance on 2006-11-11
Thanks. Chased the link you suggested and found that there is an i386 package in emacs21-bin-common. But the repository must be coded incorrectly. Is there a way around this problem?

---

### Post by Ecthelion on 2006-11-12
> Thanks. Chased the link you suggested and found that there is an i386 package in emacs21-bin-common. 

The link I gave was to emacs21---you can download emacs21 on that page---
emacs21-bin-common is only a dependencie of emacs21, just like all the other things on that page that have a red bullet left of them...
This means that in order to install emacs21, you have to have these things installed (emacs21-bin-common; libc6; libice6; ...)

That is why it's so usefull to use Synaptic Package Manager...
When you select a package to install,synaptic package manager selects automatically all the dependencies of that program.
(Did you tried Synaptic? Because you speak of add/remove programs but not of synaptic...)(Synaptic can be found in System > Administartion > Synaptic package manager, maybe you should try this first before continuing)

Back to manually installing everything (I hope you don't need to do it...)
So you have to download emacs21 (on the page I found you, at the bottom), follow the links to emacs21-bin-common etc to download those too (you better check with synaptic if none of them is already installed, so you don't install them twice)
But all those .deb files in a empty dir and do
```
sudo dpkg -i <path to the dir and then *>
```
<path to the dir and then *>  for example, for me that would be
/home/ecthelion/debian-temp/* (if i had put those files in ~/debian-temp/)

I hope this helps...
If anything isn't clear, please ask before trying...

---

### Post by Ecthelion on 2006-11-12
> But the repository must be coded incorrectly. Is there a way around this problem?

What do you mean exactly? "coded incorrectly" ?

---

### Post by Sef on 2006-11-12
emacs can be downloaded via synaptic.

---

