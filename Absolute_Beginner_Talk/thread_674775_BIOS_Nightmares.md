---
title: "BIOS Nightmares"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Semong on 2008-01-22
Pinch me and wake me up someone please. Long story short an Nvidia GeFORCE FX 5200 was plugged into my computer to "test if it was defective".Now I try using my old ATI RADEON graphics card and I get nothing but a black screen throughout boot-up. There are no video configuration options in my BIOS to tell my motherboard which graphics card to use (apparently it's supposed to auto-detect it) and I have no idea what on earth I could possibly do to solve this problem. Right now I have the the NVIDIA card in a PCI slot and my RADEON card t=in the graphics card slot. I type 'lspci -v' into the terminal and it reads the Nvidia card however the Radeon card is nowhere to be found. Any and all suggestions would be a life saver. Thanks.

---

### Post by zabien1970 on 2008-01-22
Did you make sure your original card was properly seated (wiggle it) or the connections weren't dirty?, I would take out both cards and start the computer so bios registers nothing and maybe resets, then reinsert the original card making sure the contacts are clean and its seated properly

---

### Post by Rhubarb on 2008-01-22
Boot off the ubuntu live cd to see if it boots up properly (to check if it's a hardware or a software problem).

There's a chance that your xorg.conf needs to be fixed up, run:
```
sudo dpkg-reconfigure xserver-xorg
```
in a terminal and follow the prompts.

---

### Post by Semong on 2008-01-22
> Did you make sure your original card was properly seated (wiggle it) or the connections weren't dirty?, I would take out both cards and start the computer so bios registers nothing and maybe resets, then reinsert the original card making sure the contacts are clean and its seated properly

Ok I just tried all of these things and it still doesn't work. Is it possible to update my motherboard or my BIOS perhaps? I think I remember reading somewhere that it's possible to do this but have no clue how to go about it with xubuntu.


There's a chance that your xorg.conf needs to be fixed up, run:
Code:

```
sudo dpkg-reconfigure xserver-xorg
```

I wish that this was my problem however it isn't. My card isn't detected in the terminal nor in my BIOS. The problem is much deeper than xorg but thanks for trying to help.

---

### Post by stalkingwolf on 2008-01-22
try removing the Nvida card.  I read some place ( and I am suffering from cranial flatulation at present)
that you need to change a setting on the board ( a dipp switch or jumper) or having two vid out puts
will confuse the system.

---

### Post by Golem XIV on 2008-01-22
There should be an option in the BIOS that says "Init Video" or similar.  By default this is set to PCI first, AGP second.  From your post, the nVidia is in the PCI slot so it gets first choice.  Try changing this setting to "AGP first".

Otherwise, as they said, remove the nVidia card  - use only one card at a time.

---

### Post by Semong on 2008-01-22
As I said in my initial post, there are no video configuration options in my BIOS. There is no way for me to switch it back to AGP. And beleive me I've tried removing the NVIDIA card . My monitor doesn't get any picture unless its hooked up to that card. I tried unplugging both cards and starting my computer to reset the BIOS then plugging my RADEON card back in but I get nothing but a black screen. Im still lost on how to go about fixing this.

---

### Post by Rhubarb on 2008-01-23
It doesn't sound too good there at all.
You could try resetting the CMOS memory (some people call it the BIOS), there should be 2 pins you can short with a jumper for a few seconds, or remove the battery for a few minutes.
Consult your motherboard manual about how to do this.

Do you see anything coming up on the screen at all?  Like any POST data when you boot up (before grub kicks in)?

---

### Post by Semong on 2008-01-29
No I don't see anything but a black screen. I removed the battery from my motherboard one night and left it out for about 4 hours. That didn't work either. I don't have the motherboard manual because this computer was a gift. It may be possible to find the manual online so I guess I'll have to try.

---

