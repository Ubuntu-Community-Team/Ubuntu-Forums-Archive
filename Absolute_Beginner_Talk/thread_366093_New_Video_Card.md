---
title: "New Video Card"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Patent_Lawyer_Toronto on 2007-02-20
I installed Ubuntu 6.10 a week ago (Xubuntu) on an old P3 733 with 256MB and on board video (only 4mb), and have been enjoying it; however, the video is too slow to display flash intensive web sites comfortably.  The mother board has no AGP slot (just on board intel AGP nothbridge - 810 chipset), but I had a spare PCI slot.  I purchased an inexpensive PCI video Card and installed it then restarted my computer leaving the monitor plugged into the motherboard video.  Xubuntu seems to see the card and identifies it as "**nVidia Geforce4 MX420**" (I guess that's right, I don't actually know what the card is b/c I got no documentation with the card). 

I set my bios to use PCI graphics on boot up, plugged in my monitor into the new video card, then tried to re-install Ubuntu in the hopes that it would auto-detect my video card.  Ubuntu seems to go through the steps of installing from the boot CD (I see the Ubuntu screen that asks me if I want to install - I choose yes), then, after a while, the screen goes dark and stays that way.  Obviously, Ubuntu does not know what to do with the video card.

**Question** - How do I get Ubuntu (Xubuntu) to see this card and work with it?  I reloaded Ubuntu using the on-board video (its all I can do for now).  Any help would be appreciated.

---

### Post by overdrank on 2007-02-20
Hi I am new to Ubuntu, but one thing you might check ( that has happend to me in the past) in you bios on the Motherboard you may have to disable the onboard video for it to detect the pci video card. Hope that helps.

---

### Post by Patent_Lawyer_Toronto on 2007-02-20
Thanks for the reply.  Actually, I disable the AGP video in my bios, and set it for PCI video - i.e. it boots up using the PCI video card.  The PCI video card works, b/c I see the Ubuntu boot up screen (from the CD boot up), it just seems to blank out after that.

---

### Post by ed-j on 2007-02-20
> **Patent_Lawyer_Toronto said:**
> Thanks for the reply.  Actually, I disable the AGP video in my bios, and set it for PCI video - i.e. it boots up using the PCI video card.  The PCI video card works, b/c I see the Ubuntu boot up screen (from the CD boot up), it just seems to blank out after that.

Very recently, this kind of black(ish) type screen has indicated to me that the xserver resolution was set too high for the graphics card to handle. What kind of monitor/screen are you using?

---

### Post by Patent_Lawyer_Toronto on 2007-02-20
Thanks for the post.  I am using a fairly high resolution 19 inch LCD monitor.  I don't know what its top resolution is - but right now I'm using 1280 by 1024, which is fairly high resolution (perhaps not quite the highest).  I think that I am doing something basic wrong, like not having the right driver installed or something.  The only way I get it to work is to use the on-board video - which is a lower class video graphic chipset from Intel.

I'm truly stuck.  I have no idea about the basics in setting up the video card in Ubuntu since all my experience to date has been with windows os (and I'm trying to find a good alternative to it).

---

### Post by Patent_Lawyer_Toronto on 2007-02-20
Thank you ed-j.  I have a stupid question.  What is xserver?

---

### Post by ed-j on 2007-02-20
> **Patent_Lawyer_Toronto said:**
> Thank you ed-j.  I have a stupid question.  What is xserver?

Apologies, I was off loading a new desktop which I am now using? Apparently.

I am a Novice myself, however, the xserver appears to be one ( there may be others) solid way of achieving the correct resolution for your graphics card and monitor.

If you use a Terminal window, you can type in "Commands" and I do know the one for the xserver is    [COLOR="DarkOrange"]sudo dpkg-reconfigure xserver-xorg[/COLOR]    This will lead you to an old fashioned GUI, from there you can specify which graphics card or device you would like to use and also set the resolution for your monitor.

1280x1024 sounds right for an LCD or TFT 19". The refresh rate should be around 60Hz with no percievable flicker. If you try and run your kind of monitor on anything other than the "native"( in other words, the only ) res' that it is programmed to cope with, you will get the black screen.

If you do get the black screen and have no GUI, press"esc" when the Grub is loading (it will say this on your screen in B+W) it will take you to recovery mode with the same xserver GUI as the above command. I would reccommend leaving the res' at 1280x1024. Hope you can get around this. Post if you still have problems!

---

### Post by ed-j on 2007-02-20
I failed to notice your graphics card name: There are 2 lots of Binary Drivers for Nvidia in Edgy 6.1. "Modern" and "Legacy". You will find them in Add/Remove in Accessories. I think the GeForce 4 would come under "legacy?" You will need to try either one of these and then set the xserver. I hope I'm not being too confusing. Good luck!

---

