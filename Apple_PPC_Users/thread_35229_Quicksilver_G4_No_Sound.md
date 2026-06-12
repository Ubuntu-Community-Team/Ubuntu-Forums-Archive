---
title: "Quicksilver G4: No Sound"
date: 2005-05-18
forum: Apple PPC Users
---

### Post by ipixel on 2005-05-18
I just installed Kubuntu on the second HD of my PowerMac G4 'Quicksiver' (dual processor 1.25Ghz G4, 1Gb RAM, Kubuntu HD = 160Gb).

Sound does not work at all...

I'm a newbie, so *any* suggestions at all would be much appreciated!

---

### Post by ipixel on 2005-05-18
UPDATE:

Even if I start off the Kubuntu Live CD, the sound does not work.

Does that mean that sound is not supported on my system? I thought that sound was supported on all Mac systems, bar the very latest ones, like the Mac-Mini...

---

### Post by Len on 2005-05-20
I have a later revision, the Mirrored Drive Doors mac, and there sound is distorted. It doesn't detect my speakers are plugged in as well, so I assume Mac sound support is very limited at those machines...

Did you look at the alsa settings? Did you open alsamixer (can be done from command line and GUI, in the GUI it might be called just "Mixer") to see if something is turned off?

---

### Post by ipixel on 2005-05-21
Len, thanks for the suggestions! - and yes, you are right, it *is* a mirrored-doors model.

I launched 'Mixer', and it *looks* as if everything was turned on - but no sound... Every now and then, and I click somewhere where I'd normally get a system beep, I actually get a very faint scratchy noise coming out of the Apple speakers, but that's all...

Booting from the Live CD is the same...

This is very disappointing...

---

### Post by Len on 2005-05-21
You then have exactly the same problem... Fiddling with the sound settings got my a higher volume, but still distorted... Disappointing indeed, since even as I do not use Ubuntu as a desktop, I always listen music if I'm working on some 'command line' stuff if you know what I mean. 
Oh well, my external speakers work perfectly on my MP3 player and other mac as well, but yes, it is a bit disappointing.
Keep up with the kernel updates, probably ALSA supports our machine in the near future.

---

### Post by ipixel on 2005-05-22
Someone should report this properly as a bug!

---

