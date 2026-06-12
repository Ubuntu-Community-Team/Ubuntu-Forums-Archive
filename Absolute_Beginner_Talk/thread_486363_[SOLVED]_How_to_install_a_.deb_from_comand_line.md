---
title: "[SOLVED] How to install a .deb from comand line"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by kungfugecko on 2007-06-27
Can someone please help me with a quick problem?

How do I install the file here [http://people.ubuntu.com/~pkl/ps2/](http://people.ubuntu.com/~pkl/ps2/)
the one ending in i386.deb?

The machine I need to install it on is running ubuntu 7.04, but the PS/2 mouse isn't working, and I think this patch may fix it.  I figured out I can push ctrl+alt+f1 to get to a terminal / command prompt, but I don't know how I would download and install that .deb file from a terminal.  Hopefully someone here can give me a quick run-through.  Thanks!

---

### Post by bodhi.zazen on 2007-06-27
use dpkg :

```
wget  http://people.ubuntu.com/~pkl/ps2/linux-image-2.6.20-16-generic_2.6.20-16.28_i386.deb
sudo dpkg -i linux-image-2.6.20-16-generic_2.6.20-16.28_i386.deb
```

Please use a more descriptive term for the title of your threads :)

---

### Post by HackingYodel on 2007-06-27
Are you sure the problem isn't with the mouse?

Unless you are running 7.04 on some very exotic hardware, a kernel patch or upgrade shouldn't be needed.

What computer are you running Ubuntu on?

---

### Post by starcraft.man on 2007-06-27
Ok, with the terminal open paste this in:

```
wget http://people.ubuntu.com/~pkl/ps2/linux-image-2.6.20-16-generic_2.6.20-16.28_i386.deb

```

That is the 32 bit version of the package, I assume you are running that. wget btw is simply the command that will remotely download things on sites like the debs.

Then once its finished, it will be in the directory your in (usually in home by default). Then to install I believe its:

```
sudo dpkg -i linux-image-2.6.20-16-generic_2.6.20-16.28_i386.deb
```

I hope I got that right, haven't done that from terminal often. That should do it, hope it works. I don't know anything about patches to get ps/2 mice working, all the mice I ever used worked out of box with Linux. I agree with HackingYodel, I don't really think you should need this to get a mouse working now a days... I don't know about your specific hardware though, post the model please.

Edit: Oh not sure if you needed the wget bit, if you already have it in the directory your working from ignore that.

---

### Post by kungfugecko on 2007-06-27
Alright I'm giving this a shot, hopefully it will work!  

About my hardware, it isn't that old, but the mouse just isn't working.  However, this mouse worked fine on this exact same computer while running win 2000.

It's ~ 733mhz, 256mb ram, 20gb HDD, so I think the hardware should be good enough to run Ubuntu.  I searched a bunch of forums about people with ps/2 mouse problems, and there was a lot of discussion about a problem people with SiS chipsets are having with PS/2 mouse compatability, and the computer I'm running has SiS chipset as well.  This solution worked for some people, so I'll give it a shot and report back =P

Thanks for the help!!

*edit* people with SiS and PS/2 mouse problems: 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108382](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108382)
[http://ubuntuforums.org/archive/index.php/t-464982.html](http://ubuntuforums.org/archive/index.php/t-464982.html)
[https://bugs.launchpad.net/baltix/+source/linux-source-2.6.20/+bug/108221](https://bugs.launchpad.net/baltix/+source/linux-source-2.6.20/+bug/108221)

*edit* @ bodhi.zazen - I'll try and have a more descriptive title next time xD sorry!

---

### Post by kungfugecko on 2007-06-27
problem solved! crisis averted! =P

Thanks for the help guys, that patch seems to have fixed the PS/2 mouse issues!

---

### Post by starcraft.man on 2007-06-27
> **kungfugecko said:**
> problem solved! crisis averted! =P

Thanks for the help guys, that patch seems to have fixed the PS/2 mouse issues!

No problem, oh and consider learning a bit more CLI at [linux command,]("http://www.linuxcommand.org/") never know when it might get you out of a sitch :p.

---

### Post by bodhi.zazen on 2007-06-28
Awesome ....

Also, don't forget to mark your threads as solved ;)

I did it for you this time :twisted:

---

### Post by HackingYodel on 2007-06-28
Glad to hear it's solved.

Excellent job of tracking down your problem and solution here in the forums.  Enjoy your new Ubuntu!

---

### Post by starcraft.man on 2007-06-28
> **bodhi.zazen said:**
> Awesome ....

Also, don't forget to mark your threads as solved ;)

I did it for you this time :twisted:

ROFL! And here I thought that a user had actually done it by looking at title in the main page :p.

---

