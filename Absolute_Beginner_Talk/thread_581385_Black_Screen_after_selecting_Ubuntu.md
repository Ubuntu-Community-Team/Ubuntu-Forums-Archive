---
title: "Black Screen after selecting Ubuntu"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Arkanius on 2007-10-19
On the GRUB, when I select the first Ubuntu option (The topmost), after the upgrade to 7.10, I get a black screen after Ubuntu finishes loading, (So, I get a Black screen when the Welcome screen and login screen should appear, I cant do anything neither). I believe this started after I installed the ATI drivers for my Sony VAIO laptopn (Where Im running Ubuntu), but Im not certain anymore, it was some days ago.

But if I select the other Ubuntu option in the GRUB menu (The other non-recovery option) I can enter fine.

Whats wrong, why can't I enter with the topmost option anymore and what are the differences between the two? Thanks

---

### Post by I3ullit on 2007-10-19
whats the difference between these two entry's?

---

### Post by Arkanius on 2007-10-19
> **I3ullit said:**
> whats the difference between these two entry's?

Seems to be the Kernel. The topmost one has a higher kernel number than the lower one.

---

### Post by I3ullit on 2007-10-19
did you check the Xorg.0.log file?

*System->Administration->System Log*

or

```
cat /var/log/Xorg.0.log
```

seems that there is a problem with the kernel modules

---

