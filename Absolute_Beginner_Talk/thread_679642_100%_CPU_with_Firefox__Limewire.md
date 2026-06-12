---
title: "100% CPU with Firefox / Limewire"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by jesrani on 2008-01-27
Sometimes Firefox uses up 100% CPU. I noticed this while browsing this forum also. I also have 100% CPU usage with Limewire. What to do? Common seems to be java. I checked Synaptic and Sun-java jre 6 is installed.

---

### Post by AlexenderReez on 2008-01-27
hm...i think current java 6 has bug....

```
sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/xawt/libmawt.so
```

but...are you sure it is because of java..?

---

### Post by jesrani on 2008-01-27
It seems so because when I get 100% with Limewire and check System monitor it shows java as using cpu. What does the code do? I ran and nothing happened.

---

### Post by ReddogOne on 2008-01-27
Maybe bit of a red herring but I find that FireFox's CPU usage goes mad when some flash ads/apps are shown. It looks like greedy flash code...

---

### Post by jim2057 on 2008-02-14
I had the same problem with limewire. At the advice of more knowlegable folk, I uninstalled java and limewire and reinstalled Java J2SE 5.0.11and then limewire again - worked for me

---

