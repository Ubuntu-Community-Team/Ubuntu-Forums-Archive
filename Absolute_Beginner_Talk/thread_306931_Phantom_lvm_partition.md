---
title: "Phantom lvm partition?"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by BaronStinky on 2006-11-25
After searching exhaustively, I'm still clueless as to how I can increase my swap partition with Gparted. My system is as follows:

Compaq Presario 1200 (Model 12XL510A)
PIII 700mhz
128 MB ram
40 GB HD
running edgy 6.10
(I couldn't install ubuntu probperly, so I installed using the Xubuntu alternate cd then used synaptic to install gnome)

This screenshot was taken while up and running from the hd, but it's the same gig when running from the CD:

[IMG]http://www.radiounready.com/pics/Gpartedscreen2.png[/IMG]
The problem is this:

I want to use the Gparted liveCD to decrease the extended partition on hda2 so that I can increase linux-swap on hda5. Hda6 is marked as an lvm. I've looked into lvm, but I don't yet understand it, nor did I attempt to do anything with logical volumes on install. Neither the gparted live cd nor ubuntu recognize its filesystem and all I can do is delete it. I cannot increase or decrease the size of hda2 without first deleting hda6, however, deleting hda6 leaves me with almost 40gb of unaccounted for space. I know for a fact that the hd is 40 gigs, so what gives? I don't want to actually process the deletion and resizing until I know what's going on. Admittedly, my knowledge on this is very limited. Ultimately, I guess I'm asking for an explanation of exactly what is on hda6. Is it necessary? How did it get there? It appears to be part of hda2 but again, deleting it adds phantom disk space. Any help is appreciated.

---

