---
title: "i915 desktop issues - 915resolution/xorg not fixing it"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by Reishka on 2006-12-12
Okay, so I'm pretty happy with Ubuntu. I'm just having a small issue with graphics. Whenever I try to change my resolution, instead of fitting within my screen, my desktop runs off the side. 

I'm running the intel 915GM chipset on a Gateway MX6650 laptop (15.4" Ultrabright TFT WXGA widescreen). Also, I'm running 6.06 - Dapper Drake. 

Currently, the only resolution that works correctly is 1024x768 @ 60 Hz. From using the 915resolution package I was able to make 1280x800 appear (My laptop's max resolution) in system > prefrences > screen resolution, but when I select it my desktop becomes larger than my screen and runs off to the right and to the bottom. I'm able to navagate these parts of the desktop by pushing my mouse to the right or the bottom, but it is *really* inconvenient. So, I have the option available, but it doesn't seem to want to work correctly.

I've also tried using 

```
sudo dpkg-reconfigure xserver-xorg
```

in all three modes in regards to moniter settings (Simple, ?? (I forget the name), and Advanced) to try and fix this, as well as to add a higher refresh rate -- which failed on both counts. 

If anyone can point me in any sort of direction or offer up something else that I could try, I'd really appreciate it.

---

### Post by Reishka on 2006-12-17
4th day bump.

---

### Post by Westies on 2006-12-17
I noticed the same thing on my fathers dell at 1280x1024. I noticed that if I lowered the refresh rate from 85hz to 60hz it would properly display at the higher resolution. Perhaps the monitor can't display the resolution you chose at the currently set refresh rate? Just a guess.

---

### Post by Reishka on 2006-12-17
I'm already sitting at 60 Hz, and even though I've tried different configurations I've never been able to get ubuntu to recognize anything other than 60 Hz. If I remember correctly, 60 Hz was the only thing that my Windows install used to recognize, as well. BUT I was also able to use resolutions other than 1024x768 correctly.. 

While worth a shot to try, at this point I'm not even sure my LCD can even recognize something other than 60 Hz. Signs are mostly pointing to no. :(

---

### Post by Westies on 2006-12-17
Try the section under Undected Monitor Specs
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
Perhaps you need the correct HorizSync and VertRefresh values in the X config. Again, just guessing here. I'm new to Ubuntu myself and had to fight with it to recognise other resolutions as well.

---

### Post by Reishka on 2006-12-17
Thanks for pointing me in that direction -- unfortunatly, none of it worked. The only discovery that I made was from using 

```
sudo ddcprobe | grep monitorrange
```

Apparently, my LCD only supports (48 - 50, 59-61) for sync and refresh... which are already well contained in my configuration...

---

### Post by Reishka on 2006-12-27
Okay, I've made SOME headway.... 

I updated to Edgy.

Using the i810 drivers, I can't get the resolution I want. It just doesn't happen. But if I put my display in the resolution I want (In this case 1280X800) and then switch to using VESA drivers, and restart X --- the display renders correctly. 

BUT.

If I go to restart my machine using the VESA drivers, I can't. I get stuck in a perpetual loop at login. I enter my name/pass, it glitches for a moment, and then I get to enter it all over again, never getting any further. So then I have to switch back to the i810 drivers... losing my resolution. 

Anyone got a clue as to what's going on?

---

