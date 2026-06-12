---
title: "Makefile: Linux Kernel Source Not Found???"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-04-02
Hello ALL, I need your help to compile & install a ".tar.gz" package.

It is the Intel's Gigabit LAN Drivers (I wish to install) for an ASUS Mobo.

I have managed to extract the package:
Not with the "untar" command, but by right-click on the "tar" file & select "Open with Archive Manager".
Then, from the Starndard Toolbar, I click on the button named "Extract" & choose "Desktop" & click again on the "Extract" button.

On the Desktop, I move inside the Folder, to find these:

[url/]http://i69.photobucket.com/albums/i58/dvarsam/Screenshot1.png[/url]
(look at the above picture)


And inside the folder named "src", I have these:

[http://i69.photobucket.com/albums/i58/dvarsam/Screenshot2.png](http://i69.photobucket.com/albums/i58/dvarsam/Screenshot2.png)
(look at the above picture)

Can somebody lead me, on how to perform the rest of the commands:

1. ./configure       (which file name: e.g. "./makefile" ?)
2. make <which file name>
3. etc...
4 etc...

I tried to perform a:
> root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src# make makefile

to get a:
> Makefile:65: ***Linux kernel source not found. Stop.

Thanks.

P.S.> I have never managed to install a ".tar.gz" file, so bare with me for a while...

---

### Post by dvarsam on 2006-04-02
I will try to post an Image - I have never tried this before:

On the Desktop, I move inside the Folder, to find these:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/Screenshot1.png[/IMG]
(look at the above picture)


And inside the folder named "src", I have these:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/Screenshot2.png[/IMG]
(look at the above picture)

Thanks.

---

### Post by dvarsam on 2006-04-03
Anybody?

---

### Post by az on 2006-04-03
The e1000 driver is already in the kernel.  Do you need a newer version?


In general, to make a kernel module you need to install a few packages:

linux-headers-386
build-essential
gcc-3.4 (build-essential provides gcc-4.0, but the kernel in breezy was built with gcc-3.4)

Then you go to the source tree and read the README which usually says to cd into the direcotry and run

sudo make
make install.

But you arelady have the driver....

---

### Post by dvarsam on 2006-04-04
[QUOTE=azz]The e1000 driver is already in the kernel.
Do you need a newer version?

In general, to make a kernel module you need to install a few packages:

linux-headers-386
build-essential
gcc-3.4 (build-essential provides gcc-4.0, but the kernel in breezy was built with gcc-3.4)

Then you go to the source tree & read the README which usually says to cd into the directory & run...

sudo make
make install.

But you already have the driver....[/QUOTE]

Dear "azz",

              thank you for baring with me...

First of all, please let me say this:

It is of great confort & relieve to me that an _Ubuntu PH.D guy_ - like you (if I judge from your beans), is giving the student some advice...

Now back to life's problems:
I agree with you totally, that if the drivers are ALREADY inside, then there is NO need to go & install a newer version...

I do NOT need this "steep learning curve/trouble" for now, I would just like to get things going...

I know that having the LATEST drivers (or luxury car or whatever) is Nice but it also hard to do it (./configure, make install or in the case of the luxury car have the money to afford it)...

Please understand that having NO LAN, means NO Internet to me & that is pretty bad..., as Internet is Soooo into our lives...

You say that the Drivers for the Intel LAN e1000 are already in...

No problem, but why during the installation I got this message:

I will refer to it as "Window A:"
> Title:
Detect Network Hardware

Message:
No Ethernet Card was detected, but a Firewire interface is present.
It's possible, though unlikely, that with the right Firewire hardware connected to it, this could be your Primary Ethernet Interface.
Do you intend to use Firewire Ethernet?

Pick a choice:
YES or NO

At the same time, when doing a " lshw -C Network", I get:

>  root@ubuntu:/home/elena/Desktop# lshw -C Network
*-network UNCLAIMED
description: Ethernet controller
product: Intel Corporation
vendor: Intel Corporation
physical id: 0
bus info: pci@04:00.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
resources: iomemory:cffe0000-cfffffff ioport:d800-d81f irq:5

What does "-network UNCLAIMED" mean & how do I get it recognized?

By the way, my Router is OK & I am behind it writting to you right now...

And the LAN's lamp behing the PC which creates this trouble (& can not get configured) is lighting my way in the dark... (a green light is ON)...
But it is a very little green lamp working to light my way into this Darkness...

Thank you for your time & effort.

Dimitris.

---

