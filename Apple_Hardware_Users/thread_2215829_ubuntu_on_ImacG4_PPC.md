---
title: "ubuntu on ImacG4 PPC"
date: 2014-04-08
forum: Apple Hardware Users
---

### Post by matthew_herzberg on 2014-04-08
[ATTACH=CONFIG]251841[/ATTACH][ATTACH=CONFIG]251842[/ATTACH]
Hey guys! I'm having an issue with my old mac. I'm trying to install Ubuntu onto my Imac ive tried multiple versions and get the same result im able to boot into yaboot and I have tried all the different peramiters and it boots into a blank screen with different lines and colors I have tried resetting RAM and I still does the same thing! I have pictures below! can any of you guys help me out with this?! I have the 700MHz model with 1Gb of ram and 60GB HDD.

Thanks!

---

### Post by este.el.paz on 2014-04-08
@matthew:

What are "all of the parameters" that you have tried?  I'm also trying to get the 14.04 liveDVD to run cleanly in the GUI on my 800 iMac.  If this is your first install of ubuntu be sure that you are using a "ppc" .iso, and it might be easier to get 12.04 going right now, the last version of the LTS.  14.04 is the next LTS and is still in "testing" . . . .  Read the PPCFAQ and some of the posts here by "abtabt" and "rsavage" . . . or you can read about my personal issues with it and perhaps figure out something.  I can boot 14.04 into a low resolution GUI, more or less readable, but it isn't adjusting out of that.  I have a recently started thread on this more or less same issue . . . so far not too much data there.  Enjoy the process.

e.e.p.

---

### Post by matthew_herzberg on 2014-04-08
I am using the power pc ISO and when you hit tab in the yaboot menu it gives you multiple parameters  I have tried all of them!  and it just boots to that screen with the lines and color squares so yeah :/

---

### Post by este.el.paz on 2014-04-08
Alrighty, well it is a tad challenging to get linux running on the iMac.  Read my thread that I just posted and try the last post there . . . and also read the links in the "Testers wanted for 14.04" from rsavage to get to the PPCFAQ for Nvidia cards . . . .

e.e.p.

---

### Post by frank18 on 2014-04-08
> **matthew_herzberg said:**
> I am using the power pc ISO and when you hit tab in the yaboot menu it gives you multiple parameters  I have tried all of them!  and it just boots to that screen with the lines and color squares so yeah :/

Matthew if i were you  i'd forget Ubuntu on Mac and go for Debian Wheezy 7.1 mini Iso,i know cause i tried Ubuntu and i could never install it on my G5, so Debian wheezy has been working for a long time and it's great,only can't get flash player,i use it mostly for  surfing the web.

---

### Post by matthew_herzberg on 2014-04-08
hey tried debain too :/ got a little further though! was able to actually install it but it just rebooted and some text came up (going through the boot process) and about halfway through it did the same thing!

---

### Post by abtabt on 2014-04-09
hmm
its easy too get lost in apple world i will check later
14.04 is develop but i hop that config for the kernel is
still the same 
if soo then nvidiafb will work (but if nvidiafb is removed we have to use 12.04 on ilamp 700,800)

---

### Post by este.el.paz on 2014-04-09
> **abtabt said:**
> hmm
its easy too get lost in apple world i will check later
14.04 is develop but i hop that config for the kernel is
still the same 
if soo then nvidiafb will work (but if nvidiafb is removed we have to use 12.04 on ilamp 700,800)

@the elusive mr abtabt:

Yes, it is easy to get lost in apple world, but in reading your recent threads here in the forum, you have mentioned that "nvidiafb works best" . . . however I've tried several times to "modprobe nvidiafb" from the LiveDVD and so far it has not worked . . . e.g., "start lightdm" does not return the GUI screen.  In one case running the "video off . . . single" command did not shut off the screen, but went to single user TTY and showed an error of "cannot request PCI regions."  I tried the "rivafb" option as well.  

Now today you are suggesting that nvidiafb might not work???  I have my own thread going on this "nv/nouveau for 14.04" if you care to stop by . . . you would be the first to comment other than my own reports . . . .

e.e.p.

---

### Post by matthew_herzberg on 2014-04-09
uhh....yeah..anyways even with debian I get the same result is there anything else you guys would suggest?!

---

### Post by abtabt on 2014-04-10
download Lubuntu 12.04 

and use yaboot parameters 
like at boot

boot:live video=offb:off nouveau.modeset=0 single

and wait in the dark when the network is up and cd not spinning 
and write in dark

modprobe nvidiafb             

if no respons type it one more time (typo )

if ok 

type 

start lightdm

if you get uggle desktop the we have some to go on

try this twice if that ot working  (typo)

---

### Post by frank18 on 2014-04-10
> **matthew_herzberg said:**
> hey tried debain too :/ got a little further though! was able to actually install it but it just rebooted and some text came up (going through the boot process) and about halfway through it did the same thing!

Did you type''video offonly'' when you booted from the cd?

---

