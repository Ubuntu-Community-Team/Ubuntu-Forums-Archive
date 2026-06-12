---
title: "MacBook4,1 will not boot Linux LiveCDs"
date: 2010-05-11
forum: Apple Hardware Users
---

### Post by xxjoshxx on 2010-05-11
I've tried booting my Macbook4,1 off of LiveCDs of Ubuntu 10.04 (both 64 and 32-bit) and 32-bit ones going as far back as 6.04. I've tried a Fedora 7 LiveCD as well.

I've tried: holding C while powering on, Apple boot menu (holding option) during power on, rEFIt, Bootcamp, burning the LiveCDs from using different computers

I tested my optical drive and it is fully functional. The computer boots perfectly fine off the Snow Leopard install disc and the recovery discs that came with the computer. 

The computer seems to recognize that these are bootable discs as they show up in the Apple boot menu and rEFIt boot menu. However, once selected, I get a light grey screen and the fans start spinning full speed and the optical drive eventually comes to a halt. I left this on overnight to see if anything would happen and the computer just sat there all night running fans at full speed. 

I was thinking about doing an EFI restore but Apple hasn't made an EFI restore disc for this particular model. 

Any ideas?





Additional information: These LiveCDs boot fine on my Mac Pro and Pentium 4 PC...

---

### Post by xxjoshxx on 2010-05-17
bump

please help meee : :)

---

### Post by shiink on 2010-05-17
Have you tried shutting down the computer completely for a minute or two? I used to have this very issue with my MB 4,1. And all it took was instead of just restarting it I did a complete shutdown and let it cool off for a minute and it worked just fine. So, give that a whirl.

---

### Post by Ravernomina on 2010-05-18
> **xxjoshxx said:**
> I've tried booting my Macbook4,1 off of LiveCDs of Ubuntu 10.04 (both 64 and 32-bit) and 32-bit ones going as far back as 6.04. I've tried a Fedora 7 LiveCD as well.

I've tried: holding C while powering on, Apple boot menu (holding option) during power on, rEFIt, Bootcamp, burning the LiveCDs from using different computers

I tested my optical drive and it is fully functional. The computer boots perfectly fine off the Snow Leopard install disc and the recovery discs that came with the computer. 

The computer seems to recognize that these are bootable discs as they show up in the Apple boot menu and rEFIt boot menu. However, once selected, I get a light grey screen and the fans start spinning full speed and the optical drive eventually comes to a halt. I left this on overnight to see if anything would happen and the computer just sat there all night running fans at full speed. 

I was thinking about doing an EFI restore but Apple hasn't made an EFI restore disc for this particular model. 

Any ideas?





Additional information: These LiveCDs boot fine on my Mac Pro and Pentium 4 PC...


The San Rosseta, The CPU Has a POOP load of Trouble trying to boot from a Linux Live CD. it is really hard to get a mbp 4,1 to boot of a Linux CD. But it can be done i heard... do some looking around

---

### Post by xxjoshxx on 2010-05-18
shiink: The computer's been off for days at a time in between tries before..but i'll keep this in mind when I try again

Ravernomina: maybe i'll just try it repeatedly and completely remove the power between tries 


thanks guys, i'll let you know what happens

---

### Post by linuxopjemac on 2010-05-18
If you install ```
rEFIt
``` in OSX, you should see the CD after boot. Maybe it works then.

---

### Post by xxjoshxx on 2010-05-18
> **linuxopjemac said:**
> If you install ```
rEFIt
``` in OSX, you should see the CD after boot. Maybe it works then.

Yeah, I have rEFIt installed. It does see the CD. After I select it though, it just hangs on the screen with the penguin.

---

### Post by linuxopjemac on 2010-05-18
did you try booting the alternate cd ?

---

### Post by xxjoshxx on 2010-05-19
> **linuxopjemac said:**
> did you try booting the alternate cd ?

Yeah. I did. Same thing.

---

