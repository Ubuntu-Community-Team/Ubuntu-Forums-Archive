---
title: "gksudo nautilus not working"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Zzzach on 2008-02-09
gksudo nautilus does nothing now for some strange reason. My computer is driving me crazy right now and I can't even move folders around.

---

### Post by Freddy on 2008-02-09
> **Zzzach said:**
> gksudo nautilus does nothing now for some strange reason. My computer is driving me crazy right now and I can't even move folders around.
Try "gksu nautilus" without "" instead.

---

### Post by Joeb454 on 2008-02-09
What exactly are you trying to do?

And are you using Ubuntu or Kubuntu/Xubuntu? This will make a difference in the command to use.


Also as a security measure, you can't move things about outside your home directory with admin privileges, so that may be why you can't move folders about.

---

### Post by billgoldberg on 2008-02-09
stupid question but does

sudo nautilus 

still work?

---

### Post by tangibleorange on 2008-02-09
Yeah I think "sudo nautilus" does work, but its use is discouraged as it supposedly causes conflicts with a few things. I think gksudo is for graphical apps, and sudo is for command line ones.

---

### Post by seventhc on 2008-02-09
Do you get any error messages? What happens?

---

### Post by Freddy on 2008-02-09
Fire up Synaptic and check that you have the "gksu" package installed and try both "gksudo" and "gksu" both should work the same.

---

