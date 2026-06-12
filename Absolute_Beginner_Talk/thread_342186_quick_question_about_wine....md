---
title: "quick question about wine..."
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by je1117 on 2007-01-19
I don't see wine in the synaptic package manager... but I have installed on my system. how could i potentially uninstall it?

---

### Post by bodhi.zazen on 2007-01-19
How did you install it then ???

---

### Post by taurus on 2007-01-19
Did you install it by hand or with automatix2?  See what happens if you remove it from a terminal?

```
sudo aptitude remove wine
```

---

### Post by je1117 on 2007-01-19
I was trying a couple of things at the same time, but I think what did it was I forced a i386 install on my amd64.

---

### Post by je1117 on 2007-01-19
How do you install it with automatix?

---

### Post by taurus on 2007-01-19
Did you install it with the "sudo dpkg -i **filename**.deb" command?

```
sudo dpkg -r **filename**
```

---

### Post by taurus on 2007-01-19
> **je1117 said:**
> How do you install it with automatix?

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by je1117 on 2007-01-19
that's right.

I have automatix, but i dont see where it is...

---

