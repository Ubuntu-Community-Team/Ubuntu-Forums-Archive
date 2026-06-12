---
title: "Installed Envy and now computer wont boot"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Laxton14 on 2007-07-22
i installed Envy... a program which installes ATI drivers and followed the directions in the program.. i restarted.. like it asked me to but now.. when the computer is starting up the tower makes a weird clicking/beeping noise... it hangs at a black screen with a flashing white cursor thing... i have no idea what to do... i dont care about any information on my hard drive.. i just want to put a fresh isntall of ubuntu on my computer.. any help is appreciated

---

### Post by pyros on 2007-07-22
> **Laxton14 said:**
> i installed Envy... a program which installes ATI drivers and followed the directions in the program.. i restarted.. like it asked me to but now.. when the computer is starting up the tower makes a weird clicking/beeping noise... it hangs at a black screen with a flashing white cursor thing... i have no idea what to do... i dont care about any information on my hard drive.. i just want to put a fresh isntall of ubuntu on my computer.. any help is appreciated

When it comes up to that black screen with the flashyness, try pressing control+alt+F2
That should get you to  a text-based login. after logging in, type 
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
it should ask you some questions about what type of card you have, and what resolution you want to run. after you are done, type  ```
sudo reboot
``` and see if that doesn't fix it.

---

### Post by swisscow on 2007-07-22
If its beeping when the computer is just starting up and before linux itself boots something has gone properly wrong. But if as you say you just want to reinstall just pop in the ubuntu livecd and hopefully that will boot ok and then you can reinstall.

---

### Post by Laxton14 on 2007-07-22
I tried the alt+ctrl+f2 thing.. it doesnt work.. and when i put the live cd in...it doesnt boot... ubuntu doesnt even boot, it goes straight from the bios screen to a black screen, i dont know what to do because i cant get the livecd to boot so i can reinstall

---

### Post by swisscow on 2007-07-22
Ok, I heard once about something similar when someone turned their computer off when the thing was in the middle of installing some software. What they did to cure the problem was to turn everything off, whip off the cover and remove the cmos battery (looks like a big watch battery) from the motherboard. Left it off for a couple of minutes then put it all back together. For some reason this cleared the problem, though the bios will need setting up again - date, time, boot order of devices. 

Give it a try

Good luck

---

### Post by pyros on 2007-07-22
> **Laxton14 said:**
> I tried the alt+ctrl+f2 thing.. it doesnt work.. and when i put the live cd in...it doesnt boot... ubuntu doesnt even boot, it goes straight from the bios screen to a black screen, i dont know what to do because i cant get the livecd to boot so i can reinstall

But you can see  the bios screen? can you get into the bios/system setup?

---

### Post by mikewhatever on 2007-07-22
> **Laxton14 said:**
> i installed Envy... a program which installes ATI drivers and followed the directions in the program.. i restarted.. like it asked me to but now.. when the computer is starting up the tower makes a weird clicking/beeping noise... it hangs at a black screen with a flashing white cursor thing... i have no idea what to do... i dont care about any information on my hard drive.. i just want to put a fresh isntall of ubuntu on my computer.. any help is appreciated

Are you asking for help reinstalling Ubuntu?

---

### Post by Laxton14 on 2007-07-23
ill try the battery thing... and yes i can get into the bios settings.. but... i dont think that it will boot from cd or anything.. i have the boot sequence right.. it just doesnt make it that far

---

### Post by pyros on 2007-07-23
> **Laxton14 said:**
> ill try the battery thing... and yes i can get into the bios settings.. but... i dont think that it will boot from cd or anything.. i have the boot sequence right.. it just doesnt make it that far

I was just going to suggest using the bios reset, as that will usually acomplish the same things that pulling the battery will without having to open the case. Do you know if envy could have tried to overwrite the video cards firmware?

---

### Post by Laxton14 on 2007-07-23
im not really sure what you mean, but it might have.. im going to put the computer back together now and try it... hopefully it works



it did.. it works now.. im reinstalling ubuntu as we speak.. thanks for the help guys...

---

### Post by pyros on 2007-07-23
> **Laxton14 said:**
> im not really sure what you mean, but it might have.. im going to put the computer back together now and try it... hopefully it works



it did.. it works now.. im reinstalling ubuntu as we speak.. thanks for the help guys...

Hoo-Rah. I was starting to worry that it had somehow hosed your video card. Unlikely, I know, but if it actually messes with the firmware, anything is possible...

---

