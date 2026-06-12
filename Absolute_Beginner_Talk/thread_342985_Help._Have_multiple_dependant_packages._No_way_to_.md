---
title: "Help. Have multiple dependant packages. No way to find them all"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Statik on 2007-01-20
Hi all,

I was trying to follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=294007&highlight=how+to+cinelerra") on how to install cinelerra. In the process, a ton of -dev packages got uninstalled, along with some of my other programs. Now that I'm trying to re-install those programs, I'm finding a long chain of dependant packages and I can't seem to find a root that will allow me to start the install. Is there an easy way to fix this? I have tons of stuff not working and I didn't even get cinelerra out of the deal.

Any help appreciated.

Statik

---

### Post by Ecthelion on 2007-01-21
> Now that I'm trying to re-install those programs, I'm finding a long chain of dependant packages and ...

How are you trying to install those programs?
If you are using synaptic, select them and each time a window should popup asking telling that if you select that package, the dependencies of it will also be selected...

> ... I can't seem to find a root that will allow me to start the install
What do you mean?
If you do System > Admininstartion > Synaptic package manager then you'll have to give in the root password and thus you will be root...
Or do you mean something else?

---

### Post by Statik on 2007-01-21
I am using synaptic to install the programs. When I select the program I want to install, it says it requires such-and-such a package and WILL NOT INSTALL. So, I search that package, and try to install it, and it has another package it requires and WILL NOT INSTALL. I keep this up for 5 or 6 'links' in the 'chain' never arriving at a single package that will install. The root I mean is a package at one end of the chain that will allow the next to install, and the next and the next on up to the original program I wanted.

After several hours of frustration I tried to install Edgy. This has always failed before, but I had nothing to lose. Now that it has installed, I tried to install one of the programs, gnucash, and it seems to be working. The only package it wanted to remove was linux-kernal-headers. I'm still looking into how necessary that package is, but I know I need gnucash so I'm ok so far.

Wish I knew what happened there to break the chain. I'm so used to synaptic being able to install the required packages for me. This time it had lists of programs to remove that was over 100 items long. Mostly -dev packages, but still, many. I'm still reinstalling the programs I wanted, but things seem to be going ok now.

Thanks again,

Statik

---

