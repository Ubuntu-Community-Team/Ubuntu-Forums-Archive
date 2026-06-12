---
title: "I meesed up my display settings"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by k8fox1 on 2008-02-03
I am running Gutsy 7.10. I was experimenting with different display settings and apparently selected one that won't allow an image on my monitor when i boot. The system boots but the monitor is blank with a message that the settings are not supported or something to that effect. How can I fix this?

Thanks! :confused:

---

### Post by rob1101 on 2008-02-03
boot into safe mode and try this

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by k8fox1 on 2008-02-03
Yep that worked, thanks. Can you tell me why the font on my log-in screen is so small now I can barely see it?

Thanks!:)

---

### Post by rob1101 on 2008-02-03
what resolution did you choose

---

