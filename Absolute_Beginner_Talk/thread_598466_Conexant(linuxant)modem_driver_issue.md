---
title: "Conexant(linuxant)modem driver issue"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by poision_heart on 2007-10-31
Hi i installed linuxant(conexant) modem drivers on gutsy for my compaq v3000z laptop.1st of all i found its non free drivers and free drivers only providing ya 14.4kbps speed.N linuxant says you ve to pay for full version.Well i installed free drivers,everything went well but now it locked my sound.Does anyone tried this drivers or pls guide how to open sound again?Is there any alternative to make my modem work?Pls help me in modem and sound working.Thanks in advance.

---

### Post by realvz on 2007-10-31
i understand ur pain...i just did this a few days ago...
there might be a better way to do this but this is what i did

```

sudo apt-get install module-assistan alsa-source
```

let it complete..
once done open the terminal and type this

```
sudo m-a a-i alsa-source
```

and let me know if this works...

again experts can say this is not the best (maybe) but it works perfectly for me.

---

### Post by poision_heart on 2007-10-31
Oh thanks buddy i ll give ya try now.Is there any other way for my modem?

---

