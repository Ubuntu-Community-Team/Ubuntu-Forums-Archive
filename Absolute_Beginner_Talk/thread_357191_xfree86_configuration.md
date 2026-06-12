---
title: "xfree86 configuration"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by konungursvia on 2007-02-09
I've been running Dapper on a Dell Inspiron for a few weeks now (thanks for the help guys), but I haven't been able to get it to run on my old Acer.

Now I've got a pure Debian ISO installed onto the Acer but I'm having trouble configuring xfree86. Does anyone have a suggestion as to the most likely defaults to guess? Shoule i use the vga driver or the vesa driver? What should I then put for the bus location? Thanks  a lot (Debian is the basis for ubuntu I hear).

---

### Post by taurus on 2007-02-09
When or else fails, use **vesa** and if you want to know the BusID, run this command from a terminal or console.

```
lspci
```

---

### Post by konungursvia on 2007-02-09
My god, it worked! Thanks taurus.

---

### Post by taurus on 2007-02-09
You're welcome.

---

