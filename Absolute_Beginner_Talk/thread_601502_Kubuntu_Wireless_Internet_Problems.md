---
title: "Kubuntu Wireless Internet Problems"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by matty14 on 2007-11-03
Hi, i have just set up a dual boot with kubuntu and windows xp, although i want to completly get rid of windows,i cant as i am completly unable to connect to the internet, i am using a Belkin Wireless G USB Adapter F5D7050.

What happens is when i get onto kubuntu i right click the KNetworkManager icon and the connect to my internet connection [WireFal1963] although when i get to 57% and changes to say "Activation Stage: IP Configuration Started" Kubuntu Completly Freezes and i eventually have to turn off my computer by using the switch.

Can Anyone Please Help Me By Telling Me How To Get My Wireless Internet Working?

BTW: The Wireless Adapter connects to the internet on windows with no trouble.

---

### Post by jdg.gehrig on 2007-11-03
Is the card Linux supported and if so is the beklin driver installed?

if not did you use ndiswrapper to configure the NIC?

or have you just used the drivers that come with kubuntu?

---

### Post by matty14 on 2007-11-03
> **jdg.gehrig said:**
> Is the card Linux supported and if so is the beklin driver installed?

if not did you use ndiswrapper to configure the NIC?

or have you just used the drivers that come with kubuntu?

i have just used the drivers that come with kubuntu

---

### Post by jwal82 on 2008-04-04
I am having the same problem:mad:
I haven't done anything but installed Kubuntu. As far as I know I haven't installed any drivers?
Help!!!!

---

### Post by anewguy on 2008-04-05
That's the same USB wireless adapter I use.  While it wants to work somewhat by a default driver, I had to install the Windows XP driver using ndiswrapper and then I have had no problems.  Remember you also need to set the encryption, if any, to the correct type and specify the correct password (done when you try to connect via network manager).

There are many, many posts here for using ndiswrapper.  If either of you need help, just post back and we will help you.

I will probably be off for a while as I have a hardware update to do to my PC and then I need to completely reinstall 7.10 from scratch again, but I now someone else can help you if I'm not here.  :)

---

