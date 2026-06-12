---
title: "Run Photoshop CS3 on Wine"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by dannymichel on 2007-06-09
is is possible?
If so, does it run ok?

---

### Post by starcraft.man on 2007-06-09
[Have a look for yourself.]("http://appdb.winehq.org/appview.php?iAppId=17") I believe the answer is pretty much no unless you go to a lot of trouble and copy a lot of registry/other files from a Windows install of it (even then it'd probably be poor running). If you have a copy of windows, I'd just make a VM out of it with [Virtual Box.]("http://www.virtualbox.org/")

IMO though, the even better option is to explore GNU Image Manipulation Program, or maybe Krita. There are lots of apps like it, that do everything most people need. If you absolutely need cs3, go the way of the VM.

Oh and the latest version to run really well in WINE I believe is 7.

---

### Post by JAPrufrock on 2007-06-09
go [here]("http://appdb.winehq.org/appview.php?iAppId=17")

---

### Post by Acglaphotis on 2007-06-09
Men, you are taking the longest shot possible... you are shooting to your front and your expecting to hit your back. Not even CS 1 runs on wine. I recommend CS2 on qemu and KVM it runs REALLY fast. I tried CS3 but it slows downs the machine a lot.

---

### Post by Brightbelt on 2007-06-09
I own and use CS3 with Vista, but I'm currently running PS 7.0 on wine and I re-discovered something Wonderful about PS 7.0....
No Activations!!!! 

Frank B.

---

### Post by mfratt on 2007-06-11
I need CS3 because it does do several things that the GIMP won't, so I guess I'll have to run it on an emulated XP for now.

---

### Post by dannymichel on 2007-06-11
Would VMWare do the trick on Ubuntu?
Can you install an app on VMWare standalone without first installing the whole OS through VMWare then the app in that virtual OS?

---

### Post by anaconda on 2007-06-12
CS2 works in wine.. CS3 doesn't yet.

try portable photoshop CS2 it should work fine. The only? thing that wont work is text-layers, but even those will start working if you install MS-fonts to wine.....

And vmware would do the "trick", but since vmware doesnt have proper support for feistys new kernel yet (ie. it is currently quite slow). I would recommend trying Virtualbox  first.

---

### Post by Golyadkin on 2007-06-12
> **dannymichel said:**
> 
Can you install an app on VMWare standalone without first installing the whole OS through VMWare then the app in that virtual OS?

No, VMware needs to have an OS installed. It is just like a real computer, you can't install software on a computer without an operating system, because it will never boot.

---

### Post by MenZa on 2007-06-12
I think the chances of running Photoshop CS3 in Wine are pretty much zero; instead, why not take a look at mikeytag's little Seamless Virtualisation guide [right here on the forums](http://ubuntuforums.org/showthread.php?t=433359)? I recommend running Windows XP Pro, rather than Vista in your virtual machine, so as to conserve resources.

---

### Post by jmchaffie on 2007-12-26
Just a note all... I've installed my copy of CS3 inside of a XPSP2 VirtualBox and it did run fine, however, all of the 3D functions are *REVERSED*

What I mean by this is that when you load in a 3D model / mesh to work with.. for whatever reason, say it's a human shape... the hand closest to you is small, and the one farthest from you is huge. It's like the 3D engine has its perspective reversed from x to -x.

Anyway, just something I thought I'd drop in case someone was looking forward to using that feature.

Other than that, it realy seems to work just fine. No major lag, filters all work fine, etc. 

If you don't need 3D mapping... you're all set in a VB.

Take care,
John

---

### Post by bharadwaj on 2007-12-29
Vmware would fix the problem with Photoshop but you may need very high memory to run you VM with photoshop

---

### Post by daulex on 2008-01-19
how high?

---

### Post by yesudeep on 2008-03-15
> **MenZa said:**
> I think the chances of running Photoshop CS3 in Wine are pretty much zero; instead, why not take a look at mikeytag's little Seamless Virtualisation guide [right here on the forums](http://ubuntuforums.org/showthread.php?t=433359)? I recommend running Windows XP Pro, rather than Vista in your virtual machine, so as to conserve resources.
The chances of running Photoshop CS3 under WINE aren't anywhere near zero.
The latest bleeding edge version in the WINE git repo is already able to start Photoshop CS3.  It's a matter of a few weeks before visible bugs get squashed.  WINE is an implementation of the Windows API.  Stay tuned.

---

### Post by lolzlolz on 2008-04-04
yay for wine, i saw that a few days ago, can't wait for the last bugs to be gone :)

---

