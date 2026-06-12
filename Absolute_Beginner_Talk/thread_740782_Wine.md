---
title: "Wine"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by doomedfire on 2008-03-31
How do i install wine? 

Thx in advance.

---

### Post by kpkeerthi on 2008-03-31
Check [this]("http://www.winehq.org/site/download-deb") out for a step-by-step instructions

---

### Post by prismpirate on 2008-03-31
Go to 

Application > Accessories > Terminal:

A box comes out.

Copy and paste this text:

```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list

```

You will have to enter your password.

Next, paste or type the following text:

```

sudo apt-get update

```
```

sudo apt-get install wine

```

---

### Post by doomedfire on 2008-03-31
Ok i got it installed its under applications i clicked configure my pc froze
i rebooted tried again it froze rebooted i tried notepad it froze,

---

### Post by Battalion on 2008-03-31
Have you tried booting in recovery mode? You can try and run from live cd and see if you can rescue your system if all fails

---

### Post by doomedfire on 2008-03-31
Its just when i click wine Otherwise im running fine.

---

### Post by lswest on 2008-03-31
have you run ```
winecfg
``` in the terminal?  it builds the required files.  Might take a bit.

---

### Post by Battalion on 2008-04-02
> **lswest said:**
> have you run ```
winecfg
``` in the terminal?  it builds the required files.  Might take a bit.

If this doesn't work, check synaptic because there might be a damaged package thats causing the problem.  but winecfg should work.

---

