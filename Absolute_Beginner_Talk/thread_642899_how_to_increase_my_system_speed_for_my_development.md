---
title: "how to increase my system speed for my development work"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-12-17
how to increase my system speed for my development work .
i opend sudo services-admin
there is some services are listed.
my requirement is  i want to open only one IDE(Aptana) and one browser(Mozila Firefox)
whichever processes i can deny which is not used for above requirement (from service-admin).  

my os ubuntu 7.10
my architecture is
Linux pearl 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux with (512 MB RAM)
my processor is  Intel(R) Pentium(R) D CPU 3.00GHz

---

### Post by Chayak on 2007-12-17
Well you're not really hurting for ram and most of the processes that are running by default don't hog the processor to the point where you would notice anything.  You could always switch to a lightweight desktop like XFCE and Xubuntu.  That would probably do more than just killing processes.

---

### Post by mokkai on 2007-12-17
> **Chayak said:**
> Well you're not really hurting for ram and most of the processes that are running by default don't hog the processor to the point where you would notice anything.  You could always switch to a lightweight desktop like XFCE and Xubuntu.  That would probably do more than just killing processes.


how to switch to a lightweight desktop like XFCE and Xubuntu ?.

---

### Post by LaRoza on 2007-12-17
> **mokkai said:**
> how to switch to a lightweight desktop like XFCE and Xubuntu ?.

```

sudo aptitude install xfce

```

When you log in, check "Xfce" in "Sessions"

---

### Post by chris4585 on 2007-12-17
yeah or even fluxbuntu, it is sexy, you might even want to switch your file manager to pcman or something else that doesnt use as much processes

---

### Post by mmb1 on 2007-12-18
Be aware, though that installing xfce will take up a little chunk of space of your hard drive, you may want to look at this thread:

[http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192)

---

### Post by MangasColoradas on 2007-12-18
> **LaRoza said:**
> ```

sudo aptitude install xfce

```

When you log in, check "Xfce" in "Sessions"

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
[B]Couldn't find package "xfce", and more than 40
packages contain "xfce" in their name.[/B]
The following packages are unused and will be REMOVED:
  ladcca2 libbinio1c2 libfluidsynth1 libgsf0.0-cil libjack0.100.0-0 libmcs1 
  libresid-builder0c2a libsamplerate0 libsidplay2 libwv-1.2-3 
0 packages upgraded, 0 newly installed, 10 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 2097kB will be freed.
Do you want to continue? [Y/n/?]

---

### Post by mmb1 on 2007-12-18
Well, due to the situation above, i think it may be a better move to install xfce through synaptic.

---

### Post by jordank on 2007-12-18
shouldn't it be the same?

---

### Post by mmb1 on 2007-12-18
DOH! My bad for having a brain fart, jordank.


Might he still be able to install by selecting specific packages, though?

---

### Post by niteshifter on 2007-12-18
I believe that should be:
```
sudo aptitude install xubuntu-desktop
```

That gets the Xcfe desktop environment completely, then one can remove what's not required - although that's not going to be much.

Easier, I think than grabbing the various xcfe* packages. However, the OP didn't say what kind of develpment work and for some things 512MB RAM could be a bottleneck. Before I'd start whacking processes (and I'd run top first to see what's grabbing my CPU) or changing desktop / session environments I'd increase the RAM - it's certainly cheap enough these days :)

---

### Post by lildeb on 2007-12-18
I would highly recommend switching window managers. You are probably running GNOME and I would switch to fluxbox. It is so much lighter on your system. You will have to learn a little about bash commands, but IMHO its really not hard to learn at all and totally worth it.

You can install fluxbox by running : 
```
sudo update-menus
```

then
```
sudo apt-get install fluxbox
```

then simply logging out and switching sessions to fluxbox





I might even suggest compiling the latest kernel. If you need a good tutorial on it, let me know. I wrote one about it and it has worked many times without fail.

---

### Post by RedSquirrel on 2007-12-30
If you just want Xfce, but not Xubuntu, the package name is **xfce4**:

```
sudo apt-get install xfce4
```


For Fluxbox you have to install it and then generate the default menu:

```
sudo apt-get install fluxbox && sudo update-menus
```

---

