---
title: "Help with ATI graphics drivers"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by thesheqq on 2007-04-10
I am having some trouble installing my graphics drivers.  Keep in mind I am a noob.  
lspci output for applicable parameters is as follows:
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

I am pretty sure I located the correct driver downloads from the ATI website support and downloads.  I am just not sure what to do next.  I am running Ubuntu Edgy Eft.  And while I mention it, since I am just starting off setting up my system would you all recommend upgrading to the new release I believe it's Feist?  Thanks in advance, ubuntu why can't it just work.

---

### Post by mills on 2007-04-10
[envy]("http://www.albertomilone.com/nvidia_scripts1.html") should do the trick, sorry but i dont know how to do it the hard way:)

---

### Post by rufius on 2007-04-10
You'll be better off with the xorg-driver-fglrx from Ubuntu's restricted repo's. 

Here's a howto on installing it: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

As for installing Feisty, I would recommend it. Its a great release (even in beta). It made installing restricted drivers (ie: ATI and intel wireless) incredibly simple. Though if you're new, I'd wait till a couple weeks after release (so sometime in May).

---

### Post by hardyn on 2007-04-10
its not as fast... but i have found the Mesa, 'radeon' open source driver to have better stablility than the ati binary.

---

### Post by thesheqq on 2007-04-10
Thanks for the quick response guys, I just got back to the comp station so I'm gonna go try out these solutions.  Just wanted to say thanks for getting back to me so quick and keep the advice coming if you can.  I'll be back soon with results.:guitar:

---

### Post by thesheqq on 2007-04-10
Ok so I think I have an idea of what my problem is lemme know if these seems plausible.  I installed Edgy Eft and in many of the forums, HOWTOs, and documentation it listed updating graphics drivers as one of the first things to do after the first update.  I think somewhere there was a test(GUI) to see if 3D and direct rendering were working.  I remember it said I didn't and needed the driver.  Well, I wasn't aware at the time but the kernel for Edgy already came with an open source ATI Radeon module.  So I think I ended up having two drivers installed...which I imagine is a problem...any thoughts or insight?  :mad:

---

### Post by hardyn on 2007-04-11
nope... only the load that is loaded by xorg.conf will be envoked... it usally comes along for the ride.  a new install of ubuntu will give you radeon, ati, nv, vesa, and a few others.  if you are having more problems its something else.

i have never had a problem with the mesa drivers, but the ATI drivers are somewhat intrusive... and will alter some of the files that 'radeon' uses.  if you are planning to fall back to the open source drivers after installing the binary drivers, you must reinstall radeon, and anything else referring to dri or mesa in synaptic.

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

i have found this to be the best resource for the installation of ati drivers on an ubuntu machine.

good luck.

---

