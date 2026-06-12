---
title: "gdesklets Trouble"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by kevCast on 2007-03-05
When I open gdesklets, it show know interface aside from white, and I have to force quit to get out of it. It's completly glitched out. Is there a way I can remove it completly 100% from my system? Any help is appreciated, thank you.

---

### Post by charles.g.moore on 2007-03-05
Did you install it through synaptic or apt?

---

### Post by kevCast on 2007-03-05
apt

---

### Post by jamyskis on 2007-03-05
> **kevCast said:**
> apt

It doesn't actually matter by which of those two methods you installed it through - it's still stored in the DPKG database, and you can remove it with a simple:

sudo dpkg -r gdesklets

---

### Post by kevCast on 2007-03-05
It tells me to purge.

---

### Post by jamyskis on 2007-03-05
> **kevCast said:**
> It tells me to purge.

Odd - well, the command you'd be wantin' then is:

sudo dpkg --purge gdesklets

---

