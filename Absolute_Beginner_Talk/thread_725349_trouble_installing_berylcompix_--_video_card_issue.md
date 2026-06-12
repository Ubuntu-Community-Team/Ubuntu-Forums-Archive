---
title: "trouble installing beryl/compix -- video card issues"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by badperson on 2008-03-15
Hi,

Just installed ubuntu on my machine today. I was playing around with it on a much older machine, but now want to run it on this one, and use some of the different desktop managers like beryl or compix. 

The desktop right now doesn't look right, I first want to make sure I have the correct video driver. I got this when looking to see what my card is:

lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]

Is there a linux driver for this card? also, how do you install it? (I did a search, but will do some more)

Also, I installed ubuntu earlier today, then tried installing beryl, the machine booted up in graphics safe mode, then when I booted up again, the graphics were garbled. 

should I install compix? Is that the more recent desktop program? 
thanks,
bp

---

### Post by jan quark on 2008-03-15
if you have installed the latest version gutsy 7.10 then compiz is already preistalled

beryl is outdated

check in the restricted drivers manager if there are available drivers for your card
system > administration > restricted drivers manager

are there any?

---

### Post by badperson on 2008-03-15
yeah, there was an ATI driver in there, it's installing now...
bp

---

### Post by Bölvaður on 2008-03-15
if you cannot find it in "restricted drivers" you might try 'Envy'.
Also, download "compizconfig-settings-manager" via synaptic package manager, it should give you more control of your desktop effects

---

### Post by badperson on 2008-03-15
that seemed to work, and in System\Preferences I have an "Advanced Desktop Effects Settings" option. 

but under "Appearance", when I try to change the visual effects to "extra" or "custom" I get a "The Composite extension is not available" message. 

I thought the driver would fix that. 

The desktop overall looks much better, though. 
bp

---

