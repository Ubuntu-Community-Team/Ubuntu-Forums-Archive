---
title: "linux-386 loads, linux-generic won't"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Slapyo on 2007-03-13
When I installed my Nvidia drivers I have to boot up on linux-386.  If I try to boot up on linux-generic it doesn't get to gnome.  It crashes before it gets to that point and just drops me to command line.  Last night I ran some updates and it put in a new linux-generic kernel but my machine won't boot on that, I have to boot with linux-386 in order to get back in.

I've been reading up and it looks like I should be using the linux-generic kernel rather than the linux-386.  How can I get things working on linux-generic?  It seems that kernel is getting the updates rather than the linux-386.

---

### Post by Kobalt on 2007-03-13
How did you install your drivers ? 
I installed my drivers from the Nvidia package (beta drivers indeed) : when I get a kernel update I have to boot from them and install the package once again if I want to get my Xserver going on... 
I would suggest you reinstall the drivers in command line then, since you can access that. Or If you don't know how to do that, reverse to vesa or nv drivers in your xorg.conf file, log in graphical mode then reinstall the nvidia drivers.

---

### Post by K.Mandla on 2007-03-13
If you use an Nvidia card and use the drivers from the repository, you need to use *linux-386* because there is no nvidia kernel module in *linux-generic*. If you want *generic* and want to use Nvidia drivers with it, I believe you have to install them manually, or with a script like [Envy]("http://albertomilone.com/wordpress/").

---

