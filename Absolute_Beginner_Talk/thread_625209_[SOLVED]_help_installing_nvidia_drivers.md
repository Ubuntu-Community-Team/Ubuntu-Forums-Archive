---
title: "[SOLVED] help installing nvidia drivers"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Riffer on 2007-11-27
So after to many attempts at trying to fix nVidia I did a complete reinstall.  I'm now trying to install the latest driver from nVidia.  

I went into terminal and typed

"sh NVIDIA-Linux-x86-169.04-pkg1.run"

An error message comes up that sh can't run the above command.  I tried putting sudo in front of it,  I have tried using the ctl/alt f# thing.

What am I missing?

---

### Post by Six_Digits on 2007-11-27
Just try envy :)

---

### Post by Inxsible on 2007-11-27
Why not simply use the Restricted Driver Manager?

System>>Administration>>Restricted Driver Manager

---

### Post by PeterJS on 2007-11-27
> **Six_Digits said:**
> Just try envy :)

Don't use envy, it's old, out dated, and no longer necessary. Use the restricted drivers manager instead, it's under System > Administration > Restriced Drivers Manager. It will install and set up the drivers for you.

---

### Post by 11hjpphty76lkjj on 2007-11-27
I had a similar experience installing the nvidia drivers---although I can't say for sure how come you can't run the sh you could try running 

```
chmod 777 NVIDIA-Linux-x86-169.04-pkg1.run
```

then

```
sh NVIDIA-Linux-x86-169.04-pkg1.run
```

or try

```
sh ./NVIDIA-Linux-x86-169.04-pkg1.run
```

The nvidia drivers are the only thing that got my system working correctly, now I can play WoW perfectly.

Envy although a great idea doesn't work reliably and the nvidia-glx-new drivers don't give full (ie direct rendering) capabilities.  I wish it did.

Installing the nvidia driver works.  I mean--once you get past your install problem that is... ;)

---

### Post by PeterJS on 2007-11-27
> **kalosaurusrex said:**
> 
Envy although a great idea doesn't work reliably and the nvidia-glx-new drivers don't give full (ie direct rendering) capabilities.  I wish it did.


That's not right at all. The nvidia-glx-new drivers package contains the same drivers as manually installing them, and those are the drivers that provide direct rendering.

The nv driver is the open source 2d driver, and nvidia is the 3d driver that can be installed manually, through synaptic, or the restricted drivers manager.

---

### Post by 11hjpphty76lkjj on 2007-11-27
I spent a lot of time trying to get Direct Rendering to work, with the nvidia-glx-new drivers as well as using envy.  In the end only the nvidia propriety driver worked.  Perhaps someone can define the process for using the nvidia-glx-new driver to get Direct Rendering to work?  I'd love to use it!

So correct or not, the nvidia prop driver worked right away with only some mild problems. Where as the glx-new driver didn't.  and I spent a lot of time trying to get it to work. 

Maybe there is a bug?  I can reproduce it over and over again with the same result.

---

### Post by Riffer on 2007-11-27
I'm trying a manual install because the drivers from the repositories have caused my system to crash.  I'm trying to install the latest beta drivers (169.04) in hopes that it won't cause freezes etc.  Envy never seemed to work well for me.

So I got my problem solved but now I need to know how to kill an x session.

---

### Post by PeterJS on 2007-11-27
> **kalosaurusrex said:**
> I spent a lot of time trying to get Direct Rendering to work, with the nvidia-glx-new drivers as well as using envy.  In the end only the nvidia propriety driver worked.  Perhaps someone can define the process for using the nvidia-glx-new driver to get Direct Rendering to work?  I'd love to use it!

So correct or not, the nvidia prop driver worked right away with only some mild problems. Where as the glx-new driver didn't.  and I spent a lot of time trying to get it to work. 

Maybe there is a bug?  I can reproduce it over and over again with the same result.

The nvidia-glx-new package **is** the nvidia driver. The name of the package is nvidia-glx-new, and it's contents are the nvidia driver.

Your best bet for getting the driver set up right is to use the restricted driver manager to install it.

---

### Post by Inxsible on 2007-11-27
> **Riffer said:**
> So I got my problem solved but now I need to know how to kill an x session.
Ctrl + Alt + Backspace

---

### Post by Riffer on 2007-11-27
Ok that didn't work, all it did was take me back to a login screen.  I need to know how to stop and x server.

Also the drivers in the repositories are older ones and there seems to be a glitch between them and the new kernal.  I'm hoping that thius new driver will fix that.

---

### Post by Inxsible on 2007-11-27
Ctrl + Alt + Backspace does kill (actually restarts) the X Session. X is what the GUI is. Log back in and check it out.

---

### Post by Riffer on 2007-11-27
Yeah I did that.  For the nvidia drivers to install there can be no x server running yet it has to be at a level 3???? whatever that is.

So how can I get to a command line thats at a level 3 with no x server running?

---

### Post by Riffer on 2007-11-27
Found it.

In terminal type "sudo /etc/init.d/gdm stop"

and go from there  I'm marking this solved

---

### Post by Six_Digits on 2007-11-28
> **PeterJS said:**
> Don't use envy, it's old, out dated, and no longer necessary. Use the restricted drivers manager instead, it's under System > Administration > Restriced Drivers Manager. It will install and set up the drivers for you.

ENVY's latest stable release was actually released 4 days ago. Using it to install your drivers also gives you nvidia settings. :)

---

