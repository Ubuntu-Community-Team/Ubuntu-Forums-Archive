---
title: "Which Nvidia Drivers to use?"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by phargarten on 2007-10-04
I am trying to figure out what drivers to use for my GeForce Go 7200 graphics card PCI-e. The nvidia Unix Portal offers three options and my ubuntu install offers me one. Should I be happy with the drivers provided by the OS and are they enough to run Compiz and Beryl?

---

### Post by shirilover on 2007-10-04
I believe you should use the nvidia-glx-new drivers.

---

### Post by WebSiteGuru on 2007-10-04
How about FX 5200?

---

### Post by Chafnan on 2007-10-04
The nvidia-glx-new is the right package for the 7200 and FX 5200

---

### Post by mendingo84 on 2007-10-04
you should use the latest drivers provided by nVidia ( they are named smth with 100.. ). if you don't want to mess around than use this tool: [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html") . It will do the trick ;)
I saw posted something about FX 5200...that is the graphic card, not the driver...

---

### Post by WebSiteGuru on 2007-10-04
Hmm, Weird! Because when I tried to load that before I decided to upgrade to Gutsy Gibbon (last night). I won't load the driver properly.


Anyway, thanks for the carification on it. :D

---

### Post by bodhi.zazen on 2007-10-04
> **phargarten said:**
> I am trying to figure out what drivers to use for my GeForce Go 7200 graphics card PCI-e. The nvidia Unix Portal offers three options and my ubuntu install offers me one. Should I be happy with the drivers provided by the OS and are they enough to run Compiz and Beryl?

First try the nvidia-glx-new driver.

If it works \o/

If not you will need to remove it and try the proprietary  nvidia driver.

There is a nasty bug with the nvidia-glx-new driver, so to remove it you need to :

```
sudo apt-get remove --purge nvidia-glx-new
sudo rm /lib/linux-restricted-modules/.nvidia.new.installed
```

---

### Post by phargarten on 2007-10-04
So I installed the newest driver from nvidia and now X is all broken and reboot brings me to command line. I can reset the driver in xorg but now using the proprietary driver it takes me back to the broken X. I ran the uninstalling script but it is not working. Any suggestions?

---

### Post by bodhi.zazen on 2007-10-04
~ LOL ~ look up ^^^

In my last post I described how to fix this problem.

sudo rm /lib ....

Then re-install the proprietary  nvidia driver

Then reboot and all should be good again

---

### Post by phargarten on 2007-10-04
OK the result of your second command says it does not exist. When I navigate to the directory in   /lib/linux_restricted-modules/ there is one directory: 2.6.20-16-generic

in that directory there is: 

nvidia
nvidia_legacy
nvidia_new


When installing the restricted driver in the Fiesty interface I am still getting an error for X.

---

### Post by bodhi.zazen on 2007-10-04
I would re-name all those to nvidia*-old and re-install the nvidia driver.

---

### Post by phargarten on 2007-10-04
I renamed the folders and still I am getting a crash on startup.  What can I do to completely remove the nvidia drivers. Would going back to the old kernel work? I am just out of ideas and I am new. What other info can I give you?

---

### Post by bodhi.zazen on 2007-10-04
Ouch ...

Well, the only though I have is that that file I gave your is "hidden"

so either put the command in a terminal or make sure you "show hidden files" in nautilus

If that is not the problem, :(

Post a bug report :( :(

---

### Post by xpod on 2007-10-04
I went with the driver for older cards on a fresh gutsy install today using a FX5500 via the restricted drivers manager although it now reports me as using...: NVIDIA accelerated graphics driver(latest cards):-k

Nvida-settings still reports 1.0-9639
I actually thought the FX???? *was* classed as an "older" card.

It works fine though so i aint faffing about with the new ones just to find out.Not tonight anyway:

---

