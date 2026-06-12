---
title: "vmmon Module Installing Vmware"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Herix on 2007-06-16
Im trying to install vmware and I get this question:

What is the location of the directory of C header files that match your running
kernel?

I dont know what to answer becuz I dont know what the hell they're talkin about. here is my terminal:

```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 


```

---

### Post by starcraft.man on 2007-06-16
Ah right, your running the vmware installer script. Make sure you have build-essential installed, you have to compile a few things. Paste the following in a terminal (Applications > Accessories > Terminal):

```
sudo aptitude install build-essential
```

Then rerun the script. All of the questions are already answered in the brackets with the defaults, you just have to push enter every time it stops working. These are asked for people who want to manually tweak the Vmware installation or who have made modifications to defaults in their own install.

---

### Post by skymera on 2007-06-16
i got Virtualbox, purely by accident.

its a GUI.
easier to get used to, but mroe juicy on the cpu than CLI

---

### Post by starcraft.man on 2007-06-16
> **skymera said:**
> i got Virtualbox, purely by accident.

its a GUI.
easier to get used to, but mroe juicy on the cpu than CLI

LOL! VMware has a GUI (they'd be in trouble if they didn't) :p It's just they use a perl (pl) installer script. I assume its so that the one installer works on all versions of linux (rather than recompiling).

I do like Virtual box and really think they have a great product, there are some features not present in it that VMware has though and even vice versa. I don't think theres that much of a difference in load on the machine between VMware and Virtual Box, I haven't seen that much.

Anyway, don't worry Herix, just install build essential and continue to use the defaults in the install by pushing enter.

---

### Post by lixy on 2007-06-16
> **starcraft.man said:**
> Ah right, your running the vmware installer script. Make sure you have build-essential installed, you have to compile a few things. Paste the following in a terminal (Applications > Accessories > Terminal):

```
sudo aptitude install build-essential
```

Then rerun the script. All of the questions are already answered in the brackets with the defaults, you just have to push enter every time it stops working. These are asked for people who want to manually tweak the Vmware installation or who have made modifications to defaults in their own install.

Nah. It didn't fix the issue.

---

### Post by lixy on 2007-06-16
Well, it looks like the seventh time was the charm for me. Here's what seems to have done the trick: When prompted for the "Do you want this program to probe for an unused private subnet?" answer no, then give it some IP and stuff, then it asks you the same question again at some point, to which you wanna answer no again, and give it a couple of invalid IPs, then terminate the process using Ctrl-C. Then start another install and it goes smoothly.

I actually have no idea if it's a reproducible workaround or not, because I've been installing/removing VMware server and VMware player thru Synaptic, but Server wouldn't install XP.

I hope any of that made sense.  Bottomline, the install script detects the the header files directory just fine, and it seems to be rather some bug between 6.0.0 and the latest kernel.

---

### Post by PAnna on 2008-01-11
I had the same problem as Henrix too. 
I followed your instructions, starcraft.man and ran the script 
sudo aptitude install build-essential
It seemed to install ok.
When I reran the script I got these errors:
The following VMware kernel modules have been found on your system that were
not installed by the VMware Installer.  Please remove them then run this
installer again.
vmnet vmmon vmdesched vmxnet vmmemctl

Doesn't matter what I try I cannot delete these modules.   Help :(
Sam

---

### Post by lgambett on 2008-01-11
What version of VMware are you installing ? (Server, Player, Workstation) 
Where you took the files to install ?
I suggest you strongly to remove any VMware package coming from Ubuntu, and instead use the .tar.gz versions downloaded from [http://www.vmware.com](http://www.vmware.com). You can download VMware Player or Server free, and also download a 30-day trial of VMware Workstation.
On Feisty the latest VMware works like a charm, while on Gutsy wireless bridging is not supported.
Apart from that VMware should not pose to you any problem.

---

