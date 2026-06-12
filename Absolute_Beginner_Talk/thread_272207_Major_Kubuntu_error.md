---
title: "Major Kubuntu error"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-10-05
Well, this happened on the dabber live cd also.
When the computer first turns on it says "Media protocol died unexpectantly".
I am not sure wether this has affected my system or not but now I can't get in adept. It says it's already running when it's not. I hope it doesn't come to reinstalling my entire system. :(

---

### Post by Ben Sprinkle on 2006-10-05
After typing:
```

sudo aptitude

```
I realized this:
```

dpkg --configure -a

```
And it fixed it. :) Well at least the thing with adept, anyone know what's wrong with the startup?

---

