---
title: "running gst-register"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by ngant17 on 2005-12-26
I'm a newbie to Ubuntu, although I'm slightly familiar with some of the nuances of Linux.

I am impressed with the ease of the basic install for Ubuntu, although it was a somewhat long, drawn-out process, it still worked for me and I re-installed a second time just for practice.

I downloaded Ubuntu and burned to disk using WinXP, but I hope in the future to be self-sufficient for all these tasks in Linux/Ubuntu.

Here are some current problems I'm trying to resolve.

I am trying to run a video media player, i.e., Totem.  Ubuntu is saying that I need to check the gstreamer install.  "Totem plugin could not start".  How do I run this?  I think I need to run "gst-register" but I don't know how to drop down into text mode or run if from the desktop screen.  Any help would be appreciated.  Thanks!

---

### Post by Perfect Storm on 2005-12-26
```
sudo apt-get install gstreamer0.8-plugins totem-xine
gst-register-0.8

```

Make sure that universe is enable in your sourcelist.

---

### Post by ngant17 on 2005-12-26
Thanks!  At terminal prompt, I put this command into linux/ubuntu:

sudo apt-get install gstreamer0.8-plugins totem-xine

output was the following:

----------------------------------------------------------------------------------------------------
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate
-------------------------------------------------------------------------------------------------

does this mean I need to install the original Ubuntu CD to finish the install?  I only downloaded one CD to install Unbuntu.  Do I need another CD with additional code/apps on it?

---

### Post by Perfect Storm on 2005-12-26
Did you enable universe in your sourcelist?
You running breezy with arch i386?

---

### Post by ngant17 on 2005-12-26
oops, I posted too soon!  here is my additonal output from the second line of 
sudo (i.e.,  sudo gst-register-0.8)

----------------------------------------
....Added plugin asf with 2 features.
Rebuilding user_registry (/root/.gstreamer-0.8/registry.xml) ...
Loaded 149 plugins with 296 features.
-----------------------------------------

I think I'm ready to roll.  let me try this to see how far I get.  Thanks!!

---

