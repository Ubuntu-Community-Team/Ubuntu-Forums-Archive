---
title: "Some colours causes part of screen to &quot;flicker&quot;"
date: 2011-09-24
forum: Asus Ubuntu Support (CLOSED)
---

### Post by DannyDroid on 2011-09-24
I just brought a new laptop and installed linux on it.

First, I installed eOS 0.1 but the black GNOME2 bar across the top flickers slightly between two blacks. So, I tried eOS 0.2 which failed run correctly (due to compiz I believe). After that I tried the latest Ubuntu BETA which seemed to have worked fine but then I noticed the login page, next to my name was flicking between to purples, I thought I could live with that but then I went to webupd8 to find the black on their logo going crazy and flickering so I then went to Google Images and searched "black" and some of the images do the same thing.

I've been told that it could be temporal dithering;
[https://secure.wikimedia.org/wikipedia/en/wiki/Frame_Rate_Control](https://secure.wikimedia.org/wikipedia/en/wiki/Frame_Rate_Control)

This is the laptop; [http://www.comet.co.uk/p/Laptops/buy-ASUS-X53E-SX399V-Laptop/734039](http://www.comet.co.uk/p/Laptops/buy-ASUS-X53E-SX399V-Laptop/734039)

What's going on? ):

---

### Post by DannyDroid on 2011-09-25
The laptops just a rebranded K53E, if that helps.

Heres the "glxinfo" if is any help: [http://pastebin.ca/2082706](http://pastebin.ca/2082706)

And "lshw -C video":

> danny@durp:~$ sudo lshw -C video
[sudo] password for danny: 
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:ddc00000-ddffffff memory:c0000000-cfffffff ioport:e000(size=64)
danny@durp:~$

---

