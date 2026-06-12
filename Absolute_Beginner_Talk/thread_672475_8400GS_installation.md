---
title: "8400GS installation"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by md389 on 2008-01-19
Hey Guys, 
       I posted about this earlier, but I didn't get any solutions that worked even though a couple of people tried really hard to help me out (thank you guys!). However my problem remains: after having put my new 8400GS into the pci-e slot, switching the primary video adapter to pci-e in the BIOS, and plugging the monitor cable into the card, I get NO SIGNAL. If I switch the monitor cable back to the mobo, everything functions properly. Ive installed ENVY, but it says that it can detect no NVIDIA card. Trying to install NVIDIA BETA drivers is also a failing venture. Typing ```
lspci  | grep -i nvidia
``` doesn't print out a line of code. ```
sudo dpkg-reconfigure xserver-xorg
``` doesn't even show me the screens where I would get to choose to autodetect or manually configure my gfx hardware (just starts me off at the frame buffer interface or whatever). I am running an Intel Core-D 3.2 GHz machine with a gig of ram with Gutsy and distro 8.04, and Im starting to think that the pci-e slot on my mobo is fried. Say it ain't so. Help me ubuntuforums, you are my only hope. 

Mainak DasGupta

---

### Post by jeffus_il on 2008-01-19
Have you installed the restricted-drivers package?

---

### Post by md389 on 2008-01-19
I tried doing that, but when I click on the Restricted Drives Manager, a prompt shows up telling me that my hardware does not need any restricted drivers.

---

### Post by Ub1476 on 2008-01-19
It's supposed to be:

```
lspci | grep VGA
```

Anyway, did you install try the manual way?

```
envy -t
```

---

### Post by jeffus_il on 2008-01-19
Is it possible to disable the motherboard graphics adapter in bios , not to just make it secondary?

Also try a ```
lspci | less
``` to view all the entries, you might just pick up something.

---

### Post by md389 on 2008-01-19
Well I guess firstly, I don't know how to do that. And secondly, I would be a little bit reluctant to do that considering the on-board gfx is the only reason I can do anything at all on my comp right now. I don't know. What do you think?

---

### Post by jeffus_il on 2008-01-19
I think you could reverse it in bios, does your bios setup appear on the new adapter???

---

### Post by md389 on 2008-01-19
nope =[

I'm in a real pickle aren't I?

thanks for the help so far man, but keep em coming if you can.

---

### Post by ryanVickers on 2008-01-19
is the card good?  may sound silly but if nothing will detect it perhaps there is something wrong with it... It *could* still function enough to be detected by the bios but yet not work at all...

---

### Post by jeffus_il on 2008-01-19
You want bios to pick it up first before you can expect the OS to, Is the card seated well in its slot?

---

### Post by md389 on 2008-01-19
Well I mean its brand new (just arrived yesterday). Also, the fan is definitely spinning. I don't think the card is DOA. I never thought I would say this, but this was so much easier on windows =[

---

### Post by ryanVickers on 2008-01-19
never thought of this, but does it need more power?

Some cards need extra power from one of those 4 pin cables, in addition to what they get from the PCIe slot...
You'll know for sure if your does or not because it will have a obvious extra place for one of those cables ;)

---

### Post by md389 on 2008-01-19
well it seems like its seated fairly well. I can try to manhandle it a little bit more, but I dont want to break the thing. How do I know the BIOS is detecting my card?

---

### Post by jeffus_il on 2008-01-19
If you boot into the bios setup, it should display on the monitor connected to your new card.

---

### Post by md389 on 2008-01-19
Im gonna go check right now, but I believe I have a 350W power supply, so that should be good for a card like this.

---

### Post by md389 on 2008-01-19
well after having run headfirst into walls for the last 10 minutes or so I am man enough to admit on this forum that the card WAS in fact seated improperly. If anyone can figure out how to slap me over the internet, feel free to do so. 

Thanks for your patience fellas. 

You guys just made my last 27 hours (yes, 27 hours of reinstalling ubuntu, messing around with the blacklists, experimenting with distros, and switching up kernels) worthwhile. 

Thanks again!

---

### Post by ryanVickers on 2008-01-19
:lolflag: well, good to here its all working good now! :D

---

### Post by Dark Hornet on 2008-01-19
> **md389 said:**
> Im gonna go check right now, but I believe I have a 350W power supply, so that should be good for a card like this.

I am not 100% sure what the power requirements for this card are, but I know that in order to run my 8800GTX, and CPU, etc...I need a 700+ watt power supply....350 may be on the lower end, depending on what other power requirements you have.

---

### Post by ryanVickers on 2008-01-19
I don't know, it might be enough - 450 is apparently enough to SLI the 7600GT :D

---

