---
title: "no mouse and keyboard on CD boot"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by J Bratton on 2007-03-23
Hi- Old XP computer had a power surge which did in the motherboard. Bought new computer with Vista. Not happy with Vista's crashing, so decided to install Ubuntu. 

I've got the old XP hard drive (with XP that doesn't boot because of a different motherboard), and the new hard drive with Vista on it. I thought I'd install Ubuntu on the old hard drive. After looking at the documentation, I was confused as to whether or not I need to manually partition that hard drive. At any rate, I burned Ubuntu 6.10 onto a CD, changed the boot sequence so that it boots of of the CD drive, and booted up. It booted OK, but neither the mouse nor keyboard work. 

Two questions, then:

1)How do I get the mouse and keyboard to work?
2)Once they work, can I just select &#8220;install&#8221; and get going? Or will the fact that the hard drive I am writing to has a non-working version of XP on it mean that there will be some problem with the partitioning?
thanks!
John Bratton

---

### Post by Gilgad Drumheller on 2007-03-23
Check here for your mouse and keyboard needs: [link.]("http://ubuntuforums.org/showpost.php?p=2190577&postcount=30")
As for the hard disk problems, you'd need someone who has more experience.

---

### Post by Daveth on 2007-03-24
It might be wise to ascertain if the old hard drive survived the power surge as well, or if it has died. Did you fry the cpu etc?  Try repairing the xp install with the XP recovery disk to see. You will need to put Ubuntu into its own partition, with one for the swap file, with grub (often) sharing the boot area with xp. 

It sounds like you have installed the old hard drive into the new pc with the new hard drive. Is this right? In which case, which is the master/ primary disk- the Vista or the XP one? Whilst you can boot Ubuntu from a secondary drive (I think) it is more usual to do it from the primary. You need someone with a better head around this stuff to confirm this.

---

### Post by J Bratton on 2007-03-24
> **Daveth said:**
> It might be wise to ascertain if the old hard drive survived the power surge as well, or if it has died. Did you fry the cpu etc?  Try repairing the xp install with the XP recovery disk to see. You will need to put Ubuntu into its own partition, with one for the swap file, with grub (often) sharing the boot area with xp. 

It sounds like you have installed the old hard drive into the new pc with the new hard drive. Is this right? In which case, which is the master/ primary disk- the Vista or the XP one? Whilst you can boot Ubuntu from a secondary drive (I think) it is more usual to do it from the primary. You need someone with a better head around this stuff to confirm this.


Well, I've got an update. After some internet searching, I found out that a possible solution could be had by changing settings in the BIOS. I turned off USB legacy support, and I switched the mouse from "auto detect" to "PS2." 

The mouse and keyboard are PS2. I don't have an USB keyboards or mice to try out.

Anyway, it worked fine for a while. I installed Ubuntu on the secondary hard drive, and the installation guided me through disc partition. It installed OK. 

Next step was trying to figure out why it was not connecting to the internet. I tried to get back into the primary (Vista) hard drive, and found out that it would not boot even when I set it to boot from that drive. The vista drive only boots when I actually unplug the secondary hard drive. Anyway, I found out my computer's static IP address to set that configuration in Ubuntu. I got to get back into Ubuntu (i.e. powering down, unplugging system power, then plugging in power to the secondary hard drive, changing the boot order in the BIOs, then powering up. Guess what?!!! The mouse and keyboard are out again, even though I retained the BIOS settings that had allowed them to work in the first place. 

Man, at this point I am frustrated. I have TWO operating systems that aren't letting me do what I want to do. Vista has narcolepsy (goes to sleep and crashes and won't wake up) AND won't run my SlmServer music program, and Ubuntu isn't letting me use my mouse and keyboard AND itsn't connecting to the net. I'd just use XP on that secondary hard drive, but since that OS is keyed to expect the old (fried) motherboard, I can't boot XP on the new computer. UGGG. At any rate, the secondary hard drive seems fine and appears to have been unaffected by the power surge. 

I guess what I'll have to do at this point is to keep rebooting the system to see if somehow it decides to let the keyboard work, so I can log in. Then, once I get in, to see if I can get the internet connection set up by inputting the IP address. I'm hoping it isn't an ethernet driver problem. 
John

---

### Post by Daveth on 2007-03-25
yes, I can see your frustration. Your keyboard/mouse problem, assuming the fix suggested by Gilgad Drumheller did not work, might be more a xorg.conf setting problem rather than a BIOS one. Bear in mind that with a live cd setup, no settings are saved as it all works in ram. You can however, use live cds to edit, so they are v useful. As a short term fix can you borrow a usb mouse/keyboard from a friend- at least it would get you up and running- having neither rather limits one's options. It would be worth searching the forum for xorg.conf editing- I did a quick look for you but cannot access the place I need to check out.
How are you attempting to access the internet? With a usb modem, or a router? Latter is much easier. Sorry not to be of more use.

---

