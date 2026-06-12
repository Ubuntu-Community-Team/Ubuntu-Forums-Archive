---
title: "nVidia Control Panel Access &amp; Options"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-09-24
Ok, so I've gathered that to open it, I can go "nvidia-settings", but you know that feature that is a check box called "allow flipping" in the tab "OpenGL Settings"?  Well, is there a command or 2 that I can run to turn it on and then back off again? :p  I know this sounds weird, but I have my reasons... :)

---

### Post by mesilliac on 2007-09-25
If you open a terminal and type ```
nvidia-settings --help
``` it will tell you the common options you can pass to nvidia-settings. In this particular case, you could use ```
nvidia-settings -a AllowFlipping=0
``` to turn it off, and a similar command to turn it back on :).

---

### Post by ryanVickers on 2007-09-25
I read through all of that, and in theory, you should be right, but it doesn't work; I looked in the nvidia-settings window and the checkbox was still off when I said to make it "1" :(

:confused: Edit: Interestingly enough, I used the same command to adjust the gamma, and it worked perfectly...:confused:

---

### Post by mesilliac on 2007-09-26
It did work. But the change is only temporary, it doesn't write it to your .nvidia-settings-rc configuration file. When you run nvidia-settings by itself, it loads and applies this file, overwriting whatever you just set via the command line :).

A better way to check the current setting would be to use ```
nvidia-settings -q AllowFlipping
```

If you wanted the change to stick, you could make another config file and swap it before running nvidia-settings, I just think the temporary change is cleaner :).

---

### Post by ryanVickers on 2007-09-26
But there must be some command that does the same thing as clicking the checkbox?!?! :p

---

