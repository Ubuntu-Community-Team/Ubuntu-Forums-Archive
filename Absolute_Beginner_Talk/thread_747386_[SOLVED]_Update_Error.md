---
title: "[SOLVED] Update Error"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by Orcaporka on 2008-04-06
I was updating when there was a error in one of the files i downloaded this caused my computer to slow right down and was pretty much ineffective. I reset it and now my wireless doesnt work, and when I got back to the updates its says I must manually run "dpkg --configure -a" but whe I do I am told I need superuser priviledge.

Any idea?

---

### Post by artir on 2008-04-06
execute sudo dpkg --configure -a 
enter your pasword when your system told you to do so and wait :)

---

### Post by skymera on 2008-04-06
what do you mean reset it?

try

```
 sudo dpkg --configure -a 
```

---

### Post by Orcaporka on 2008-04-06
> **skymera said:**
> what do you mean reset it?

try

```
 sudo dpkg --configure -a 
```

thank you, no error now but, I still cannot get back on my wireless.

---

### Post by Orcaporka on 2008-04-06
In network there isnt even a choice for wireless anymore just wired and modem.

Also the light that indicates that my wirless is on, is on but I have no conncection.

---

### Post by Orcaporka on 2008-04-06
2nd page bump.

---

