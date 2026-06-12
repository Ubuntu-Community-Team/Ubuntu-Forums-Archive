---
title: "dual monitor set up issues"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by blubyu1914 on 2008-02-29
Ok everyone. I'm very new to Ubuntu. I've recently built my first computer and made the switch from Windows to Linux. Very Happy so far!!!! Running Ubuntu 7.10 with no issues. I decided to upgrade to an Nvidia GeForce 7600 LE graphics card. My motherboard does have an integrated Chrome9 HC IGP. I have searched thru the forums for the last two days trying to solve my problem. With Geforce card installed, I get only black screens when computer boots. Both monitors says no signal. If I removed the Geforce card, I get a signal again thru the integrated graphics. I've been into the BIOS to disable the integrated graphics, but the only option I see is to change the settings to allow to boot to PCIE or PCI. Nothing to disable completely. Also, I have installed Envy and tried to install Nvidia drivers. This gives me an error message because the card is not installed..  I'm at the point of returning the card and trying another one. But, not 100% it's the Nvidia card that's not functioning.... Any help would be greatly appreciated.:confused:

---

### Post by Sam Lars on 2008-02-29
You should at least see the BIOS load screen and the Grub come up... if you don't, it's in BIOS or hardware.

---

### Post by blubyu1914 on 2008-03-01
ok. Thanks for the reply. I've researched my MB, it's a ESC P4M900T-M. Nothing I can find states anything to do differently to disable the integrated graphics. So, that leaves only the new graphics card. I'll return it tomorrow, get a new one and see what happens.. Anyone else with any other suggestions would be helpful before I return this.

thx

---

### Post by jezebel on 2008-03-01
Hi.

Not sure I'm equipped to help, but here goes..

Nvidia and Ubuntu don't play nice together with dual monitors, number one. So...can you first try to disconnect your secondary monitor and reboot?

If you still get the black screen of death, leave your Nvidia card in, but run in safe mode (can't remember how to do that) and from there, get Envy ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)). Envy is better than the built in drivers on Gutsy.

Then restart and see how you go. 

Once you get one monitor working well, then hook up the other. Then you can deal with a whole other set of challenges:)

J.

PS - I'm running dual monitor set up on Gutsy with a (real cheap) Geforce 5200.

---

### Post by blubyu1914 on 2008-03-01
I already tried that as well. Even with Nvidia card installed and one monitor installed, still nothing but black screen of DEATH!!! No signal from monitor....

thx:confused:

---

### Post by blubyu1914 on 2008-03-02
Thanks for all the help. I solved my problem. It was the graphics card. Returned the old one, bought a better one, installed and working just fine now.:guitar:

---

