---
title: "Experiences with 7.10rc on intel macs: mac pro/macbook pro"
date: 2007-10-15
forum: Apple Intel Users
---

### Post by jamieno10 on 2007-10-15
I would just like to know people's experiences on 7.10rc for mac pro (desktop & laptops) in general. Might also be useful for an overview of what features work and don't work (hopefully some fixes =) )

Has it been stable? Do the keyboard work? Sound?

For me, in the short time that I've been using ubuntu on my mac pro (Geforce 7300 GT, duo quad core): 

1. My pioneer DVD drive boots up LIveCD fine (received my mac pro oct 1st; there has been firmware/driver update for the DVD-rom it seems)

2. I can only open the dvd drive and not close it from the keyboard.

3.  I have no sound, speakers or headphones
  
4. Using Gparted to partition my 2 other Hard-disk results in ubuntu not being able to load upon reboot. Seems that workaround is to re-install GRUB after partitioning (haven't tried that)

---

### Post by quannum on 2007-10-16
I have a MacBook Pro last gen with 11n wireless and ATI graphics.

I've been running it full time for the past couple of days with no issues whatsoever, sound works, but not through the internal speaker, only headphones. I don't really need my speakers so I've not investigated this too much.

No issues with the keyboard or trackpad, but I had to reconfigure via xorg.conf to get OSX style two-finger scrolling,

I have a slot drive, so I can't comment on the DVD issues, but I was very happy to discover that the eject hotkey works!

---

### Post by wdo_will on 2007-10-16
No problems here, except the touchpad is ultra-sensitive no matter what I do to the settings.

---

### Post by russo.mic on 2007-10-16
Just installed Gusty on my Macbook Pro, everything works great so far, except for sound.  

Russo

---

### Post by neowip on 2007-10-16
I have a Macbook pro 15inch (2.33Ghz versio) and an Airport Extreme Basestation, but I cannnot create a wireless connection to the router. In fact, it won't even see the wireless.

---

### Post by russo.mic on 2007-10-16
neowip:

I have the same computer and the latest madwifi worked without a hitch for me.
 
Just a tip!

---

### Post by neatokino on 2007-10-17
I've got a newer model Santa Rosa Macbook Pro... tried running 64 bit and couldn't get the screen resolution right and couldn't get any sound.  Loaded i386 and things are, well... pretty good.  

Sound works.  Screen looks great.  Loaded Emerald and Compiz Gnome manager and got some cool compiz effects happening.  wifi worked after downloading madwifi drivers.  Flash loaded and works.

Runs very hot, much hotter than with OSX.  That scares me a bit.

trackpad is twitchy, doesn't right click with two-finger tap.  I've played with xorg.conf and put in synaptic trackpad settings the same way I had in Feisty, and nothing seems to affect the trackpad whatsoever.  I can only really work this with an external mouse.  When I type, the cursor flies all over the page, even after running syndeamon -d -t.

I was going to run Ubuntu regularly on the MBP if power management and trackpad issues were fixed in Gutsy, but so far that doesn't seem to have happened.  :(

Haven't tried suspend yet, but I will after posting this.

---

### Post by kaiguy57 on 2007-10-24
try some of the fixes here:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

they worked wonders for me! also, to get all of the ATI graphics capabilities, visit here:

[http://www.simplifiedcomplexity.com/blog/mgalvin/ubuntu-gutsy-macbook-pro-ati-fglrx-compiz-fusion-working-you-ask-yes](http://www.simplifiedcomplexity.com/blog/mgalvin/ubuntu-gutsy-macbook-pro-ati-fglrx-compiz-fusion-working-you-ask-yes)

---

### Post by mcdull2k on 2007-10-24
for sound issue you can try alsamixer from terminal and unmute all channel.

---

