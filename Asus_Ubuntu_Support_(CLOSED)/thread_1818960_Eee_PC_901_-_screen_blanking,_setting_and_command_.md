---
title: "Eee PC 901 - screen blanking, setting and command line having no effect"
date: 2011-08-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by SolipsistWriter on 2011-08-05
So I just got an Eee PC 901 off eBay and all seems fine so far. I installed 11.04, putting the root of the OS on the 4GB SSD and the home on the main 8GB SSD.  Anyway, it all seems to running fine and surprisingly fast, but I do have one small issue: Despite the fact I have changed the power saving settings so that the screen should never turn off while on battery or AC power, it keeps doing so anyway, usually after a minute but sometimes after just a few seconds, of inactivity.

Other than the settings change, I've also tried typing "x set noblank" into the Terminal as suggested by a Google search, but I had no luck with that either.

I highly doubt it's a BIOS level issue as, when the netbook came with XP and I left it sitting there idle for about 30 minutes while I set up the Ubuntu USB stick, the screen didn't even so much as dim, let alone go blank, so I'm quite certain it's an Ubuntu issue. 

Any tips on how to sort this would be very helpful. It's not a major problem, obviously, but it is very annoying, especially when I'm trying to stream videos.

Thanks :)

---

### Post by SolipsistWriter on 2011-08-05
Two further observations: when on the login screen, the screen does not dim, and just now I woke it up from sleep mode and the screen dimmed right down so I couldn't see anything; I had to manually adjust the brightness using keyboard hotkeys.

---

### Post by Plumtreed on 2011-08-05
I have a 701 but the arrangement is similar. I have my OS running on the internal 'drive' with the /home to the external or removable SSD.

...perhaps I have misunderstood????

---

### Post by wojox on 2011-08-05
Does it dim or completly blank?

Look in 

```
/etc/laptop-mode/conf.d/lcd-brightness.conf
```

for configuring it. That where my Asus 900 eeepc is.

---

### Post by SolipsistWriter on 2011-08-06
wojox, you were right, it kept dimming right down so the backlight turned off completely. Turned off screen dimming and it fixed it right away :)

---

### Post by clegends on 2011-08-08
That's great news! Can you please mark this thread as 'solved'? Cheers.

---

