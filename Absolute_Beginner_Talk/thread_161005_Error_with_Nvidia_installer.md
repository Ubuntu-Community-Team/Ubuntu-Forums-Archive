---
title: "Error with Nvidia installer"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by Goatee on 2006-04-16
I've got a new machine and i'm trying to go 100% penguin.
I downloaded Breezy (AMD64)
New default install.
X server doesn't go but i'm not surprised (2*6600GT in SLI)
Download NVIDIA driver start to install and I get...

Error: Unable to find the system utility 'ld' please make sure you have the package 'binutils' installed. If you do have 'binutils' installed, then please check that 'ld' is in your PATH.

:confused: 

I think that binutils is a pretty essential bit of system kit and I think it's been installed (correct me if i'm wrong).

The PATH?
Stumps me.

Little help?
Thanks in advance :-D

---

### Post by akiro.yamamoto on 2006-04-16
Hmmm....
[**CLICK ME!!!**](http://ubuntuforums.org/showthread.php?t=75074)
That is a fairly comprehensive NVidia install guide.....
Hope it helps ;)

---

### Post by dermotti on 2006-04-16
So nvidia-glx doesnt work?

---

### Post by akiro.yamamoto on 2006-04-16
To set up a basic X system use:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
This should enable a basic x set-up automatically that you can use until you get your 3D set-up configured.
Hope this info helps ;)

---

### Post by Jason_25 on 2006-04-16
That error occurs because you don't have everything you need to build from source.
```

sudo apt-get install build-essential

```
will get you started.

---

### Post by dermotti on 2006-04-16
I have a question though. Why does everyone want to compile the nvidia driver? With both my systems with Nvidia 6600gt and a 6200, i just downloaded the **nvidia-glx** package, and 3d worked fine....

Do you  need to compile to run SLI or something?

---

### Post by Goatee on 2006-04-16
[QUOTE=dermotti]I have a question though. Why does everyone want to compile the nvidia driver? With both my systems with Nvidia 6600gt and a 6200, i just downloaded the **nvidia-glx** package, and 3d worked fine....

Do you  need to compile to run SLI or something?[/QUOTE]
Well It didn't go 'out of the box' and i'm x86_64

---

### Post by dermotti on 2006-04-16
So you tried installing **nvidia-glx** and run **sudo dpkg-reconfigure xserver-xorg** afterrwards? Alwyas works for me.....but its possible it an AMD thing i guess...

---

### Post by Jason_25 on 2006-04-16
[QUOTE=dermotti]So you tried installing **nvidia-glx** and run **sudo dpkg-reconfigure xserver-xorg** afterrwards? Alwyas works for me.....but its possible it an AMD thing i guess...[/QUOTE]
The current driver in breezy is ancient.  It doesn't support sli at all.

---

### Post by Goatee on 2006-04-16
I have got ANOTHER error...

so I have a question...

How do you set the cc environment variable to gcc 3.4

I have no net connection on that machine.

---

### Post by dermotti on 2006-04-16
Ahh, im using dapper :-P very new driver included.

---

### Post by Jason_25 on 2006-04-16
[QUOTE=Goatee]I have got ANOTHER error...

so I have a question...

How do you set the cc environment variable to gcc 3.4

I have no net connection on that machine.[/QUOTE]

```

CC=gcc-3.4
export CC

```

Make sure you apt-get gcc-3.4 first.

---

### Post by Goatee on 2006-04-16
Make sure you apt-get gcc-3.4 first.[/QUOTE]

How do you apt get without the net on that machine?

---

### Post by Jason_25 on 2006-04-17
Well you can go through the complicated process of setting up a local or cd repository or you can just grab the debs that you need from archive.ubuntu.com

---

