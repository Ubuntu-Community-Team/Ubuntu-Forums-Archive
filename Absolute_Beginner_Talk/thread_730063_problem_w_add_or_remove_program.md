---
title: "problem w/ add or remove program"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by hershe33 on 2008-03-20
when I start add or remove program an error message come up. this is what it says

This is a major failure of your software management system. Please check for broken packages with synaptic, check th file permisions and correctness of the file '/etc/apt/sources.list'
and reload the software info. with sudo apt-get update' and sudo apt-get install -f

Can u help me the codes don't work. I've tried them so many times.

---

### Post by Oldsoldier2003 on 2008-03-20
> **hershe33 said:**
> when I start add or remove program an error message come up. this is what it says

This is a major failure of your software management system. Please check for broken packages with synaptic, check th file permisions and correctness of the file '/etc/apt/sources.list'
and reload the software info. with sudo apt-get update' and sudo apt-get install -f

Can u help me the codes don't work. I've tried them so many times.

please paste the error messages you received when you run the commands in a terminal:
```

sudo apt-get update
sudo apt-get install -f
```

---

### Post by forestpixie on 2008-03-20
can you post your sources

```
cat /etc/apt/sources.list
```

---

