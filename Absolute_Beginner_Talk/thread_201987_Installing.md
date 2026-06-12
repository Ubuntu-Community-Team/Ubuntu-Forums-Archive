---
title: "Installing"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by Paradoxum on 2006-06-22
Hi,

I'm new to linux, but have tried slackware briefly in the past..

Im downloading 6.06 dvd i386 iso via way of torrent, and i have 2 partitions on my HD, 1 is an NTFS windows XP and the other is 8GB NTFS partition. 

When installing Ubuntu is it possible to install to that 8GB partition? (formatting beforehand from the installer, as i believe linux doesn't work with NTFS?)

that's what i did with Slackware, and it worked fine. But i tried to install opensuse this morning and the partition options really confused me and i wasnt sure, so i never ended up doing it.

another question is, when running games via WINE, will it possible to play them over the network, with my brother whos running WinXP? I should assume so..but just making sure.

thanks!

---

### Post by bruce89 on 2006-06-22
[QUOTE=Paradoxum]
When installing Ubuntu is it possible to install to that 8GB partition? (formatting beforehand from the installer, as i believe linux doesn't work with NTFS?)

that's what i did with Slackware, and it worked fine. But i tried to install opensuse this morning and the partition options really confused me and i wasnt sure, so i never ended up doing it.[/QUOTE]
Yes, that will work, but I think you'll have to use manual mode.  Somebody else can advise how much space you need for / and how much for swap.

---

### Post by Paradoxum on 2006-06-22
Alright, hope someone can help me with that then.

Third question...just what is the difference between all these distro's? I understand they all use gnome/kde interface, so they all tend to LOOK the same..and feel the same, so i assume the differences is functionality, in the code and how the OS generally works? for example what does ubuntu have or do, which slackware doesnt? and vice versa?

thanks again.

---

### Post by lamego on 2006-06-22
GNOME and KDE are very customizable, the way the menus, panels etc can be layed out on complete differente ways...
Also the version of the applications will depend on the distro upgrade policy, some keep using older but more stable versions while others prefer to give you the bleeding edge.
Also the way you install applications and configure the system in general is usually very different between major distros, same for the installer...

---

### Post by bruce89 on 2006-06-22
[QUOTE=Paradoxum]Alright, hope someone can help me with that then.

Third question...just what is the difference between all these distro's? I understand they all use gnome/kde interface, so they all tend to LOOK the same..and feel the same, so i assume the differences is functionality, in the code and how the OS generally works? for example what does ubuntu have or do, which slackware doesnt? and vice versa?

thanks again.[/QUOTE]
Ubuntu has APT, a powerful package installer which makes install new software very easy.  Slackware doesn't.  I mean, all distros are much the same really, they have different philosophies, DE's etc.  Ubuntu uses GNOME.

[QUOTE=Paradoxum]another question is, when running games via WINE, will it possible to play them over the network, with my brother whos running WinXP? I should assume so..but just making sure.[/QUOTE]
Games don't really work in WINE, but I can't use WINE as I use AMD64, so I don't really know how well programs work first hand.

---

### Post by Brunellus on 2006-06-22
They're all Linux--at least the kernel is.  But there are differences in each distribution as to the exact software included.  Some distros use more bleeding-edge stuff...others use very old but stable stuff (like, say Debian Stable).  

Same goes with kernels.  Ubuntu doesn't run a plain vanilla kernel;  it takes the current 2.6 kernel and applies its own patches.  Those patches eventually make it upstream, but the default ubuntu kernel is not the kernel you get from kernel.org, nor is it necessarily the same kernel you'd get from slackware.

Ubuntu uses .deb packages and apt for software installation.  This vastly simplifies administration by downloading and installing the package you want ALONG WITH ALL ITS DEPENDENCIES.

---

### Post by Paradoxum on 2006-06-22
Thanks for the replies. But can anyone help with the installing to that partition i mentioned?

---

### Post by bruce89 on 2006-06-22
[QUOTE=Paradoxum]Thanks for the replies. But can anyone help with the installing to that partition i mentioned?[/QUOTE]
General consensus is that the last bit of the disc you want to install on is used as swap, and it usually is at least the same size as your RAM.  The rest of the disc you want to use can be used for /.  See - [http://psychocats.net/ubuntu/partitioning.html](http://psychocats.net/ubuntu/partitioning.html) for a good guide.

---

