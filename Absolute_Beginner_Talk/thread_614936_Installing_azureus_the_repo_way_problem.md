---
title: "Installing azureus the repo way problem"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-11-16
Hi, I would like to install azureus for my system. When I tried doing apt-get install azureus, I noticed that as a dependency gcj was added to the list of downloads. However, I already have java installed from Sun, which is the one I always use and prefer. When I last installed gcj on top of Sun java, gcj put priority of something like 1001 on the alternatives, overriding the Sun Java.
Is it possible to install azureus and tell it to use Sun Java instead of gcj?

I installed java myself using Sun's .bin download and extracted to /usr/lib/Java6u3/ and set the alternative links to all the Java6u3/bin files to /usr/bin with priority 300.

---

### Post by taurus on 2007-11-16
You can always reconfigureyour system to use your own Sun java with

```
sudo update-alternatives --config java
```

---

### Post by noorez on 2007-11-16
That would be one solution. I guess I could make a script that does that for all the binary files in Java6u3/bin. Is it possible to update the priorities in a script, or will I have to that manually?

---

