---
title: "How do I force an lm_sensors update to lm_sensors-2.10.0?"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by jtp51 on 2006-03-28
How do I force an lm_sensors update to lm_sensors-2.10.0?

I using: sudo apt-get -u upgrade

Thanks,

--Todd

---

### Post by Pragmatist on 2006-03-28
If: 
```
sudo apt-get update
``` followed by:
```
apt-get upgrade lm_sensors
``` 
doesn't upgrade your package, you either need to try and enable another repository in your /etc/apt/sources.list file, or, more typically, just go find the exact version you want via google and then either use a debian binary or compile from source depending on what is available

---

