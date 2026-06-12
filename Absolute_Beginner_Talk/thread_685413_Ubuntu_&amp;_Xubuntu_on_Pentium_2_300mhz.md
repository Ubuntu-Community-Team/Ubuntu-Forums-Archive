---
title: "Ubuntu &amp; Xubuntu on Pentium 2 300mhz"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by joshbanter on 2008-02-02
Hey everyone, I have few questions about installing ubuntu/xubuntu on Pentium II 300 mhz with 384 mb of memory. I managed to install both Ubuntu and Xubuntu on the machine despite having a warning about ACPI failed bios cutoff year -  my bios is dated 1998. Anyway both are kinda sluggish on my computer. Ubuntu was slightly slower(than Xubuntu) and  even non-responsive at times but overall both of them are slower than it was when Windows 98 was installed. So is this expected because my computer is old? I was hoping for a better performance than Windows.

I've read an old thread [[COLOR="Blue"]_Picking the Kernel thats Right for You (Possible Speed Increase)_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=85917") but when I did "sudo apt-get install linux-686", there wasn't any match for linux-686. Does that mean it's no longer necessary to do this?

So, what can I do at this point?

Thanks in advance.

---

### Post by at a loss on 2008-02-02
I tried both on my laptop (700 mhz chip) and they ran ok.  You either have to use a faster system or use a smaller linux version.  DSL is only 64mb.

---

### Post by Julita on 2008-02-02
You can also try Fluxbuntu - it is lighter than Ubuntu and Xubuntu.

---

### Post by rich.bradshaw on 2008-02-02
Yeah, try Damn Small Linux, Puppy or Fluxubuntu.

How much RAM does it have? It's worth upping it to 512 if you can find the ram for it, as it will make a huge difference.

---

### Post by Julita on 2008-02-02
If the type of RAM is SDRAM, than DDRI, most probably, will fit (since it is pretty hard to find SDRAM now, at least, for us )) ), so there should not be any problem with finding additional RAM.

---

### Post by mysticrider92 on 2008-02-02
You could try the kernel, but I doubt it will have a huge speed increase. The package you want (assuming you installed Ubuntu 7.10) is linux-image-2.6.22-14-i386. The best bet for your computer would actually be compiling your own kernel (if you are ok with doing this the harder way). Here is a guide for that: [http://beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_compile](http://beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_compile).

The custom-compiled kernel can be trimmed to your hardware, and is optimized for your processor, so it will see the largest speed increase.

---

### Post by joshbanter on 2008-02-02
> You can also try Fluxbuntu - it is lighter than Ubuntu and Xubuntu.
Mmm, I didn't see Fluxbuntu anywhere in Ubuntu website. Does it have any affiliation with Ubuntu?

> Yeah, try Damn Small Linux, Puppy or Fluxubuntu.
How much RAM does it have? It's worth upping it to 512 if you can find the ram for it, as it will make a huge difference.
Does Puppy or Fluxbuntu come with synaptic manager? I tried DSL before but I couldn't find it anywhere.  Also, it was rather boring I mean compared to Ubuntu or even Xubuntu. Lol, maybe I'm asking too much here. 

I don't think I'm going to upgrade the memory since it's working alright with Windows 98. It's just that it's been left alone for some time and there were few missing installed component. So I need to do an OS reinstall and I thought I'd try some other OS on it while I'm at it. But I'll give Fluxbuntu a try if I can find the site to download. Hopefully, the iso file isn't so big, I'm at 256kbps connection! :tongue:

> You could try the kernel, but I doubt it will have a huge speed increase. The package you want (assuming you installed Ubuntu 7.10) is linux-image-2.6.22-14-i386. The best bet for your computer would actually be compiling your own kernel (if you are ok with doing this the harder way). Here is a guide for that: [http://beginlinux.com/index.php/desk...e_m/ub_compile](http://beginlinux.com/index.php/desk...e_m/ub_compile).

The custom-compiled kernel can be trimmed to your hardware, and is optimized for your processor, so it will see the largest speed increase.
Mmm, yeah it was Ubuntu 7.10 but I already switched to Xubuntu, are those(guide & linux-image) still applicable?

Anyway thanks for the feedback everyone.....

---

### Post by Julita on 2008-02-02
All the information about Fluxbuntu is available here: [www.fluxbuntu.org](www.fluxbuntu.org)
The ISO image for your architecture is here: [http://releases.fluxbuntu.org/7.10/rc/fluxbuntu-7.10-installer-i386.iso](http://releases.fluxbuntu.org/7.10/rc/fluxbuntu-7.10-installer-i386.iso)

Sure, it has Synaptic and everything, just as Xubuntu ))

---

### Post by joshbanter on 2008-02-02
> **Julita said:**
> All the information about Fluxbuntu is available here: [www.fluxbuntu.org](www.fluxbuntu.org)
The ISO image for your architecture is here: [http://releases.fluxbuntu.org/7.10/rc/fluxbuntu-7.10-installer-i386.iso](http://releases.fluxbuntu.org/7.10/rc/fluxbuntu-7.10-installer-i386.iso)

Sure, it has Synaptic and everything, just as Xubuntu ))
That's good to know :D Thanks for the links.

---

