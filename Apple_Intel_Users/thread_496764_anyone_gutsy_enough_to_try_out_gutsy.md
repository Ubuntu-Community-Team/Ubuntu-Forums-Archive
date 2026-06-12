---
title: "anyone gutsy enough to try out gutsy?"
date: 2007-07-09
forum: Apple Intel Users
---

### Post by cryptocoryne on 2007-07-09
For "alpha-quality" this is amazing! I got everything to work on a 2nd gen. macbook dual booting OS X and ubuntu in about two days of fiddling. compiz eye-candy even seems to be working. I'm still testing sleep, but it is too soon to tell if it's 100% reliable.  

There were two small hassles:
1.
I spent forever trying to install madwifi and iSight drivers until I noticed that, for some reason, installing linux-headers-2.6.22-7-generic failed to create the symlink
```

/lib/modules/2.6.22-7-generic/build -> /usr/src/linux-headers-2.6.22-7-generic/

```

2.
I wanted read-only access to my OS X music folder in linux and had to create ab ubuntu user with the same name and GID # as my OS X username.

Is there anything like the old PPC app. "Mac on Linux" for intel macs? I'd prefer to avoid buying Parallels Desktop or vmware if possible.  I remember trying vmware in the past and having my laptop burn a hole in the desk.:lolflag:

---

### Post by tgoose on 2007-07-09
There's all the qemu stuff for virtualisation, but I only used it briefly so I don't know how well it works.

I was pretty amazed by the live CD of Gutsy: all stuff I'd had to fiddle with configs and CLI and compiling for on Feisty just worked on boot up! (apart from networking..!)

For an alpha, this is definitely remarkable with Compiz. I liked the idea of a Mozilla OpenOffice.org plugin as well, but without access to the Internet I couldn't install it. I'll perhaps download the .deb in Feisty and install it in Gutsy if I get bored, though.

The new GIMP seems nice, and in the hour or so of running I had no crashes. There's still no way I'm replacing Feisty till it gets at least to beta though, since I'm pretty reliant on this laptop actually working!

---

### Post by ryan86corolla on 2007-07-09
you could try virtualbox for emulation. i haven't used it, but i've heard it's good.

---

### Post by cyberdork33 on 2007-07-09
I had a few issues with my iMac. I could fiddle and get Xorg to start, but I didn't do much more than that.

---

### Post by tomaspollak on 2007-07-09
yup, i've been trying to set up Gutsy on a MBP third generation (the new ones with LED displays & Nvidia GPU's)... although Gutsy look great, most of the hardware didn't work at first boot.

I've already managed to set up wifi, sound & keyboard backlight (through pommed). but i'm still using the "vesa" driver for display, since neither the "nvidia" nor the "nv" driver work. :(

---

### Post by ThufirHawat on 2007-07-10
I do believe, on the basis of my experience with Feisty on my MacBook Pro 2.33 GHz, C2Duo, that in order to get Ubuntu to work one must:

- have a not too new CPU (=SantaRosa bad);
- have a lot of patience;
- pray that the developers will understand that if they do not fix the unholy mess with the WiFi, than it is going to be a release about as worthless as Feisty.

Let me specify: I have stopped using Ubuntu because I have invested a lot of hours tweaking madwifi, ndiswrapper, whatever, without ever getting it to work in my home WPA2 network.

Please do not provide me with yet another hint on how to do it.
I do not believe it can be done with Feisty. Full stop.
I challenge anybody who has a MacBook Pro 2.33 GHz, working on a WPA2 network, to tell me how it was done (not how they think it could be done: *being there, done that...*)without three indirection links.

I will wait for Gutsy with impatience, but the very first thing I am going to check is the network specs.

Cheers to all the good souls on this board, who helped my with everything so far.

---

### Post by cyberdork33 on 2007-07-10
> **ThufirHawat said:**
> - have a not too new CPU (=SantaRosa bad);
nope, other hardware, yes, CPU, no
> - have a lot of patience;definitely
> - pray that the developers will understand that if they do not fix the unholy mess with the WiFi, than it is going to be a release about as worthless as Feisty.Talk to Broadcom / Atheros. They are the ones that do not support linux.

---

### Post by sergiez on 2007-07-10
I am trying Gutsy in a Mac Pro and it runs almost everything out of the box. I did not check wifi nor bluetooth. I had no problems in Feisty so I hope nothing will be broken in Gutsy.

Regards.

---

### Post by onechard on 2007-07-11
working fine here on first gen macbook pro 17 have gotten everything working right running kubuntu gutsy :)

---

### Post by rockingmtranch on 2007-07-12
:)

---

### Post by benanzo on 2007-07-12
I booted up the latest Gutsy LiveCD on my first gen MacBook last night and was *impressed*.  Finally I get my native resolution of 1280x800 out of the box (because they switched to using the **intel** driver rather than **i810**.  They've still got Xorg 7.2 installed, but I imagine as 7.3 gets closer and closer we'll see that migration happen before release time in OCtober.  No need for 915resolution anymore.  Also I noticed that Compiz (desktop-effects) was enabled by default, which is awesome.  Restricted Manager enabled my wireless out of the box as well (as it did in Feisty.)  I also like the update to gnome-power-manager that automatically dims your screen if inactive.  This is really starting to feel like a great laptop experience instead of a series of hacks.

I had a ton of fun for a few hours playing around with all the updated GNOME apps like Totem, Rhythmbox etc.  I'm still having trouble rationalizing why they're sticking with Evolution as the default E-mail client instead of moving to Thunderbird.  I suppose it's because Evolution has good integration with GNOME and integrated calendar memos, task, contacts etc.  I would still like to see the Mozilla suite installed as default (Firefox, Thunderbird, Sunbird.)

It's looking to be a good release.

---

### Post by thully on 2007-07-12
The intel driver is actually in Feisty - it just isn't enabled by default.  I actually changed the MacBook wiki to use this rather than 915resolution, as that is a pretty crude BIOS hack. Anyway, I have actually used Gutsy on my first generation MacBook as well, and I definitely agree that it is coming along quite well.  However, I think I may opt to do Feisty for now and do a chroot (basically a directory containing a Gutsy install on my Feisty partition that I can use with the chroot command) once I figure out how.

---

### Post by MichaëlVD on 2007-07-14
Gutsy works fine here on my Intel iMac 20". However, I can't get my iSight to work, and, more importantly, wireless doesn't work either.

lscpi does refer to "03:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)", but I don't see anything about wireless in the 'restricted drivers' dialog.

---

### Post by Nekiruhs on 2007-07-14
Well, me! I'm working on a new distro and am using some gutsy packages.

---

### Post by cyberdork33 on 2007-07-14
> **MichaëlVD said:**
> Gutsy works fine here on my Intel iMac 20". However, I can't get my iSight to work, and, more importantly, wireless doesn't work either.

lscpi does refer to "03:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)", but I don't see anything about wireless in the 'restricted drivers' dialog.

you are going to have to use ndiswrapper

---

### Post by MichaëlVD on 2007-07-15
> **cyberdork33 said:**
> you are going to have to use ndiswrapper

The Tribe 2 release notes say that restricted-manager can now fetch and install bcm43xx drivers itself... Maybe what I'm seeing is a regression since Tribe 2?

---

### Post by MichaëlVD on 2007-07-15
I got it to work now, after some fiddling and a restart. Time to cut the cord!

---

### Post by cyberdork33 on 2007-07-15
it was my understanding the the bcm43xx module does not support the 802.11n broadcom cards.

---

### Post by MichaëlVD on 2007-07-15
Well, it's working, but I don't see anything in the restricted-drivers window. The 'fiddling' I mentioned involved ndiswrapper, so I guess that is what is doing the job now.

---

### Post by ShirishAg75 on 2007-07-16
Well guys, I'm on a 3.5 yr. old desktop (maybe older as p4 1.8 ghz came out end 2k3 IIRC) but anyways, things working great sound, ethernet,all up ,  there is the usual breakage like [http://paste.ubuntu-nl.org/30130/](http://paste.ubuntu-nl.org/30130/) for instance but other than that, things are cool. I am using  1:7.2-3ubuntu4 with intel i810 driver though. The intel driver hasn't been too kind nor has xrandr or grandr :(

---

