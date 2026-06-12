---
title: "Is It Possible?(Linux on OS X 1)"
date: 2008-10-19
forum: Apple Hardware Users
---

### Post by bdup12 on 2008-10-19
Hi im Brandon and 14yrs of age and am pretty good with computers but i have an outdated mac and i dont feel like buying leopard when they are gonna come out with snow leopard soon and i just recently installed HardyHeron on my desktop(i am loving it) but i want a linux operating system for it is there any possible way to install it like wubi?

---

### Post by tgalati4 on 2008-10-19
Fink Commander allows you to install a lot of Open Source software on an OS X system.  Look for an old x86 system to experiment with Ubuntu. PPC hardware support can be spotty.

---

### Post by loboc on 2008-10-20
if you want a fresh install of ubuntu only on your mac you need to determine if its a intel mac or a ppc (g4 g5 etc ) mac . 

 Installing on a mac is just like installing on a pc but you need the right install disk

---

### Post by loboc on 2008-10-20
[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

has a list of the install cds with a description

[www.apple-history.com](www.apple-history.com) will tell you the features of your mac

to get it to boot of the cd you can select the startup disk in OSX or
hold C down while its booting during the mac chime

google will tell you alot if you search for things like linux ubuntu how-to mac apple ppc etc,

---

### Post by ppc_guy on 2008-10-22
I agree with the previous post. First off you need to determine what mac you have.. A good place for that is [www.lowendmac.com](www.lowendmac.com) Click on the profiles and find what you have.. If you have a machine known as 'NewWorld' with Openfirmware it's going to be a lot easier.. However, if it's an older machine, you will need to get BootX which you can get here: [http://penguinppc.org/historical/benh/](http://penguinppc.org/historical/benh/) . This makes things a bit more tricky as you have to retain a small MacOS install to allow BootX to load and give you the option of linux. Think of it as the Grub of Mac.

As always, your mileage may vary

ppc_guy

----------------------------------------------------------------------
When you are Sierra-Oscar-Lima. I'm Hotel-Tango-Hotel
----------------------------------------------------------------------

---

### Post by mfox on 2008-10-22
> **bdup12 said:**
> ... is there any possible way to install it like wubi?
Assuming your Mac is a PowerPC (after all, that's the forum you're in), I believe the answer to your question is yes.  An old product called VirtualPC (last version made was sold by Microsoft) can be used to install Linux in emulation mode.  This would be pretty slow, but it apparently does work.  (I haven't tried it.)  If you were installing Ubuntu/any Linux on VirtualPC, you would install the x86 version, not the PPC version.

If you want to try Ubuntu (or any Linux) on a PowerPC, you might try the liveCD.  (Make sure you get the PPC version!)  If you like it and want to run Linux along with your MacOS, you are best off to run it as a dual boot.  That's what I have on my PowerBook G4.  What happens is you get a menu when you start up that offers to start in Linux or MacOS.  If you want Linux, you can still have access to the MacOS, running in emulation mode (which is fast) within Linux.  The program that does this is Mac-on-Linux (MOL).  Current versions of Ubuntu don't run this; you probably have to go back to version 7.04.  Alternatively, MOL runs in Debian Lenny and openSUSE 11, both of which sport good PPC versions.

---

### Post by omoikane on 2008-10-22
.

---

