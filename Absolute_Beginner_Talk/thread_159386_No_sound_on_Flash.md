---
title: "No sound on Flash?"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-04-12
My flash plugins for Firefox are really working strange. I installed them with Automatix and sometimes the sound works, and other times it doesnt?

Is this normal?

The strange thing is that it could be the same websites flash movie that worked today, that wont work tomorrow.

Any thing I can do about this? :confused: 

Thanks

---

### Post by Qrk on 2006-04-13
Flash has sound problems in Linux because Macromedia Flash uses OSS and not ASLA. 

The easiest way to fix it (worked for me) is to install the asla-oss package. Then flash should work when asla is already monopolizing the soud card.

```
sudo apt-get install alsa-oss
```

It has the nice side effect of fixing other OSS apps.

---

### Post by Sef on 2006-04-13
> The easiest way to fix it (worked for me) is to install the asla-oss package. Then flash should work when asla is already monopolizing the soud card.

Code:

sudo apt-get install alsa-oss



It worked for me too. :)  Thanks Qrk.

---

