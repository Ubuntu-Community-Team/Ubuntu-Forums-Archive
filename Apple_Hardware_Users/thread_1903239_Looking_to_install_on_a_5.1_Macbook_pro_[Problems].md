---
title: "Looking to install on a 5.1 Macbook pro [Problems]"
date: 2012-01-02
forum: Apple Hardware Users
---

### Post by Ogie on 2012-01-02
I'm looking to run a pure ubuntu os on my macbook pro no partition is this possible? 

Also I downloaded ubuntu 10.11 64bit from their website and burned it onto a dvd+r disc threw disk utility and when I restarted and boot from CD and error came up saying "preset is not set" or something like that its to quick to read. I then come up to a screen that asks me to 1.try Ubuntu with out installing, 2.install ubuntu, and 3. detect disc for defects. Each one of these options results in alot of loud disk drive noise and black screens nothing actually happens and I have to force restart.

I'm currently downloading a ubuntu-11.10-desktop-amd64+mac.iso is this the proper os file I should be burning onto a dvd disk? 

If anyone can help me out that be great.

---

### Post by Wolfador on 2012-01-02
You probably need to install refit first since Mac's use EFI not Bios to boot. Then you can boot the install disk, try adding "nomodeset" to the kernel parameters. This resolved the black screen for me.

---

### Post by markthekdeguy on 2012-01-10
I  have a Macbook Pro 5.1 - and the only *buntu's that install easily are 10.04 LTS - best use the 32bit too it seems,  as soon as you do get it installed goto the Ubuntu Mactel PPA and install pommed and the AppleSMC stuff. the 2 Nvidia VGA cards in the laptop the (9400 and 9600)  default to using the higher power card, and, dependng what website you read, they are both powered up at the same time - (but can only use the 'better 9600) - with the resulting loss in battery life, and an alarming  increase in heat generation.

BEWARE: there is information on various parts of the 'net that  lifespan of the Macbook can be reduced, perhaps dangerously so, (Google: Macbook Vcore linux) so i run Lunix in a VM
for a £700 laptop i'm not going to take the chance. 
Especially worrying is the state of power-saving / heat-generation in some laptops, i have been researching and compiling and tweaking for several years on this very subject. and i thing there is some way to go yet, in this area.

My 2 year old Packard Bell laptop (AMD Turion 64x2 CPU) overheated while installing Fedora on it a month before Xmas 2011 - taking out one of the RAM sockets.
this is not perculiar to Fedora - Slackware and many other distros are particularly bad for this, - in fact Ubuntu - or Kubuntu (my preferred DE) was the best distro in this respect in my tests over the last few years..
Good Luck.

---

