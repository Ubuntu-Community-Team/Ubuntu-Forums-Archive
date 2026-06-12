---
title: "No Sound"
date: 2007-03-25
forum: Apple Intel Users
---

### Post by Wee_Guy on 2007-03-25
I booted my iMac from a Ubuntu Live CD and everything appeared to work fine, but i didn't get any sound:(. There were no headphones connected so sound *should *have come out of the internal speakers:confused:, and when i booted back into Mac OS X i got sound so i suspect that my sound card isn't compatible](*,).

My system is a Intel Core Duo iMac.

---

### Post by the.dark.lord on 2007-03-25
> **Wee_Guy said:**
> I booted my iMac from a Ubuntu Live CD and everything appeared to work fine, but i didn't get any sound:(. There were no headphones connected so sound *should *have come out of the internal speakers:confused:, and when i booted back into Mac OS X i got sound so i suspect that my sound card isn't compatible](*,).

My system is a Intel Core Duo iMac.

You're not alone. I have the same problem with my iMac.

---

### Post by cyberdork33 on 2007-03-25
1. Right Click on speaker icon on panel
2. Click "Open Volume Control" in the resulting menu
3. Select the "Switches" tab
4. Make sure "Line In as Output" is checked.
5. Enjoy sound.

---

### Post by pikz on 2007-03-27
This didn't work for me when I tried it on my iMac Core Duo.

---

### Post by cyberdork33 on 2007-03-27
It also defaults to an odd sound channel. I had to adjust the correct Slider to get sound working... (Once you figure out which one it is you can make it the default for volume control in the properties) I think it is the "Front" Channel, and Ubuntu defaults to adjusting the "PCM" channel

If you can't find anything in the volume properties, then try running

```
alsamixer
```

and make sure that no channels are muted ("m" mutes / unmutes)

---

### Post by pikz on 2007-03-28
Thanks. It's working now. Most channels were muted.

---

### Post by Wee_Guy on 2007-03-30
I got it working now, thanks.

---

### Post by Gen2ly on 2007-03-30
mark as solved, please

---

### Post by Wee_Guy on 2007-03-31
How do i do that?

---

