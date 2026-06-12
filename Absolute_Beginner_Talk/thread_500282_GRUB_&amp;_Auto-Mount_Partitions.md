---
title: "GRUB &amp; Auto-Mount Partitions"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by ChaOConnor on 2007-07-13
Good morning!  Spent last night installing Fiesty, had a blast!  System did a bunch of updates, I used the Howto Forge "Perfect Desktop" how-to and everything seems to be running fine. (No sound yet, but I have a SoundBlaster card so I may have to forgo that and use the onboard sound... we'll see!)

Question:
Part of the updates put a new kernel on... went from .14 to .15 or something like that.  GRUB has both entries in the menu now.  Sound I delete the .14 entry?  How do I?
Does that mean there are .14 kernel files laying around on my hard drive that I should delete also?  I mean if I'm using .15 why do I need .14?  I guess there is always the chance I need to roll something back, but how often does that happen?

Now for the Auto-Mount question:  When I setup Ubuntu I labeled my NTFS partition as "Windows" and all was well.  One of the auto-updates was from Automatix2 and it installed "read-write NTFS", and now I have "sda2" on my desktop when I start up and A) I don't want it on my desktop, but the only option is to "unmount" it and B) how do I change the label permanently so it mounts under "Windows" as opposed to "sda2"?

Thanks for your help!  I have to say, this is the most responsive forum I have EVER seen!  I've been dabbling w/ Linux for 8 years now, always trying new distros out, etc. but I always go back to Windows for one reason or another.  With Ubuntu I feel like I can finally make the switch for good (still need that Windows partition for a bit longer to port stuff over...) but I want to dive whole-hog into this.

- Cha

---

### Post by mikewhatever on 2007-07-13
To delete the older kernel, open Synaptic and search for 'linux-image' without the quotes. Right click on the version you do not want and select 'Mark for Removal'. That should also remove the entry from grub menu. As to why you have two kernels, well, you've answered it yourself. Obviously, you do not have 14 kernels too. My kernel number, for example, is 2.6.20-16.29, the current kernel for Feisty, but that does not indicate that the number of files is 29.

To remove the icons from the Desktop, hit Alt+F2 and type gconf-editor, navigate to apps/nautilus/desktop and remove a V from 'volumes_visible. That would not unmount the partitions, but simply remove the icons. You would still be able to access them from Places in the panel menu.

---

### Post by Happy_Man on 2007-07-13
Welcome to Ubuntu, bud! 

For the kernel stuff, yeah, you will have extra entries. However, take this into account: each of those entries is only about 1 MB in size. You may have to roll back, however, in case something happens and your kernel borks. So I recommend keeping them. 

To fix your automount problem try this code in the terminal: (Applications --> Accessories --> Terminal)
```
sudo umount /dev/sda2
sudo mount /dev/sda2 /media/Windows
```

Each line above goes in separately. Have fun with Ubuntu!

---

### Post by mikewhatever on 2007-07-13
> For the kernel stuff, yeah, you will have extra entries. However, take this into account: each of those entries is only about 1 MB in size.
A kernel the size of 1 MB, are you sure? Mine is like 70 MB showing in synaptic.

---

### Post by ChaOConnor on 2007-07-13
Thanks!  Appreciate the instructions as well as the insight!

---

### Post by Happy_Man on 2007-07-13
> **mikewhatever said:**
> A kernel the size of 1 MB, are you sure? Mine is like 70 MB showing in synaptic.
Eh, I exaggerate sometimes. Sue me. :p

---

