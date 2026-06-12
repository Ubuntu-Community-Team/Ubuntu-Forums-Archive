---
title: "Getting cc or gcc for ubuntu"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by NecromancyBlack on 2006-07-28
Hi guys,

I'm currently learning linux and using ubuntu to do so. So far it's great, no idea why I waited till uni to try this stuff out. But I have one problem and that is a c/c++ compiler, namly along the lines of cc, gcc, c++, etc...

Went I try to install stuff it said none of these could be found. I search in each directory listed in $PATH and found that this was indeed the case. I did find cpp-4.0.1 (or something similar) but this doesn't seem to be the same thing.

So, does ubuntu indeed not include a cc-like compiler and if not, were would be the best place to get one and how do I set it up.

thanks

---

### Post by IYY on 2006-07-28
Easy:

```
sudo apt-get install build-essential
```

---

### Post by Swab on 2006-07-28
System > Administration > Synaptic Package Manager

Search for the build-essential package and install it.

---

### Post by NecromancyBlack on 2006-07-28
awesome, thanks guys. I assumed this stuff would've been include in the main install

---

### Post by Swab on 2006-07-28
> **NecromancyBlack said:**
> awesome, thanks guys. I assumed this stuff would've been include in the main install

No, most things people want to install are in the repositories meaning there's not much need for normal users to compile stuff.

---

