---
title: "gnome-panel blinking and unresponsive"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2007-03-27
My gnome-panel is blinking, and unresponsive in fiesty. I have tried reconfiguring the xserver with no results. Everything was working fine until a restart this afternoon. Does anyone know how to fix this?

Edit: It seems this was caused by some update to compiz. For a temporary solution I started a failsafe terminal session and typed in ```
desktop-effects --disable
```

---

### Post by adam.tropics on 2007-03-28
I had a similar problem after yesterdays updates with the same package, but after today's updates it was fixed, which is good, because my poor cpu needed a break!

---

### Post by DSn0wMan on 2007-03-28
Ok, I got my desktop-effects working. The offending package was compiz-extra. Once I removed compiz-extra I was able to re-enable desktop-effects with the desired results.

---

