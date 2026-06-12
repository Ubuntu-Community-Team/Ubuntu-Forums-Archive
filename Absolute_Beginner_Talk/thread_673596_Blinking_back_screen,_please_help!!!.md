---
title: "Blinking back screen, please help!!!"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by y2kpops on 2008-01-20
I have come back to using ubuntu on my desktop (7.04).

I started to update to 7.10, restarted a couple of times and interupted the update.

I now get a black, blinking screen, when I hit a key I get a blue. grey and red screen and the final messege reads "The X server is now disabled. Restart GDM when it is configured correctly"

I have no idea how to fix the problem, can someone please help?!??

---

### Post by shearn89 on 2008-01-21
either boot into recovery mode, or hit ctrl-alt-f1 to get to a real console. Then log in as usual, and run ```
sudo dpkg-reconfigure xserver-xorg
```

---

