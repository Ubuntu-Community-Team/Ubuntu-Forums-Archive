---
title: "Ubuntu Running Sluggishly, need help!"
date: 2005-10-30
forum: Absolute Beginner Talk
---

### Post by Animus on 2005-10-30
I just installed Ubuntu, however, everything is running kinda slowly, like its on a slower system, my specs are the following:

MSI neo2 platinum nforce 3 mobo
AMD 3500+ Athlon 64 processor
1 gig of corsair dual channel memory
1 80 gig HD
ATI X800 XL AGP

However, everything kinda stutters a lot, like when I move windows around, or switch programs, its like Ubuntu isn't recognizing my total system resources.

Anyways, I hope someone can give me a hand, as I like the OS thus far, and am just trying to iron out the few problems that I have.

---

### Post by Breaks on 2005-10-30
Actually i must admit that quite recently ive been noticing considerable changes in the speed of ubuntu with my system and im running a P4, 3GHz also. One of the latest updates isnt the reason behind this is it?

---

### Post by Animus on 2005-10-30
Yeah, I'm kinda dissapointed, as I was impressed by the fluidity of everything when I used it earlier

---

### Post by gt24 on 2005-10-30
Are you using the 686 kernel are or you still on the 386 kernel?

(just thought to throw that out... it might help)

---

### Post by nitricacid on 2005-10-30
[QUOTE=gt24]Are you using the 686 kernel are or you still on the 386 kernel?

(just thought to throw that out... it might help)[/QUOTE]

How do you pick and choose, let alone install that?

---

### Post by Animus on 2005-10-31
386 I think...its whatever came with the X86 download from the Ubuntu.com site....

I dunno...everything just seems to have a stutter to it.  The refresh rate it also stuck at 60hz, which kinda exacerbates the problem.  I'm working on sorting that out in a different thread though.

---

### Post by Qrk on 2005-10-31
Downloading a new kernel is easy.

Just open up synaptic and download linux-686 (for P4) or linux-k7 (for athlon xp)

For 64 bit I'm not sure if its in the 32 bit repos.

As for the general sluggishness... I had the same problem when xorg was set to nv. It went away after changing to vesa and downloading the nvidia-glx package. I'd try switching to vesa by

sudo dpkg-reconfigure xserver-xorg

and in the second screen switch to vesa. If you have an ati card you can't use the nvidia package.

---

### Post by poofyhairguy on 2005-10-31
[QUOTE=Qrk]Downloading a new kernel is easy.

Just open up synaptic and download linux-686 (for P4) or linux-k7 (for athlon xp)

For 64 bit I'm not sure if its in the 32 bit repos.

As for the general sluggishness... I had the same problem when xorg was set to nv. It went away after changing to vesa and downloading the nvidia-glx package. I'd try switching to vesa by

sudo dpkg-reconfigure xserver-xorg

and in the second screen switch to vesa. If you have an ati card you can't use the nvidia package.[/QUOTE]


The orginal poster has an ATI card so that won't help. A new kernel might. Try this command:

sudo apt-get install linux-686

---

### Post by darrenrxm on 2005-10-31
I got this from a ubuntu review at distrowatch.

> A minor annoyance was that the wrong kernel was installed. In this case, "wrong" was not disastrous. What happened was that a 386 kernel was installed even though I have a 686 processor.** The machine ran OK, but performance clearly suffered.** I initially filed a bug report, but the developers replied that the Ubuntu CD just doesn't have room for multiple kernels so they have to go with the lowest common denominator, which is 386. You can check which kernel is installed as follows:

  root@x31:~> uname -r
  2.6.12-9-386

The solution is to upgrade your kernel. If you're upgrading to a 686-based kernel, the command would be as follows:

  apt-get install linux-686

I assume the above is a non-issue if you install Ubuntu on an AMD64 or PPC.

[www.distrowatch.com](www.distrowatch.com)

---

### Post by Animus on 2005-10-31
Alright, I'm updating the kernal to 686 now...

Is there a better solution to take full advantage of my video cards capabilities?

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=Qrk]As for the general sluggishness... I had the same problem when xorg was set to nv. It went away after changing to vesa and downloading the nvidia-glx package. I'd try switching to vesa by

sudo dpkg-reconfigure xserver-xorg

and in the second screen switch to vesa. [/QUOTE]

Let me know if I should start a new thread on this; I don't want to hijack this one.

I have a notebook with an nVidia Go 6800 and I too have been disappointed with the sluggish GUI.  I am running the nVida drivers that I installed via apt-get.  I was also disappointed to find that the nVidia Control Panel has absolutely no advanced settings available in it.

My questions are:

1.  I was planning on going through the rigmarole of installing the latest drivers from nVidia directly.  Will this help with performance and get me a useful nVidia control panel?

2.  Should I do the tasks quoted above after doing so?

Thanks, 

-Doc

---

### Post by Doc.Caliban on 2005-11-01
[QUOTE=Qrk]
sudo dpkg-reconfigure xserver-xorg

and in the second screen switch to vesa. If you have an ati card you can't use the nvidia package.[/QUOTE]

OK, I knew I was a kid with a loaded gun as soon as I fired up this command. :D 

So now I've gone and cludged my xserver settings and can't launch the GUI.  Is there a painless way to get back to the original config?

Thanks,

-Doc

---

### Post by Doc.Caliban on 2005-11-01
[QUOTE=Doc.Caliban]OK, I knew I was a kid with a loaded gun as soon as I fired up this command. :D 

So now I've gone and cludged my xserver settings and can't launch the GUI.  Is there a painless way to get back to the original config?

Thanks,

-Doc[/QUOTE]


Update:  I re-ran the config program and hit escape all the way through it.  Now I can get back into GNOME, but I'm sure a lot of the settings for x-server are now incorrect.  How can I clean it up?

-Doc

---

### Post by Doc.Caliban on 2005-11-01
Well, in my haste to fix this, I think I overwrote my good backup copy of xorg.conf by rerunning the config and hitting esc all the way through.  Oh well.

So now my question is simply, how can I know that my conf file is configured properly?

-Doc

---

### Post by Qrk on 2005-11-02
retype

sudo dpkg-reconfigure xserver-xorg

I wouldn't use vesa. I always suggest vesa because it seems to support the most hardware, but I may be wrong, or you might be unlucky, or both.

You probably should try the "nvidia" one, it probably will work. If that doesn't nv is also a safe bet.

---

