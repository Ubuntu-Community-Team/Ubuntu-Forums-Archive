---
title: "screen res..."
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by Vendeta on 2007-04-08
my monitor goes up too 1280 by 1024 and i always use that and i CANT stand anything but that and when im on ubuntu its WAY WAY WAY to big at like 800 by somthing how do i get my good resulution and easy ubuntu keeps freezing when i go to install somthing im using kubuntu with a ubuntu instaled desktop does that madder?

---

### Post by bikeboy on 2007-04-08
Using both desktops is fine.

For the resolution, what sort of video card do you have (nvidia, ati? and model)? Sometimes the default open source driver doesn't know your card well enough to provide full resolution, in which case using the proprietary one is necessary. In most cases it's very easy to install.

---

### Post by Vendeta on 2007-04-08
Nividia GeForce4 MX intergrated GPU
Is that what u needed?

---

### Post by bikeboy on 2007-04-09
That is.

There may be more complicated ways to get things right, but IMHO the easiest way to get the right resolution will be to open up Synaptic (System > Admin > Synaptic) and search for nvidia. You will find the nvidia-glx package, not the nvidia-glx-legacy. Install that and post back once that's done or if you have any problems.

If you don't find the package, have a read of how to enable the extra software repositories. There is an explanation here where you can copy and paste the commands.
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

edit: It seems that recent changes by nvidia mean that you *might* need the legacy driver. The Ubuntu wiki has some good instructions for enabling the nvidia driver once it's installed.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

