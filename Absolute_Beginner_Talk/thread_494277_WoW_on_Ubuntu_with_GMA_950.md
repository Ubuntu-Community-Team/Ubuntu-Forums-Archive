---
title: "WoW on Ubuntu with GMA 950"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Adrenalynn on 2007-07-06
Hi,

I'm very new to Ubuntu, but have managed to install World of Warcraft using Wine. I am able to start the game, but it works very badly. I know my graphics card isn't all that, but it works like a charm on Vista, and I expected it to work on Ubuntu as well.
I have replaced the i810 driver with Intel and tweaked the WTF config according to the WoW-walkthrough on Ubuntu.com ([https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")), but still no luck- the game loads, but the frame rate sucks and I get a lot of "visual noise" when in game. Does anyone have any tips/tricks I could try?

Thanks so much!

-AdrenaLynn

---

### Post by trinaryouroboros on 2007-07-06
> **Adrenalynn said:**
> Hi,

I'm very new to Ubuntu, but have managed to install World of Warcraft using Wine. I am able to start the game, but it works very badly. I know my graphics card isn't all that, but it works like a charm on Vista, and I expected it to work on Ubuntu as well.
I have replaced the i810 driver with Intel and tweaked the WTF config according to the WoW-walkthrough on Ubuntu.com ([https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")), but still no luck- the game loads, but the frame rate sucks and I get a lot of "visual noise" when in game. Does anyone have any tips/tricks I could try?

Thanks so much!

-AdrenaLynn

One thing that helped me was:
```
sudo apt-get install alsa-oss
```

and running WoW with:
```
aoss wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe
```

As it seems, the sound causes trouble more often than not!

To get down to the root of the problem, see if you can just turn off music and sound while in-game.

If that works like a charm, start troubleshooting the sound stuff for WoW.

---

### Post by Adrenalynn on 2007-07-07
Thanks for the reply! Sadly, no luck :( It works on my hubby's PC with the exact same configurations, however, his graphics card is way better than mine. Mine also doesn't support OpenGL, I found....

---

### Post by trinaryouroboros on 2007-07-07
> **Adrenalynn said:**
> Thanks for the reply! Sadly, no luck :( It works on my hubby's PC with the exact same configurations, however, his graphics card is way better than mine. Mine also doesn't support OpenGL, I found....

Ouch, yeah that'll hurt things big time, but, you could also try to tweak some of wine's settings for directx:

```
winecfg
```

Add WoW.exe and see if you can play with the DirectX emulation, or version of windows, etc.

---

### Post by Adrenalynn on 2007-07-07
Hm, how do I "add WoW.exe?" And there's nothing in there that resembles what I want to do with directX. do I need to install directX or something first...? Thanks for the input!

---

### Post by trinaryouroboros on 2007-07-07
Sorry, not directX, Direct3D...

hit ALT-F2, type ```
winecfg
``` hit the Enter key

In the Wine configuration window, there should be a button on the Applications tab that says "Add application" - hit that and find WoW.exe - usually it's in: /home/youruser/.wine/drive_c/Program Files/World of Warcraft/

Once added, you'll see there's a Windows Version you can choose from, I recommend Windows XP, although you might want to tinker with it and try Windows 2000.

On top, there should be a "Graphics" tab, click that and the Direct3D settings should be below.

Might require a bit of tweaking here as I said.

If you don't have the Direct3D section, or windows version - it's possible Wine is outdated. Just see if you can get it from synaptic package manager if that's the case.

---

