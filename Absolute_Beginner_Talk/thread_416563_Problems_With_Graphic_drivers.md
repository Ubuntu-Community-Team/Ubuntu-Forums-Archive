---
title: "Problems With Graphic drivers"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Urko on 2007-04-21
Hello:)

I am new in Linux and I am wondering how can I install Nvidia Graphic drivers in my Ubuntu 7.04??????
Problem is that I use old Nvidia Geforce MX 440 graphic card wich latest drivers do not support it:( 

Thanx Urko

---

### Post by Theimon on 2007-04-21
sudo aptitude install nvidia-glx-legacy

---

### Post by hencke on 2007-04-21
> **Urko said:**
> Hello:)

I am new in Linux and I am wondering how can I install Nvidia Graphic drivers in my Ubuntu 7.04??????
Problem is that I use old Nvidia Geforce MX 440 graphic card wich latest drivers do not support it:( 

Thanx Urko

To make this answer more general anyone with nvidia graphics should first go to:

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)

and see which driver they should use. There are 3 different driver families (71xx, 96xx, 97xx).

I just checked the naming policy in Feisty Fawn and it seems to be the following:

nvidia-glx:1.0-9631
nvidia-glx-new:1.0-9755
nvidia-glx-legacy:1.0-7184

To install open Synaptic(gnome) or Adept(kde) and search for nvidia. If it doesn't find anything make sure your internet connection is working and that you have restricted repositories enabled. In synaptic go to "settings" -> "Repositories" (In adept from the "Adept" menu choose "Manage repositories"). Now tick the "Proprietary drivers" in the first tab. Remember to press "Update" or "Fetch updates".

When Synaptic (or Adept) find the drivers all you have to do is install the appropriate driver, in your case the nvidia-glx package. After installing the driver open a terminal and type:

sudo nvidia-glx-config enable

(hit enter and give your password), as instructed in the description of the package in the package manager.

This worked for me in Kubuntu 7.04, but I just remembered that there is also an easier way to do the same in Ubuntu. In gnome go to "System" -> "Administration" -> "Restricted Drivers Manager" and select the preferred drivers. This might be the easiest way to install your nvidia drivers, but make sure you get the right version installed.

[https://wiki.ubuntu.com/7.04Tour#head-83d7cdd5e03c9dbfa171dde3f05d96348c81925a](https://wiki.ubuntu.com/7.04Tour#head-83d7cdd5e03c9dbfa171dde3f05d96348c81925a)

Either way should work.

Edit(May 3, 2007): Updated gnome information.

---

### Post by K.Mandla on 2007-04-22
(Edit: Sorry, I changed my mind on my answer. Pay no attention to this. :oops: )

---

