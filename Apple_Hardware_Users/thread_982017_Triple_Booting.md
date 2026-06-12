---
title: "Triple Booting"
date: 2008-11-14
forum: Apple Hardware Users
---

### Post by Betta on 2008-11-14
Now I just skimmed over the front page and didn't see any similar topics, but if there are, please link me and I'll read that. 

Anyway, here is what I am trying to do: Triple boot Ubuntu (8.10), OS X Leopard (10.5), and Windows Vista. I currently have Vista running on the bootcamp partition that OS X does for you. Here are my questions:

1) Is this at all possible?
2) Can I still use the pretty (I'm a sucker for pretty things) Mac boot loader that I select bootcamp or OS X with?
3) Would a 30gb Ubuntu partition be adequate size for just tinkering?
4) Is it possible to boot into the partitioned Ubuntu installation from Parallels, similar to how you can boot to your Bootcamp partition in parallels?
5) Assuming that I can do this at all, how is 64 bit support doing these days? The last time I tried was on 6.10 and the support was terrible for that. Do flash and media libraries work on it these days (I would like to take advantage of my 4gb of RAM on Ubuntu). 

Macbook Pro model: MacBookPro(4, 1) (Mid 2008). 
I think I got everything I need in there, but I can provide more information if needed.

-Betta

---

### Post by _mario_ on 2008-11-14
> **Betta said:**
> Now I just skimmed over the front page and didn't see any similar topics, but if there are, please link me and I'll read that. 

Anyway, here is what I am trying to do: Triple boot Ubuntu (8.10), OS X Leopard (10.5), and Windows Vista. I currently have Vista running on the bootcamp partition that OS X does for you. Here are my questions:

1) Is this at all possible?
there is more than 1 page ... ;-) and yes it is possible. have a look at [the Ubuntu wiki]("https://help.ubuntu.com/community/MacBookPro"), [the OnMac wiki]("http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp"), or just google around.

> **Betta said:**
> 
2) Can I still use the pretty (I'm a sucker for pretty things) Mac boot loader that I select bootcamp or OS X with?
you most likely want to install refit, which is much more pretty and user-friendly than the built-in boot menu.

> **Betta said:**
> 
3) Would a 30gb Ubuntu partition be adequate size for just tinkering?

30 GB is more than enough. my system partition (no data) is about 10 GB plus 4 GB of swap on a separate partition.

> **Betta said:**
> 
4) Is it possible to boot into the partitioned Ubuntu installation from Parallels, similar to how you can boot to your Bootcamp partition in parallels?
in theory yes. if you can manage to set up parallels appropriately. i never tried that.

> **Betta said:**
> 
5) Assuming that I can do this at all, how is 64 bit support doing these days? ... Do flash and media libraries work on it these days (I would like to take advantage of my 4gb of RAM on Ubuntu).
fine. i'm running Ubuntu 8.10 64-bit with no problems at all. don't forget to add the mactel repository, by adding these lines to your /etc/apt/sources.list
```
deb http://ppa.launchpad.net/mactel-support/ubuntu intrepid main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu intrepid main
``` and install the hid-dkms package.

ciao,
Mario

---

