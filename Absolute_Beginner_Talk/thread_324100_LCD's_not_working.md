---
title: "LCD's not working"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by Uncle_John on 2006-12-23
hey:p 

I recently got new LCD. I have two OS on my computer. When I run windows everything is Ok, I mean screen works. but when I run Ubuntu screen stays black, but I know it works cuz i hear sound when I sign in. Maybe there's a problem with driver? But how can I install driver if I don't see anything? :confused: :confused:

---

### Post by taurus on 2006-12-23
If you replace your old monitor with a new one, you need to reconfigure your X again.  To do that, you need to boot into recovery mode from GRUB menu and at the prompt, run

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

