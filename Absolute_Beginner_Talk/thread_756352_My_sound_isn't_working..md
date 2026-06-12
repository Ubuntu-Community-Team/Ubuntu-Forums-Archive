---
title: "My sound isn't working."
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by spaceship.rodeo on 2008-04-15
I just installed Gutsy on my girlfriend's computer after Windows totally annihilated it.  Everything went pretty smoothly, until I tried to play some of her music, and there's no sound.  I went to youtube, myspace music, google video, all that good stuff, and none of them worked.  I already installed the gstreamer plugins, so I know it's not that.  And I know it's not the speakers, because I plugged them into my ipod, and they worked just fine.  

Anywho, I've tried searching around for answers, but haven't really gotten the answer I'm looking for, and I'm pretty damned stumped right about now.  So any help will be greatly appreciated.

---

### Post by spiderbatdad on 2008-04-15
could you open a terminal and post the output of ```
asoundconf list
```

---

### Post by jbrown96 on 2008-04-15
what sound card do you have? type ```
lspci
``` in a terminal and find the card? Check ALSA's website to see if it's supported and post back here - I may be able to help.

Your sound may also be muted. ```
alsamixer
``` will bring up individual channel controls. Make sure that the master and pcm are unmuted and turned up. You can also mess with the others to see if it works. 

Post back if it still doesn't work.

---

### Post by spaceship.rodeo on 2008-04-15
> **spiderbatdad said:**
> could you open a terminal and post the output of ```
asoundconf list
```

```
Names of available sound cards:
SB

```

It's just an onboard sound card.  =/


edit- I opened alsamixer and started messing around, but everything seems to be at full volume.  Except for front, which is off.  Is that what the problem could be?  And if so, how do I turn it on?

---

### Post by spiderbatdad on 2008-04-15
Often this is a simple fix. Enable the linux-backports-modules-generic in synaptic package manager.
If this does not solve the problem, you will most likely need to update the ALSA drivers for your card.
Please try backports first, and reboot.

---

### Post by Inxsible on 2008-04-15
Try the alsamixer command as suggested before. Just increase the volume to max for all channels. 

I have seen that happen to a lot of people :)

---

### Post by Sidewinder1 on 2008-04-15
This 'probably' won't solve your problem but.... when I installed Gutsy I had no sound; did numerous searches on this board and Google (lots of repetition) between the two, finally got pi$$ed and moved the speaker plug from one port to the next (Soundblsater Card {about 5 yrs. old})....it's been working fine ever since... Windoze (XP) also works out of the same jack; go figure. Hope this may help but I doubt it...

---

### Post by spaceship.rodeo on 2008-04-15
Getting the linux-backports-modules-generic package worked, thanks spiderbatdad!

---

