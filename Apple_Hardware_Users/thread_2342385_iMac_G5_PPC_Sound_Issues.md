---
title: "iMac G5 PPC Sound Issues"
date: 2016-11-06
forum: Apple Hardware Users
---

### Post by arrowin13 on 2016-11-06
I have read a lot of forums and tried to fix this a few times, In my final conclusion, each attempt has failed... Anything you could tell me to fix this would be useful. I am using **Lubuntu version 12.04** (Using 12.04 for certain reasons.) I have prior experience with Linux and have never before had issues like this.

---

### Post by howefield on 2016-11-06
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by rican-linux on 2016-11-07
try 

```

sudo modprobe snd-aoa-i2sbus

```

Then run the command *alsamixer* and set the PCM Channel to 70.

Hope that helps!

---

