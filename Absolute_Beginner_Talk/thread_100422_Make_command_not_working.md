---
title: "Make command not working"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by Justus on 2005-12-07
I downloaded some GUI networking program, that's supposed to make it easier to get your modem configured and everything, and the install instuctions say to use the "make" command to compile it. When I try to run make, it says "file not found", or "program not found" or whatever. Help!:o

---

### Post by jrib on 2005-12-07
Install the build-essential package.  You can use synaptic or you can just use apt-get and type:

```
sudo apt-get install build-essential
```

---

### Post by public_void on 2005-12-07
When you ./configure look at the last couple of lines, there could be some packages you need.

---

### Post by Justus on 2005-12-07
[QUOTE=_jason]Install the build-essential package.  You can use synaptic or you can just use apt-get and type:

```
sudo apt-get install build-essential
```[/QUOTE]

I think I need internet to do that, right? Still trying to figure out how to connect to dial-up to do that. And if I could figure out how to connect, I wouldn't need that program in the first place:( Thanks for trying though lol. Hopefully I'll get it figured out...eventually

---

### Post by darth_vector on 2005-12-07
i belive build-essential is on the cd, it just isnt installed by default.

---

