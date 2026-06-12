---
title: "Ok what's going on?"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Mazehero55 on 2007-05-18
Alright now I'm really confused.
Before I made two threads on here  one on [my sound]("http://ubuntuforums.org/showthread.php?t=446392") not working and one on a [firefox]("http://ubuntuforums.org/showthread.php?t=446396") thing

You can read those to get caught up more. 

Well long story short there was no sounds in games at all and the system sounds wouldn't work. And on my other post ubuntuguide wasn't loading all the way. Well my system freezes so I restart it with the button. And when it starts up my computer has sound! and ubuntuguide loads fully, but my scroll wheel is messed up. I won't bother you with the scroll wheel because I ended up fixing it myself. 
The buttons assigned to forward and backward were suddenly assigned to my scroll wheel???

Well I restart my system again to make sure this is permanent and when it boots up everything is back to the way it was kinda. The sound didn't work in games but ubuntuguide now loads fully still. I just don't understand how shutting it down with the button would cause my sound to work. I mean isn't it bad for the system?

does anybody know what's going on with my sound. 
I could really use the help

thank you

---

### Post by starcraft.man on 2007-05-18
Has this been happening intermittently since you installed Ubuntu? It sounds to me like your install was corrupted/flaky, I don't really see how the sound for instance could be related to the wheel failing to work or web pages failing to load. More to the point, audio seems to be one of the things Ubuntu supports very well... so I don't see why it would work and then not work unless otherwise provoked from something you did. Have you done anything yet? If not, I'd clean it out and do a new install. Should fix it for sure methinks.

---

### Post by theicyj on 2007-05-18
Do you have multiple sound cards?  I also had some sound issues.  Mine ended up being from having two sound cards, one built into the motherboard and a soundblaster pci card.  My sound would work sometimes, and for some programs, and would not work on other occasions, it was very inconsistent. Long story short, I disabled the sound card that is built into my motherboard in the bios and everything works fine now.

---

### Post by Mazehero55 on 2007-05-18
actually yes I do have two sound cards.

One built into my motherboard and on that i installed myself.

yeah some programs do work with sound but some don't. Like my media players seem to have great working sound. but no games do.

So how would I go about disabling the one in my motherboard?

---

### Post by theicyj on 2007-05-18
You'll have to restart you computer. Enter the BIOS during the boot-up sequence (when the computer scans your memory, finds your hard drives, ect, if you own a dell, hp, or another manufactured pc there will probably be some sort of splash screen).  Depending on your BIOS version, you will need to press the "Delete" key, "Escape" key, or one of the F keys to enter the BIOS menu.  Once in the BIOS menu, look around for something like "onboard sound" or something along those lines, then disable it (you can always enable it later if need be).  Then save changes and your computer will reboot.

---

