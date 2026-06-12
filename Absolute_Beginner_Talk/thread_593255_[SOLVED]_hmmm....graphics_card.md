---
title: "[SOLVED] hmmm....graphics card"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by mandrill on 2007-10-27
ok, so I broke it....installed gutsy, have older geforce 2 card, automatically it selected the nvidia glx drivers, no problem...a little slow, 3d chess slow, video from LAN slow, decided to try "new" drivers....BIG mistake...got restart in low graphics, etc, re-installed glx, no go, tried legacy, no go, re-installed glx,  ran   "sudo nvidia-glx-config enable", more trouble, something about sums not matching, more re-starts, finally no nvidia drivers, which, it turns out, I really need. Guess I'm not happy unless I'm breaking something....anyway, HOW DO I FIX IT?

this is what I get when trying to install nvidia glx:

jim@monkey:~$ sudo nvidia-glx-config enable
[sudo] password for jim:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

---

### Post by FuturePilot on 2007-10-27
```
sudo apt-get remove --purge nvidia-glx-new
sudo apt-get install nvidia-glx
```
```
gksudo gedit /etc/X11/xorg.conf
```
Find the Device Section and change the driver from "nv" to "nvidia"

---

### Post by Cato2 on 2007-10-27
I'm fairly sure Gutsy can recover better from messed up X server configurations, so I would try:

1. cd /etc/X11
2. mv xorg.conf xorg.conf.broken
3. Hit Ctrl+Alt+Backspace to kill the X server (this is a bit brutal but that's what we want here)

(If step 3 doesn't work, just reboot the system).

Now, Gutsy has a Bulletproof X mode, so when it finds the X config is missing or bad, it should kick in and help you resolve this - it can even pick up the Windows .INF files for a  monitor, though that isn't your problem here.

---

### Post by mandrill on 2007-10-27
> **Cato2 said:**
> I'm fairly sure Gutsy can recover better from messed up X server configurations, so I would try:

1. cd /etc/X11
2. mv xorg.conf xorg.conf.broken
3. Hit Ctrl+Alt+Backspace to kill the X server (this is a bit brutal but that's what we want here)

(If step 3 doesn't work, just reboot the system).

Now, Gutsy has a Bulletproof X mode, so when it finds the X config is missing or bad, it should kick in and help you resolve this - it can even pick up the Windows .INF files for a  monitor, though that isn't your problem here.

well....that certainly blasted the heck out of it - MANY THANKS!  I had noticed that before this, the restricted drivers screen had a green checkmark next to the nvidia driver notation even though the little square box itself was not checked, and it was (sort of) indicating that the drivers were enabled....what now? just enable the drivers from restricted drivers, synaptic, add/remove, which?

---

### Post by Frak on 2007-10-27
Better yet
```
sudo apt-get remove --purge nvidia-glx-new --force-yes
sudo apt-get install nvidia-glx
```

It will switch the driver automatically.

---

### Post by mandrill on 2007-10-27
> **FuturePilot said:**
> ```
sudo apt-get remove --purge nvidia-glx-new
sudo apt-get install nvidia-glx
```
```
gksudo gedit /etc/X11/xorg.conf
```
Find the Device Section and change the driver from "nv" to "nvidia"

well, gentlemen, I have tried it both ways, and it is now officially foobar. now it says   /etc/x11  is not a directory.....I believe I will have a cigarette and re-install the m*th**f**cker

---

### Post by FuturePilot on 2007-10-27
Make sure you type X11. Linux directories are case sensitive
x11 != X11

---

### Post by mandrill on 2007-10-27
> **Frak said:**
> Better yet
```
sudo apt-get remove --purge nvidia-glx-new --force-yes
sudo apt-get install nvidia-glx
```

It will switch the driver automatically.

did not work....still getting boot scripts, and at one point, terminal notified me xorg changed, backup saved somewhere - at this point I am going to try Cato2 method again, then, if that doesn't work, "there's nothing like the smell of gibbons in the morning"

worst part, I spent 3 f-ing hours last nite learning some cool stuff on this thing, and now it looks like I'll have to start all over......

---

### Post by mandrill on 2007-10-27
> **mandrill said:**
> did not work....still getting boot scripts, and at one point, terminal notified me xorg changed, backup saved somewhere - at this point I am going to try Cato2 method again, then, if that doesn't work, "there's nothing like the smell of gibbons in the morning"

worst part, I spent 3 f-ing hours last nite learning some cool stuff on this thing, and now it looks like I'll have to start all over......

well - time to re-install....you don't suppose using amarok might have had anything to do with it?

---

### Post by Frak on 2007-10-27
> **mandrill said:**
> well - time to re-install....you don't suppose using amarok might have had anything to do with it?
If Amarok did that, I could supposedly also make a nuclear warhead with GIMP.

No, Amarok most likely could not have done it.

---

### Post by mandrill on 2007-10-27
> **Frak said:**
> If Amarok did that, I could supposedly also make a nuclear warhead with GIMP.

No, Amarok most likely could not have done it.

that's funny! but amarok was having issues with gnome, and, I'm just a lowly windows convert....what the heck do I know....thanks for your help...

---

### Post by Frak on 2007-10-27
You probably just had some speed issues with the QT libraries, but other than that, I don't see Amarok stopping X11 anytime soon.

---

### Post by forestpixie on 2007-10-27
what position are you actually in with your graphics driver - I'm confused :)

I had problems with a GeForce4 card - however many times I told it to use the restricted driver - it rebooted with the 'can't find card' box - I ended up using [envy]("http://albertomilone.com/nvidia_scripts1.html") to get it right, which it has for the time being. 

When I've got time I'll have another go - I sure hope that Hardy Heron will do better with graphics sigh.. at least it's better than Feisty.

---

### Post by mandrill on 2007-10-27
> **forestpixie said:**
> what position are you actually in with your graphics driver - I'm confused :)

I had problems with a GeForce4 card - however many times I told it to use the restricted driver - it rebooted with the 'can't find card' box - I ended up using [envy]("http://albertomilone.com/nvidia_scripts1.html") to get it right, which it has for the time being. 

When I've got time I'll have another go - I sure hope that Hardy Heron will do better with graphics sigh.. at least it's better than Feisty.

I have actually already done a complete re-install, except for a couple minor things - gotta get my printer going, install freepops, and set my slave drive to automount, and I'm done....

---

