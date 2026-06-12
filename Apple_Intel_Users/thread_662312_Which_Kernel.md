---
title: "Which Kernel?"
date: 2008-01-08
forum: Apple Intel Users
---

### Post by czechman86 on 2008-01-08
I have been having some problems with running the standard i386 kernel that is packaged with ubuntu and have been advised by members of this board, as well as friends to look at running an i686 kernel. there are several available in synaptic and was wondering if anyone had any recommendations. thanks!

Edit: further information: i have a macbook coreduo 2, 2.16ghz with 2 gigs of ram, and i purchased this computer in august of 2007, right before the santa rosa models were released.

---

### Post by cyberdork33 on 2008-01-09
if you use the default 'generic' kernel, it should actually be using a i686 kernel for you.

What kind of "problems" are you having?

---

### Post by czechman86 on 2008-01-09
just the same ones which i have posted about in the past. applications randomly quit and then the whole system shuts down. there is nothing that i can find int he logs about it.

Edit: here is a reference to what has been going on: [http://ubuntuforums.org/showthread.php?t=642149](http://ubuntuforums.org/showthread.php?t=642149)
not all random crashes give me the error however, as a matter of fact, most do not. typically the crashes will start to happen about 3 days after an install and then happen every other boot. after a few days of that, it is every boot. i love ubuntu and would love to use it as my only os on my computer. i would, if it were not for these problems. some theories that we (my cousin, and friends) have come up with regarding this issue are as this last post was about, i386 vs. i686, mods that i have made to gnome (using gtk themes or icon sets that are not up to date with gnome (ie for 2.18 instead of 2.20)) or possibly emerald (although we highly doubt that at this point in time). I see that ubuntu runs fine on many other mac systems and just would like the same for mine, so any help that you could offer would be great. thanks!

---

### Post by cyberdork33 on 2008-01-09
> **czechman86 said:**
> not all random crashes give me the error however, as a matter of fact, most do not. typically the crashes will start to happen about 3 days after an install and then happen every other boot. after a few days of that, it is every boot. i love ubuntu and would love to use it as my only os on my computer. i would, if it were not for these problems. some theories that we (my cousin, and friends) have come up with regarding this issue are as this last post was about, i386 vs. i686, mods that i have made to gnome (using gtk themes or icon sets that are not up to date with gnome (ie for 2.18 instead of 2.20)) or possibly emerald (although we highly doubt that at this point in time). I see that ubuntu runs fine on many other mac systems and just would like the same for mine, so any help that you could offer would be great. thanks!
Can you try installing without doing any "mods" as you call them? Just try to bear with the plain Ubuntu theme and see if you start getting the same effects. I would not be quick to blame the kernel since several, several other people use the same kernel (the generic kernel) on their Mac without a problem. I would, instead, think that it has something to do with some software that you are using in Ubuntu, possibly some change that you are making to a configuration file or something. What software are you typically using?

---

### Post by czechman86 on 2008-01-09
> **cyberdork33 said:**
> Can you try installing without doing any "mods" as you call them? Just try to bear with the plain Ubuntu theme and see if you start getting the same effects. I would not be quick to blame the kernel since several, several other people use the same kernel (the generic kernel) on their Mac without a problem. I would, instead, think that it has something to do with some software that you are using in Ubuntu, possibly some change that you are making to a configuration file or something. What software are you typically using?

i have done that, the only thing that i modified was the /etc/modules section, so that i could read my temperature settings with lm-sensors. i have also added some things from the macbook wiki, but i imagine that was safe to do. as far as for the programs here are my main programs of use: firefox, thunderbird, amarok, vlc, transmission, openoffice, and the terminal. the theme and all that other stuff has been left alone. furthermore, here is a copy of my etc/modules

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ndiswrapper
coretemp
applesmc
```

thanks again

also please note that i have the restricted extra package installed, but flash is not installed in ff.

Edit: Forgot to add that I also use skype, but have not installed it at this point in time.

---

### Post by cyberdork33 on 2008-01-10
Here is my /etc/modules. (Note: I am on an iMac, and also that I use ndiswrapper...)
```
$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
sbp2
hidp
```

I do realize that the applesmc and coretemp modules you probably need (and I can't use on the iMac), but I don't think the ndiswrapper line is required for it to load at every boot. 

Note, I have no idea if that is the issue, but I figure it is worth a try.

---

### Post by czechman86 on 2008-01-10
> **cyberdork33 said:**
> Here is my /etc/modules. (Note: I am on an iMac, and also that I use ndiswrapper...)
```
$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
sbp2
hidp
```

I do realize that the applesmc and coretemp modules you probably need (and I can't use on the iMac), but I don't think the ndiswrapper line is required for it to load at every boot. 

Note, I have no idea if that is the issue, but I figure it is worth a try.

i think that i may have figured things out and at this point in time, it looks like there is unfortunately no fix. the system crashed last night and i recieved the following error in my log:

```
gdm[5471]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
```

I did a little research and came up with these bugs:
[https://bugs.launchpad.net/ubuntu/+bug/140554](https://bugs.launchpad.net/ubuntu/+bug/140554)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/153466](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/153466)

these are the exact problems that i have been having and it looks like ubuntu has been informed, so i guess the only thing that i can do is sit back and wait for a fix. thanks for your help again!

---

### Post by cyberdork33 on 2008-01-10
> **czechman86 said:**
> these are the exact problems that i have been having and it looks like ubuntu has been informed, so i guess the only thing that i can do is sit back and wait for a fix. thanks for your help again!Well, at least you know that you are not alone in the world. You should be sure to contribute to the bugs as well. More information is always better. 


You can see how to get a Trace here:
[http://live.gnome.org/GettingTraces/Details](http://live.gnome.org/GettingTraces/Details)
It is quite a lot of information, but it is usually very helpful in determining the problem.

---

