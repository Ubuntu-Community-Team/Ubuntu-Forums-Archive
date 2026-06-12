---
title: "Linux Dxdiag and a q bout automax"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by kavon89 on 2007-01-05
Hi, in Winblows we have this neat thing called 'dxdiag' which is a command in the Run window that brings up a lot of system details like sound card name/driver version/display card/driver version/basic system specs etc. Is there a similar easy command in Ubuntu?

Can some one link me to the Wiki u guys have on using that Automax thing to install the most common packages? Thank you

---

### Post by taurus on 2007-01-05
Applications -> Accessories -> Terminal
```
lspci
lshw
lsmod
```

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by PriceChild on 2007-01-05
Please try and follow wiki articles to install things yourself without resorting to automatix... you will learn a lot more and be able to fix things with this knowledge. :)

---

### Post by kavon89 on 2007-01-05
man make automax

man give automax

me use automax

me happy :D 

==

```
lspci
lshw
lsmod
```

There a diffrence between the three? seems lspci means ur motherboard info, lshw is hardware... and whats lsmod for?

---

### Post by taurus on 2007-01-05
> **kavon89 said:**
> 
and whats lsmod for?

The modules/drivers that you are currently using/running...

---

