---
title: "asoundconf list showing no sound devices"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by damphoux on 2007-12-06
Installing 7.10 on a Dell Optiplex GX1 (one of those older serviceable units).  

The sound card is built into the motherboard and has standard speaker/mic jacks.  It was working when XP was installed.

When I do: 

     ```
sudo asoundconf list
```

There are no devices listed.

Wondering if there is a hardware setup somewhere not detecting the sound card.  Any thoughts?

Mike

---

### Post by ajmorris on 2007-12-06
does running sudo alsaconf detect any cards?

---

### Post by damphoux on 2007-12-06
No. Nothing listed.

I went to the BIOS configuration and the on board sound card (chipset) is set to ON, and it says it is Creative Labs Sound Blaster Live! 512V.

Still unable to recognize it after reboot.  Still searching for answers.....thx

---

### Post by redpawn on 2007-12-16
I too have a GX1 now working with sound thanks to the post near the end of this thread.
[http://ubuntuforums.org/showthread.php?t=305269](http://ubuntuforums.org/showthread.php?t=305269)
Without the module load the Kernel can't work with the sound card.

---

