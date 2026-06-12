---
title: "Baffling Sound Problem"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by stuart264 on 2007-11-01
I am having major problems with the Sound cards since installing Skype for Linux at the weekend, during the setup of that I set it so I could use it with my USB Headset and since then my sound card is not putting out sound.

I have been googling various bits and I suspect its down to me having a motherboard sound card (AC97) and a Soundblaster Live card which I use. If I go into the sound options through the gnome desktop everything seems to be set to use the Soundblaster card but nothing works unless I test sound in skype.which works so I know its not a hardware problem.

I read about using the alsamixer command and tried that out, but it brings up the settings for the AC97 chipset so I suspect i have a conflict somewhere that's causing this but I haven't been using Ubuntu long enough to know what the problem is and all the other fixs I can find don't seem to apply

Any suggestions?

---

### Post by ddrichardson on 2007-11-01
You can specify which soundcard to use from the command line:```
alsamixer -c 0
```Selects the first soundcard.

---

### Post by stuart264 on 2007-11-01
Sorted, it suddenly occurred to me that Ubuntu was detecting a sound card that was allegedly turned off in the BIOS, guess what it wasn't, switched it off and now it works like a charm.

Now all I have to do is work out why my bios has reset itself to optimized defaults so I suspect replacing a BIOS battery is in my near future.

---

