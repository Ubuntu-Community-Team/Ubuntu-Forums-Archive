---
title: "[SOLVED] Kubuntu sound problems"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by jonward690 on 2007-12-08
Ok well it is kind of anoying,when I listin to music the sound does not always stay steady sometimes when I am listing it will start playing louder and then sometimes it will get quite.It is like the volume changes but I am not changing it I have seen it do it while I was just sitting there reading something.Does anyone have any ideas how to fix this.

---

### Post by jonward690 on 2007-12-08
Anyone there

---

### Post by skyjacker on 2007-12-08
> **jonward690 said:**
> Ok well it is kind of anoying,when I listin to music the sound does not always stay steady sometimes when I am listing it will start playing louder and then sometimes it will get quite.It is like the volume changes but I am not changing it I have seen it do it while I was just sitting there reading something.Does anyone have any ideas how to fix this. My sound got lower sometimes and I solved it by doing this:

In the file /etc/modprobe.d/alsa-base

Add this line at the end of "options"
```
options snd-hda-intel model=3stack
``` 
Note... you must edit this file in Root.

---

### Post by jonward690 on 2007-12-08
Thanks so much man I realy apreciate it a lot

---

### Post by jonward690 on 2007-12-08
Ok my bad I though this fixed it but it just made it worse but thanks for trying,do you have any other ideas on how to fix this?

---

### Post by Don1500 on 2007-12-08
load the latest ALSA files and compile them yourself.

---

### Post by jonward690 on 2007-12-08
Well that sounds good could you give me a link to a site or a guide on how I would do this.

---

### Post by Don1500 on 2007-12-08
Now that you're really lost. If you know how to boot to ROOT do it. Ckeck out your audioo here, then, if it's good, load the settings you have in root to your normal user.

---

### Post by jonward690 on 2007-12-08
I loged into root and does the same thing.

---

