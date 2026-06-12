---
title: "Getting My Intel Wireless Card Working"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by vincent_m on 2007-08-27
I've got the wireless card: Intel Pro/Wireless 3945 Network adapter, and I've gotten the correct drivers as well as the mac80211 packages from there supplier sources. The problems is that I never really got the card to work and in the middle of getting the mac80211, certain pieces of hardware such as my sound and regular network card stopped working after I restarted ubuntu on my laptop. After that restart, I couldn't even establish a wired network anymore. I'm unsure whether trying to install mac80211 also tampered with my sound card, but it did notice I couldn't adjust the volume around the same time my wired connections stopped working. I did some searches on this site to see if I could fix the problem without starting a new thread, but the answers I got were much more advanced than anything I've ever done. I'm still very much a beginner at the whole Linux OS (64 bit), and the computer it's on is dual booting Ubuntu 7 64 bit and Windows Vista 64 bit. I've found that Vista can cause driver complications with other operating systems after reading through this forum, but I'm still in the dark on what to do. As of right now, I have no internet support unless I'm in Vista, which is where I'm writing this from.

---

### Post by p_quarles on 2007-08-27
The driver for that card is included in the Ubuntu restricted modules package. Downloading other drivers isn't going to do any good. Did it recognize the card when you booted with the live CD?

---

### Post by vincent_m on 2007-08-28
It did come up as a restricted driver, but I couldn't get the wireless connection to work at all. The wired connection worked until I started to build and install the mac80211, and the wireless card's driver packages. I followed the instructions, but I kept getting errors, and after I restarted my computer at one time, the wired connection ceased to work altogether.

---

### Post by p_quarles on 2007-08-28
> **vincent_m said:**
> It did come up as a restricted driver, but I couldn't get the wireless connection to work at all. The wired connection worked until I started to build and install the mac80211, and the wireless card's driver packages. I followed the instructions, but I kept getting errors, and after I restarted my computer at one time, the wired connection ceased to work altogether.
That doesn't sound like fun. I guess I'm fortunate that mine worked out of the box.

I don't know what you've tried already, but here's what I would do:
1) Consider the possibility that the installation disk didn't work correctly. If you didn't, you should verify the MD5sum of the downloaded ISO file. Then, prior to installing, run the install disk's integrity self-test.
2) This is a new installation, and it looks like trying to install drivers manually has messed things up. I would attempt to reinstall. 
3) Before actually installing, though, run a few tests in the terminal on the live disk (of course, you can skip this if the card starts magically working like it should). Specifically:
```
sudo lshw | less 
```This will print out all of the hardware recognized by the the CD. Look for the profile of the wireless card, and make a note of its logical name (probably eth0 or wlan0). Then,
```
sudo ifup wlan0
```substitute the appropriate name for the wireless card. The "ifup" command (interface up) will attempt to activate the network device. If this (fingers-crossed) brings up the wireless card, and allows you to connect to your router, then you can go ahead and install. If it doesn't, I would next test the ethernet connection again. 

Let us know what the results are. If this doesn't work, I'll try my best to think of something further to try.

---

### Post by mlentink on 2007-08-28
Stop. Rewind. Start over.
I have that exact same card in the notebook I'm typing this on (HP Compaq nx7400). The card was recognized from the start and simply enabling the restricted drivers made it work out of the box. You should not be having these problems, so I suspect you mistyped or took a wrong turn somewhere.

---

### Post by vincent_m on 2007-08-28
Yeah, it showed that my driver was a restricted driver. What it would do is find the networks, then I would enter the password to the router, and then I would get failures in connecting to the router. It would take a long time to establish a connection, then the attempt would result into failure. I know the password is right for sure.

---

### Post by p_quarles on 2007-08-28
Have you already done all the things I suggested above? If not, it's very likely that one of those things will fix the problem. Not a guarantee, but a likelihood.

---

### Post by vincent_m on 2007-08-28
I just reinstalled Ubuntu again, setup the pspsdk, and got all the other libraries setup for its use. So now, I'm back to where I was except I can get a wired internet connection again. The wireless connection still doesn't work and Ubuntu alerted me that Ubuntu is running a restricted driver (I'm guessing it's on the wireless card on some opt rom) that isn't supported. I checked the restricted driver manager, and I saw that it was in use. It can pick up networks, but it won't connect, infact, I onlly get one light on the connection icon in Ubuntu.

---

### Post by p_quarles on 2007-08-28
> **vincent_m said:**
> I just reinstalled Ubuntu again, setup the pspsdk, and got all the other libraries setup for its use. So now, I'm back to where I was except I can get a wired internet connection again. The wireless connection still doesn't work and Ubuntu alerted me that Ubuntu is running a restricted driver (I'm guessing it's on the wireless card on some opt rom) that isn't supported. I checked the restricted driver manager, and I saw that it was in use. It can pick up networks, but it won't connect, infact, I onlly get one light on the connection icon in Ubuntu.
Obviously, the wireless card is working. So (again) did you do the following?:
1) Check the MD5sum after downloading Ubuntu
2) Run the installation disk's integrity self-check.

If you don't know how to run these tests, just ask, and I or someone else will provide more detailed instructions.

---

### Post by mlentink on 2007-08-29
You probably thought of this, but have you checked the wireless network config? Trying to connect with WEP to a WPA-scrambled network will obviously not work

---

### Post by vincent_m on 2007-08-29
I've thought of it, but I don't know where the network properties are. The router I'm using is a WEP, and I try to get onto it via 128-bit passcode. The defaults probably have to change. When I do try to connect, i get no lit up buttons at all, so I guess my request to connect doesn't even reach the router.

---

