---
title: "Failed to start X Server?  Please help!"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by lemonsCC on 2006-10-14
When I start ubuntu I get an error message saying X server failed to start.

```
(EE) No devices detected.
Fatal server error:
no screens found
```

Please help!

---

### Post by taurus on 2006-10-14
You need to reconfigure your X again.  At the prompt, do

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by lemonsCC on 2006-10-14
I am trying that now.  What causes it to get messed up?

---

### Post by taurus on 2006-10-14
> **lemonsCC said:**
> What causes it to get messed up?
I have no idea but somehow your /etc/X11/xorg.conf is missing a section for your monitor!

---

### Post by lemonsCC on 2006-10-14
use kernel framebuffer device interface?

---

### Post by taurus on 2006-10-14
> **lemonsCC said:**
> use kernel framebuffer device interface?
Sure.  And if it doesn't work, run that command again and choose a difference answer.  ;)

---

### Post by lemonsCC on 2006-10-14
I left it on "No."

Thank you jesus it works!

---

### Post by lemonsCC on 2006-10-14
*Hands taurus avagardo's number of cookies*

---

### Post by taurus on 2006-10-14
> **lemonsCC said:**
> 
Thank you jesus it works!
:-|

---

