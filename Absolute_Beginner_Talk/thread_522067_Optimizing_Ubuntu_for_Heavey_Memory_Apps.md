---
title: "Optimizing Ubuntu for Heavey Memory Apps"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by XCan on 2007-08-10
I just recently installed Ubuntu. The main reason for it was the stupid memory handling in Windoows. I am running  pretty intensive calculations  on the worksttation. The app in question is unfortunnetly written in java (at least the GUI) part. I was wondering if there ways to optimise the OS to work the best with single heavy memory apps. The issue seems like the system swaps a LOT, even though there are lots of data I only need to access once in a very long while,, thus slowing down the rest of the system. I understand that there is swapiness, but haven't dared to try it yet. I'm also interested in if there are other ways.

---

### Post by kerry_s on 2007-08-10
how much ram do you have?

switching to a lighter gui will help alot.

---

### Post by userundefine on 2007-08-10
[Check out this article.]("http://kerneltrap.org/node/3660")

You could also switch to Fluxbox.  Gnome is top-heavy.

---

### Post by schorsch on 2007-08-10
You can try to optimize the behaviour of swapping via the kernel parameter "vm.swappiness". The default value is 60; the range is from 0-100 and the higher the value the more the kernel will swap out. So you can try to minimize the value to 10:

```
sudo sysctl -w vm.swappiness=10
```

This change lasts only until the next boot; if you want to set it permanent to a value other than 60, you have to add a line to "/etc/sysctl.conf"

```
vm.swappiness=10
```

Take a look [[COLOR="Blue"]here[/COLOR]]("http://kerneltrap.org/node/1044")

---

### Post by hyper_ch on 2007-08-10
You could not load any gui at all to do the calculations...

---

### Post by XCan on 2007-08-10
Thanks for the answers. I currently have 4GB of RAM and have allocated 4GB to swap.  About not having a GUI while doing calculations, it can be done in theory. But the issue is that the calculations are not the only thing hogging memory. As setting everything up (geometry etc) can only be done reasonably easy through the GUI. And it appears like presenting all that information is hogging a lot of memory, although not all information is needed for the calculations, and those get swapped, instead of cleared.

I will test out the swapiness and see if it helps! Thanks again!

---

