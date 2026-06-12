---
title: "Installing XP after Ubuntu"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-11-09
I 'm currently running XP Pro and I really haven't had any issues out of it.
It's a nice OS but I think it's the end of the road for me. I've been using
Ubuntu 7.04 in Virtual Box for a few months and am very impressed with it.
I see no need to shell out for Vista when Ubuntu can fulfill most my needs
there are a few things I need to work out so this is the reasoning for my question.

I plan to Duel Boot soon but for now, I'd like to do it this way. I have another
80 Gig Drive that I would like to install Ubuntu 7.10 on.  I plan on partitioning
it like this

/ ( 15 Gigs )
Swap: ( 1 Gig )
Home: ( 24 Gigs )

I am going to leave the rest of the 40 gigs unformatted for XP later.
For now, I'm going to put the Drive in an external USB Drive
enclosure and boot it off USB. Basically I want to keep what I got
right now in case I have issues and I want to revert back to my
current XP Setup, This way my XP Drive is still intacked.
I would go ahead and install XP 1st on the other drive but this whole 
XP Activation thing will probably keep me from using my other drive
if I need to throw it back in.....

So, is it going to be a nightmare to install XP Pro later when I decide to
format the old drive and use my copy of XP on the Ubuntu Drive?

I would use Virtual Box and put XP in it but VB's are sooo slow and have
issues with USB and DVD Drive.....

---

### Post by dpar on 2007-11-09
Shouldn't be a nightmare.....you will have to reinstall grub after the XP install, because it will overwrite the MBR.

---

### Post by sc2 on 2007-11-09
> **dpar said:**
> Shouldn't be a nightmare.....you will have to reinstall grub after the XP install, because it will overwrite the MBR.



I was under the impression Windows "didn't like" being anything but the first partition. Or was that a vista-only thing? What is Grub btw? Simplified boot menu or something? :/

---

### Post by Frak on 2007-11-09
> **sc2 said:**
> I was under the impression Windows "didn't like" being anything but the first partition. Or was that a vista-only thing? What is Grub btw? Simplified boot menu or something? :/
Every so often you'll get a BlSOD (Black Screen of Death) which is where the installer fails, but it doesn't always occur.

---

### Post by kd7swh on 2007-11-09
It doesn't matter what partition windows is on, but as he said above you will need to re-install a boot loader like GRUB because your Master Boot Record will be scrapped.

---

### Post by Orbital75 on 2007-11-09
Yeah, as long as it's not a nightmare and you guys walk me through the Grub
install I think it will be end up working out.  :)

---

### Post by sc2 on 2007-11-09
> **Frak said:**
> Every so often you'll get a BlSOD (Black Screen of Death) which is where the installer fails, but it doesn't always occur.

Ah, ok.

---

