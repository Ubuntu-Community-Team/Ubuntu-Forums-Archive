---
title: "How good is Ubuntu's usb jumpdrive support?"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-07-13
Lets say its a random jump drive that should work plug'n'play with XP. What are the chances it would auto mount and work just fine in Ubuntu, showing up on the desktop and what not w/o user intervention?

---

### Post by wildseven on 2007-07-13
Mine seem to work when I just put it in the USB.

---

### Post by overdrank on 2007-07-13
> **FleetAdmiral74 said:**
> Lets say its a random jump drive that should work plug'n'play with XP. What are the chances it would auto mount and work just fine in Ubuntu, showing up on the desktop and what not w/o user intervention?

HI so far I have three and all three work right off the bat. SanDisk 512mb, Streamline 128mb, Memorex travel drive 1gb. :guitar:

---

### Post by Super TWiT on 2007-07-13
The chances of it working are very high.  The only USB device that hasn't worked for me is my USB MP3 player, but all of my USB storage devices have worked.

---

### Post by wildseven on 2007-07-13
Even if they don't work, a small bash script can simplify things.

---

### Post by insane_alien on 2007-07-13
haven't came across a USB device that hasn't worked out of the box yet(on feisty at least).

chances are good and getting better by the day.

---

### Post by FleetAdmiral74 on 2007-07-13
> **Super TWiT said:**
> The chances of it working are very high.  The only USB device that hasn't worked for me is my USB MP3 player, but all of my USB storage devices have worked.

hey, same with me! The player *should* be plug and play, never needed software for XP, and is used like a disk drive. But I swear, that thing has NEVER worked w/ Ubuntu. 

ps: if anyone thinks they can help with the player, do a quick search for my previous topics, I have a few w/ info  :) thanks

---

### Post by Super TWiT on 2007-07-13
> **FleetAdmiral74 said:**
> hey, same with me! The player *should* be plug and play, never needed software for XP, and is used like a disk drive. But I swear, that thing has NEVER worked w/ Ubuntu. 

ps: if anyone thinks they can help with the player, do a quick search for my previous topics, I have a few w/ info  :) thanks

It might be what is called an MTP device.  MTP devices in Windows show up exactly like a usb device.  Try installing libmtp5:
 ```
sudo apt-get install libmtp5
```
then after you plug in the device type,
```
mtp-detect
```
However, in my case it said "no MTP devices detected"  Another thing you could do is try installing new firmware for the device.

---

