---
title: "nvidia-glx-src, nvidia-kernel-scr problem"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by medley on 2007-01-11
I am unable to install nvidia-glx because it fails on a 'nvidia-glx-src' conflict. Adept won't let me install it. If I try from the terminal it tells me that I have 'unmet dependancies, nvidia-glx depends nvidia-kernel-1.0.9742'. I've tried installing 9742 from nvidia-linux-x86-1.0-pkg1.run, but that tells me I have an X server running. When I stop X, and kill KDM, it tells me that I have a kernel source problem (can't remember exactly the text of this one; I'd have to kill off X and would lose this post). Can anyone tell me how to fix this dependancy problem?

Thanks

---

### Post by rai4shu2 on 2007-01-11
You need to remove nvidia-glx-src, and don't try to install the latest nVidia driver unless you don't mind the problems (like possible crashing in Wine).

---

### Post by medley on 2007-01-11
I cannot remove nvidia-glx-src because I can't find it. It is not showing up in the apt database, nor can I find it in any of my repositories. If I do a find on my system, it is not there. Any other ideas?

---

### Post by rai4shu2 on 2007-01-11
Go to konsole and type:

sudo apt-get remove nvidia-glx-src
sudo apt-get install nvidia-glx

---

### Post by medley on 2007-01-11
> **rai4shu2 said:**
> Go to konsole and type:

sudo apt-get remove nvidia-glx-src
sudo apt-get install nvidia-glx

No joy. It says that nvidia-glx-src was not installed so can't be removed. This has been my problem; I can't find the stinking src file. BTW, the install didn't work either.

---

### Post by rai4shu2 on 2007-01-11
What does it say when you try to install?

---

### Post by medley on 2007-01-11
> **medley said:**
> No joy. It says that nvidia-glx-src was not installed so can't be removed. This has been my problem; I can't find the stinking src file. BTW, the install didn't work either.

Is now an inappropriate time to refer the readers to my previous rant about 'Linux will never win the Desktop!!!"?

:twisted:

---

### Post by rai4shu2 on 2007-01-11
Never is a long long time.

---

### Post by medley on 2007-01-12
> **rai4shu2 said:**
> Never is a long long time.

I know...I was just trying to get some attention ;)

---

### Post by medley on 2007-01-12
Still haven;t got this figured out...any more suggestions?

---

### Post by rai4shu2 on 2007-01-12
What does it say when you try to install?

---

### Post by medley on 2007-01-12
> **rai4shu2 said:**
> What does it say when you try to install?

When I try to install nvidia-glx from konsole, it says

nvidia-glx: depends: nvidia-kernel-1.0-9742
E:Broken packages

---

### Post by medley on 2007-01-12
> **medley said:**
> When I try to install nvidia-glx from konsole, it says

nvidia-glx: depends: nvidia-kernel-1.0-9742
E:Broken packages

Also, for the record, if I try to apt-get install nvidia-kernel-1.0-9742, it says it can't find the package, which would suggest I don't have the correct repository in sources.lst. Where would I find this?

---

### Post by medley on 2007-01-12
Bump

---

### Post by rai4shu2 on 2007-01-12
In my experience, 9742 is too flaky for general use. The 96xx is okay if you need it for Beryl/Compiz. You should either find a good repository for a 96xx driver or stick with the driver in the official repo.

---

