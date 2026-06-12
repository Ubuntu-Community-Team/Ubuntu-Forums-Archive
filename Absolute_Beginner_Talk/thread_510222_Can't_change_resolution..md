---
title: "Can't change resolution."
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Jokeaflorias on 2007-07-26
I just upgraded my video card to a GeForce 7600GT and everything was working great. I had my resolution where I wanted it and there were no problems. Suddenly, I started up Ubuntu today and the screen resolution is at 640x480 at 50Hz, and I can't change it in System > Preferences > Screen Resolution.

Is there anything I can do about this?

Thanks,
Jokeaflorias

---

### Post by wolfen69 on 2007-07-26
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Jokeaflorias on 2007-07-26
Thanks. I did that, and now I'm at the package configuration step where you have to press ok, except pressing enter doesn't do anything and I can't just click the word ok. How am I supposed to say ok?

---

