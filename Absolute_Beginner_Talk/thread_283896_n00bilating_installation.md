---
title: "n00bilating installation"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by GOLDfish_74 on 2006-10-24
I am trying to install a program from a tar.gz I have downloaded but I have tried using synaptic to install it from the tar.gz file but when I try nothing happens. Any insight into how I can install the program having extracted the tar.gz myself?

Thanks,
Sir n00b.

---

### Post by deepwave on 2006-10-24
Hehe... Synaptic is not used for installing tar.gz.  It installs pre-made packages called debs specific to Ubuntu to Debian.

In your case, read the readme in the extracted folder.  You may need to compile or run a script to get the program running, depending on the file.

A running of a script is done:
sh ./run_scripty.sh (in console)

A basic compile is done via:
configure
make
make install (sudo this for a global installation)
You will need to install a few tools off Synaptic.  Off the top of my head: build-essentials, gcc, make.

Most of the popular programs can be searched for and installed right in Synaptic.

---

### Post by CatKiller on 2006-10-24
[How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/"):
A graphical guide for all new users with a Windows background using Ubuntu

---

### Post by GOLDfish_74 on 2006-10-24
I looked at that tutorial, and following the instructions was pretty useless. I have an instal.pl file in the main dir. I also have some .sh files scattered around. I tried running one and it referred me to another, so I ran that one and it responded with:

```
Usage: Installer.sh {kind|version|converdb|uninstall}
```

What could that mean?

GOLDfish!

---

### Post by CatKiller on 2006-10-24
> **GOLDfish_74 said:**
> What could that mean?
That could mean that you should read the instructions that came with the download if you are going to install random stuff that you found on the Internet.

---

### Post by GOLDfish_74 on 2006-10-24
> **CatKiller said:**
> That could mean that you should read the instructions that came with the download if you are going to install random stuff that you found on the Internet.

You know that's good in theory, but the instructions provided were "Unpack and Install"

How helpful are those instructions... especially for a n00b like myself.

---

### Post by CatKiller on 2006-10-24
> **GOLDfish_74 said:**
> You know that's good in theory, but the instructions provided were "Unpack and Install"

How helpful are those instructions... especially for a n00b like myself.

That's a fair point, I suppose. What is it you're trying to install? It's possible that it's in the repositories, or someone knows where there's a .deb. Or there might be a file called README. There's supposed to be one in everything, but I did find one the other day that hadn't bothered.

---

