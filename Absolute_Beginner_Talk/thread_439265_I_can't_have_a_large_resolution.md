---
title: "I can't have a large resolution?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by OutThisLife on 2007-05-10
Okay so on windows I had a 1600x1024 60hz resolution and it worked fine.

Now that I'm back on Linux I tried to edit the xorg.conf to allow this resolution and it will either:

[LIST]
[*]Crash to terminal
[*]It will stay a 1024x786 resolution but I can "scroll" around the screen as if it was 1600x1024
[/LIST]

I have NVidia 6150 LE, 2GB RAM so I don't think that's a problem :]

Any ideas? I really can't stand this 1024x786 thing :x

---

### Post by annda on 2007-05-10
do you have the nvidia driver installed?

if so, back up your xorg.conf and use nvidia-settings to make the necessary changes:
```

gksu nvidia-settings
```

---

### Post by LaRoza on 2007-05-10
Interestingly I have the same card and a similar problem, I fixed it by pressing "auto - adjust" on my monitor.

I wanted 1280x1024 by couldn't, but could only get 1024x768, with is warped. Auto-adjust fixed it, it still says 1024x768, but looks 1280x1024, weird, but it works fine.

---

### Post by Wim Sturkenboom on 2007-05-10
Some points
1) Install the driver
2) Adjust the horizsync/vertrefresh to meet the specs of the monitor (xorg.conf)
3) Add the resolution (xorg.conf)

---

### Post by OutThisLife on 2007-05-10
> **annda said:**
> do you have the nvidia driver installed?

if so, back up your xorg.conf and use nvidia-settings to make the necessary changes:
```

gksu nvidia-settings
```

Thank you that worked! :D

/lick

---

