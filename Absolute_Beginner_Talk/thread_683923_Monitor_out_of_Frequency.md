---
title: "Monitor out of Frequency"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Riptr on 2008-01-31
When I try to boot up the Ubuntu or any Ubuntu variant live CD, and I start up the Live CD enviroment and it begins to load, but unfortunately when the "bar" loads to 100% my monitor bluntly informs me that my monitor is out of frequency.

Simple question is, how would I get around this issue, I have read similar issues with solutions like "CTRL+ALT+F2" and sudo dpkg -reconfigure -phigh xserver -xorg.

Thank you in advance.

CPU: AMD ATHLON 2800+ 2.08GHz
RAM: 1GB
GPU: Sapphire ATI Radeon X1950 GT 256MB

---

### Post by benfindlay on 2008-01-31
Yes, pressing Ctrl+Alt+F2 will change you to a shell. Log in with your username and password.

Then the code you need is ```
sudo dpkg-reconfigure xserver-xorg
```

Just follow the prompts on screen and choose the advanced option when prompted I believe. This will allow you to set frequencies and refresh rates and the like for your monitor. If that doesn't work, rerun the above command and choose Medium instead when prompoet, which will allow you to select all the resolutions you want available (by highlighting them with arrow keys and pressing spacebar to select, then press enter when you have selected all the ones you want).

Hope this helps!

---

### Post by Riptr on 2008-01-31
Thank you very much, it worked like a charm.

Now expect me to blow my computer up or something :P.

---

