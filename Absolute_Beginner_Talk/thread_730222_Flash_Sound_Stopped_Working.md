---
title: "Flash Sound Stopped Working"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by dethredic on 2008-03-20
Flash has never given me any trouble, until now. It has been working flawlessly for like 5 months.

All of a sudden yesterday, my sound stopped working. It worked a couple hours before.

Anyone have thins problem or know of the fix?

---

### Post by dethredic on 2008-03-21
anyone?

---

### Post by dethredic on 2008-03-21
someone?

---

### Post by Redptc on 2008-03-21
Is this a general sound problem or is this specific to Flash?

My personal sound problem relates to 'no sound at boot-up' but I can initiate sound by adjusting the Master control. What this means is that I regularily 'fiddle' with various adjustments that cause the sound, especially in Flash to disappear. I then have to undo the adjustments to restore my sound.

Perhaps you can tell us more but may I suggest you examine the 'Master' control and move the button away from, and then, back to the full position. If still no sound, right click to **Open Master Control** and do the same with the Master and PCM controls.

---

### Post by maddog39 on 2008-03-21
Well if this is specific to flash, then its probably another application such as rhythmbox or banshee taking over the sound device. Because as far as I know, flash still uses OSS which will stop working sometime despite other applications using ALSA.I have this problem generally with skype and flash, where either one cancels out the other.

---

### Post by dethredic on 2008-03-21
Yes it is specific to Flash. All my other applications emit sound. I tried just launching FF, and going to youtube, and still no sound. I had not opened anything else. It happens all the time, not just occasionally.

---

### Post by AmyRose on 2008-03-22
> **maddog39 said:**
> Well if this is specific to flash, then its probably another application such as rhythmbox or banshee taking over the sound device. Because as far as I know, flash still uses OSS which will stop working sometime despite other applications using ALSA.I have this problem generally with skype and flash, where either one cancels out the other.
Actually Flash 9 uses ALSA. 4front's OSS drivers require a compatibility layer or Flash doesn't produce any sound. (I know this because I am starting to prefer these drivers over ALSA (long story).

I am not sure why this problem would be Flash-specific though.

---

### Post by dethredic on 2008-03-22
I still can't get this, any other ideas?

---

### Post by dethredic on 2008-03-22
anyone?

---

