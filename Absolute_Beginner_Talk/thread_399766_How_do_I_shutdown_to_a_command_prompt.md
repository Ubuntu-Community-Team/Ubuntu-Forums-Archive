---
title: "How do I shutdown to a command prompt?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Aro on 2007-04-02
Hi, I have a Nvidia Geforce 6600N (not sure what the N means...it's an agp card that supposedly is 'sli enabled' according to the box, but I only have one so I don't need to worry about getting SLI working)

I found this tutorial on how to install the drivers [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/index.html)

The installer tells me that I need to shut down my X windows system in order for it to run.

My problem is that I have no idea how to do that. I can press control alt backspace...and I get a command prompt for about two seconds before it flips me back to the ubuntu graphical login screen. I can use that screen to 'change session' to 'failsafe terminal' but that's no better as while in there it still says I have the x window front end running

-----------

I didn't know what repositories were so I looked them up. Now I understand why I had so few programs on my add/remove list...I need to add the multiverse and universe repositories...well this explains it better

Thanks guys :D

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by deanjm1963 on 2007-04-02
easiest way is to log out to the login screen, then hit Ctrl+Alt+F1.

why don't you use the nvidia drivers in the repositories? very easy to setup, there's a heap of posts on how to do it.

---

### Post by rocknrolf77 on 2007-04-02
You also have to do a ```
sudo kilall gdm
```  When your'e done installing the drivers do a ```
sudo /etc/init.d/gdm restart
``` to get back in to x. :) Maybe you have to reboot your computer. Just remember you need the build-essential package.

---

### Post by jordanmthomas on 2007-04-02
```
sudo /etc/init.d/gdm stop 
```
is a little nicer than killall since it stops it "properly"

---

### Post by Aro on 2007-04-02
I got it working :)

Once I found out what repositories are and how to add all of the universal ones to my synaptic package manager I was able to find the generic nvidia drivers nvidia-glx

Since I had already been reading the Nvidia site trying to do it their way (their way sucks btw), I knew that Nvidia packaged all their drivers together and that my card was in that package and not the legacy one.

Anyway, I installed it with the package but it still didn't work.

Reading the little blurb for nvidia-glx in the synpatic package manager, it told me to run some sudo command...

I did, but it gave me some error and told me to do something funky (which did nothing), OR to check my /etc/X11/xorg.conf file and change my driver from "nv" to "nvidia"

After that I rebooted. 

Now I'm watching my screensavers not chunk at all ;-)

Thanks!

---

