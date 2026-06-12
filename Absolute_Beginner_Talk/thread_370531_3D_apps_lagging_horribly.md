---
title: "3D apps lagging horribly?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Mochtroid-X on 2007-02-25
I've been having this problem all day and the only way to fix it is to restore my old xorg, uninstall the nvidia-glx drivers and reinstall them. For some reason, out of the blue, my 3D games (namely Nexuiz, Tremulous and Doom 3 which are completely unplayable at this point) will get horrible lag. When I got up this morning Nexuiz played fine but later today all my 3D games just lagged. I'm using a GeForce 6200 256mb AGP with Edgy if that makes any difference. Anyone have any insight for this problem?

---

### Post by nereid on 2007-02-26
Is your 3d card enabled? Just run this snippet through the terminal and if it says yes, then your card is enabled and the problem lies elsewhere.

```

glxinfo | grep direct

```

---

### Post by sultanoswing on 2007-02-26
Check the temperature of your card - the fan may have died, resulting in heat buildup.

The reason it may appear to work in reinstalling drivers is that the card has a chance to cool down in between the bouts of intense 3D work.

Just a thought because it's happened to me before!!

---

### Post by Mochtroid-X on 2007-02-26
Well I went into recovery mode and restored my old xorg conf so I could get online and see what the word was after I checked the nvidia binary howto one more time, only to find a third method of installation I hadn't noticed before- the method I used that installed my nvidia vanta card on my old 550mhz computer. After following that method everything seems fine now and I hope it stays that way since my 550 shows no signs of losing 3D rendering any time soon (and I hope this one doesn't either!) Thanks for the assistance anyhow. :)

-edit- Okay, Nexuiz still lags horribly and glxinfo | grep direct says I have direct rendering enabled...

---

### Post by Mochtroid-X on 2007-02-28
bump.. without 3D acceleration I can't play most of my favorite games and may have to resort to... Windows... :(

---

### Post by Kossu on 2007-02-28
You don't happen to be running dual monitors?

---

### Post by Mochtroid-X on 2007-02-28
No, just a single monitor running 1024x768 @ 85Hz.

---

