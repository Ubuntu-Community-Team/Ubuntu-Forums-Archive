---
title: "Very happy with Dapper on a Powerbook G4"
date: 2006-07-21
forum: Apple PPC Users
---

### Post by K.Mandla on 2006-07-21
I am test driving a Powerbook G4 (12" 867Mhz) a friend wants to sell. I'm very happy with Ubuntu's performance on it thus far. Graphics look good, networking works fine and Gnome is quick and responsive.

I haven't taken the time yet to tinker with the wireless, but I'm sure it won't be a dealbreaker. I also want to fire up the 3D acceleration; somehow I think Wolfenstein ET on that teeny screen will be a real blast! :mrgreen:

Anyway, just an open note of thanks for a distro that works as cleanly on one architecture as another. \\:D/ 

Cheers!

---

### Post by jedsen on 2006-07-21
Glad to hear you're having luck with open source. The wireless should work just fine with Dapper, as the newer kernels have bcm43xx support built into them. No more downloading patches and firmawre!

---

### Post by Skia_42 on 2006-07-21
Did you have any trouble configuring the x server? It was a real pain to do it for the first time on my iMac G3 and eMac G4... I have been thinkign of getting a laptop though, thanks for the input.

---

### Post by TDave on 2006-07-21
Likewise.

I have run Ubuntu dual-boot on my Powerbook G4 since just before the release of 5.04 and loved it.
I had some difficulties with the automatic upgrade to 5.10 (x-server problems) but managed to fix them. (I had no such problems auto-upgrading to 6.06 and was very happy with the new look Gnome.

However, I decided to try out Kubuntu the other week and installed ran KDE alongside Gnome and loved it.

I have since committed a fresh install running just Kubuntu and found it extremely simple to run adn found the KDE tools easier to work with for things like wireless.
I did try to run network-manager when running Gnome but for some reason found that whenever that was running, no connection was possible.

Either way, I think its safe to say that I have been incredibly impressed with the new release, primarily with the new easy-to-install Mac-On-Linux, which makes the few times I need to run OS X a whole lot easier! :-)

---

### Post by K.Mandla on 2006-07-21
I'm running into my first real problem -- not the wireless, like I thought, but graphics-related.

According to my hardware profile and my xorg.conf, I have a 32Mb Nvidia Geforce card. Far as I can tell, that's right.

Ordinarily, on some of my other laptops with nvidia cards, I can apt-get nvidia-glx or nvidia-glx-legacy, and get full 3D acceleration. 

For some reason, I don't have that option with the Powerbook. I can apt-cache search for nvidia, but nothing glx-related (that I can tell) appears. 

Am I stuck without 3D acceleration on this? That doesn't seem like it ought to be the case. But then again, I surfed the Nvidia Web site in hopes of finding some clue ... and there aren't any Linux-on-Mac drivers.

:confused:

---

### Post by Skia_42 on 2006-07-22
> **K.Mandla said:**
> I'm running into my first real problem -- not the wireless, like I thought, but graphics-related.

According to my hardware profile and my xorg.conf, I have a 32Mb Nvidia Geforce card. Far as I can tell, that's right.

Ordinarily, on some of my other laptops with nvidia cards, I can apt-get nvidia-glx or nvidia-glx-legacy, and get full 3D acceleration. 

For some reason, I don't have that option with the Powerbook. I can apt-cache search for nvidia, but nothing glx-related (that I can tell) appears. 

Am I stuck without 3D acceleration on this? That doesn't seem like it ought to be the case. But then again, I surfed the Nvidia Web site in hopes of finding some clue ... and there aren't any Linux-on-Mac drivers.

:confused:
I came across that porblem as well, "apt-get install nvidia" doesn't do anything even if you have the correct repositoies installed.:evil:

---

### Post by K.Mandla on 2006-07-22
Hmmm. I'm going to post the question in a separate thread, so it isn't lost under this one.

I like the size and feel of the Powerbook, but if I can't get full 3D acceleration on it, I don't think I'll keep it. I have a half-dozen older machines that I use for day-to-day tasks; another one (especially at the price he wants) isn't really practical for me.

Cheers!

---

### Post by pindar on 2006-07-22
I'm not 100 % sure, but I think the nvidia package you refer to installs binary drivers which cannot and will never work on PPC architecture since they're x86 only. So you have to make do with the generic nv driver...

---

### Post by K.Mandla on 2006-07-22
Ouch. :cry: That's a dealbreaker, I'm afraid. 

I like the looks and style of the machine, but to be honest, I was looking forward to 3D support. I have plenty of machines for checking email and surfing the net and playing music ... and at the price he wants, it's just not practical.

No matter. I'm sure it will find a home. Thanks everybody for your help. I appreciate it. ;-)

---

### Post by BlueBuntu on 2006-07-22
Hi Mandla,

That's sound pretty good hearing someone got it working. I have PB G4 12 inch 1.5 GHz that I'm planing to install Ubuntu along with Tiger.

I have some questions to ask you about your setup. How did you partition your harddrive. I mean the software you use for partitioning and the way you partition the drive. I'm really wondering about this issue. [-( 

Thanks in advance,

Alez. ;)

---

### Post by K.Mandla on 2006-07-22
Hey Alez. I don't know how much help I will be, since I only had Ubuntu on the PB for a day or so. It ran great though, and short of the wireless (which I never got to) and the 3D acceleration (which kind of ruins it for me), it set itself up automatically.

I didn't dual boot either, since Panther (what I had) doesn't really do anything for me.

However, I'm sure someone can steer you the right way on that. Good luck! ;) 

(Just for the record, I was using the Xubuntu 6.06 PPC iso. I put Gnome on for a little while, but I'm a XFCE fan to the core! :mrgreen: )

---

