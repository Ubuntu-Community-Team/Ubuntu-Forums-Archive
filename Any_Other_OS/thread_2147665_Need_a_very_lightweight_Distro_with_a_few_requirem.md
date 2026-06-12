---
title: "Need a very lightweight Distro with a few requirements for a rookie (OLDD machine)"
date: 2013-05-22
forum: Any Other OS
---

### Post by Psxsage on 2013-05-22
Looking for suggestions for a lightweight Distro for an old Dell C600 Pentium 3 800 mhz 512MB ram 20GB HD laptop.  I replaced a few parts in this machine to get it running again for a friend who has fallen on hard times.  I'm going to give him the machine but it currently has No OS and he has little to no experience with Linux other than using Chromium for 5 minutes on my Xubuntu machine :p

So i need the Distro to do the following.

1. Work well with a USB WIFI B/G adapter as this unit has no internal wifi and the PCMIA port is shot

2. Be relatively fast so the poor kid isn't sitting there all day waiting for it.  (I did try an old XP disc i had sitting around and the machine just can't handle it worth a damn)

3. Be fairly easy for someone with zero Linux experience to use for VERY basic tasks IE Browsing,Text Documents etc.

My Initial thought was DSL however i think that's a bit complicated for someone with little to no Linux use under their belt (Nor am i an Expert but compared to him i have a PHD in Linux :p)


Cheers

---

### Post by d.atanasov on 2013-05-22
Hi, 

I have tried Puppy linux and it is cute and done for old machines.
[http://www.puppylinux.com/](http://www.puppylinux.com/)
i have no idea however how it is now as I haven`t used it a lot. I hope that this can be enough. 

cheers

---

### Post by ubu_dynamite on 2013-05-22
You could do a minimal install with a light desktop and just the programs you really need.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by binaryhermit on 2013-05-22
Lubuntu might work, though it might be a little slow.  It'd probably help if you could bump the RAM up to 1 GB, though.

---

### Post by Irihapeti on 2013-05-22
My EeePC900 is 900MHz and about the only problem I have with that is streaming Flash videos stuttering from time to time. (Not that I have that problem on my own.) It does have 1GB of RAM, so as has already been suggested, boosting the RAM would help.

I avoid KDE and a full Unity desktop. 12.04 Gnome classic works fine. Xubuntu would also be an option.

If you can't increase the memory, I'd think about installing Openbox, especially if you're able to do a little handholding for a while. Yes, I know it takes some setting up, but once that's done, it should be fine. Especially for someone with basic needs who's not into fiddling with things.

---

### Post by mips on 2013-05-23
Nothing more demandin than Openbox I would say.

Also see [http://ubuntuforums.org/showthread.php?t=2143547](http://ubuntuforums.org/showthread.php?t=2143547)

Try cruchbang, archbang, slitaz, tiny core, dsl, puppy.

---

### Post by mörgæs on 2013-05-23
Sorry, but it's too weak for any practical use. 

The least problem is getting an operative system running, what matters most are applications like a browser and a media player. You will not get a decent speed out of them.

A 900 MHz EEE is by far superior to a 800 MHz Pentium 3 from around year 2000. The processors do not compare Hz for Hz.

---

### Post by vasa1 on 2013-05-23
> **mips said:**
> Nothing more demandin than Openbox I would say.
....
How is Openbox **more** demanding ???

---

### Post by Moose on 2013-05-23
> **d.atanasov said:**
> Hi, 

I have tried Puppy linux and it is cute and done for old machines.
[http://www.puppylinux.com/](http://www.puppylinux.com/)
i have no idea however how it is now as I haven`t used it a lot. I hope that this can be enough. 

cheers

+1. I installed Puppy on my Uncle's desktop that was about 10 years old, and works like a charm!

---

### Post by deadflowr on 2013-05-23
Outside of light distros like puppy or crunchbang, I say build off of a minimal install, and pick a barebones window manager like openbox.
Then install the lightest barebones browsers,text editors, etc you can find.

It's old, though, so it's still gonna be slow no matter what you do.
But it can still be functional, sort of.

---

### Post by mips on 2013-05-24
> **vasa1 said:**
> How is Openbox **more** demanding ???

I think you should read my post again, I never said openbox is more demanding.

---

### Post by vasa1 on 2013-05-24
> **mips said:**
> I think you should read my post again, I never said openbox is more demanding.
Sorry. What exactly did you mean?

---

### Post by mips on 2013-05-24
> **vasa1 said:**
> Sorry. What exactly did you mean?

Exactly what I wrote,

> [COLOR=#000000]**Nothing *more* demanding *than*** Openbox I would say.[/COLOR]

Which in english means you should not look at anything that is heavier on resources than openbox. This does not mean openbox is heavy on resources, I'm saying not to use anything that requires more than openbox does which is lightweight.

---

### Post by deadflowr on 2013-05-24
I agree with mips, the machine is going to be taxed enough already, even before a desktop is involved.

If it was me, I'd forget about making it into any sort of productive desktop and have fun turning it into a learners server.
And by learners server, I'd use it not for productive use, but for academic reasons. Like how a server works, and how to make a server do what I want.

But it's not me and the OP is doing this for a friend in need of a working machine.

---

