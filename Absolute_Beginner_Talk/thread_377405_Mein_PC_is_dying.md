---
title: "Mein PC is dying"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Akira_Oni on 2007-03-06
Well, I've been trying to figgure Ubuntu out for about 6 months now and still no luck. Recently I upgraded my Ubuntu software after about a month (which meant lots of updates) and I lost sound. However tonight I was installing a video card into my pc, and noticed the sound card was a bit loose... that could be my issue.

However now I'm having a problem with the video card. It's an 64mb DDR nVidia GeForce2 200 PCI video card being installed into a P3 gateway with 640mb of SD ram.

Anyway, the video card works. It shows the boot information, and even shows Ubuntu loading. However when it comes time to launch the GUI the screen just goes black. The same thing happens when I try to boot from a 6.10 install disk. I've been trying to learn Blender as a replacement for flash, so I need a video card. Anyone have a suggestion as to what I might do to make Ubuntu work with my video card?

---

### Post by Kateikyoushi on 2007-03-06
I would try to reconfigure xorg first.

```
sudo dpkg-reconfigure xserver-xorg
```

Then check what drivers is the best for that card.

For the soundcard read this guide. [LINK]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

---

### Post by Akira_Oni on 2007-03-06
I'm guessing I'll have to do this with the video card removed. will that work?

---

### Post by Kateikyoushi on 2007-03-06
No do it with this videocard, you can boot to recovery mode and then try it.

---

### Post by russell.h on 2007-03-06
Uh, I have a feeling that if you remove the video card you are going to have trouble plugging your monitor in :) 

Try pressing Control + Alt + F1 after the GUI goes all blank, and see if you can see stuff then. If you can see stuff, then type in your name where it asks for it, then your password at the prompt. Then try the above commands.

After that press Control + Alt + F7, then Control + Alt + Backspace. That should switch you back to the GUI, then restart it so the changes can take effect. No garuntees, but its worth a try.

---

### Post by Akira_Oni on 2007-03-06
Ok, so I did that. Now it's giving me a list of drivers (I guess)

sis
sisusb
tdfx
trident
tseng
vega

I have no idea where to start with this. Really, I'm a noob.

---

### Post by Akira_Oni on 2007-03-06
ok, so now I'm really lost. I've tried the driver install a few times now, and I'm really not sure how to do this. It keeps telling me I'm doing it wrong.

---

### Post by TonKi on 2007-03-06
When reconfiguring the driver select vesa, this should work on (almost) all cards.

and by the way what version are you using (dapper,edgy,feisty)?

---

### Post by Akira_Oni on 2007-03-06
First things first... I'm using Edgy.

Now that that's out the way, I've tried loading the drivers as suggested, however I keep getting the same message. "V-BIOS cannot be found". I even tried installing them in the most simplified fashion as possible. I'm lost.

---

### Post by Akira_Oni on 2007-03-06
Ok, so at the suggestion of someone at another forum, I tried booting another distro of Linux. I've found that I can boot DSLinux with no issues to the video or sound card. However I've tried both Ubuntu 6.06 and 6.10, neither will boot from disk. 

This video card: [http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=140089144928](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=140089144928)

I've done what was suggested above, but apparently I'm still doing it wrong. Any suggestions?

---

