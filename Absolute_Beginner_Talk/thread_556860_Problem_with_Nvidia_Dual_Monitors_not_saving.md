---
title: "Problem with Nvidia Dual Monitors not saving"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by orion2087 on 2007-09-21
Hey guys, Ubuntu is great so far but I'm having trouble getting dual monitors set up the way I want. Ubuntu is booting exclusively to my TV (right) monitor whenever its plugged in. I've tried switching ports but its still the same. I want to have my left monitor booted to and my right monitor off by default. I can set this up in nvidia-settings but it doesn't keep it next time I restart, even when I select "Save to X Configuration File".

Any thoughts?

---

### Post by NoThanksM$ on 2007-09-21
Are you running the nvidia control panel as root?  You can do this by typing:
sudo nvidia-settings
in the terminal.  only by doing this can you save changes to the X configuration file.

---

### Post by C.S.Cameron on 2007-09-22
You can also save it to your desk top then replace the original using terminal, but No's answer seems simpler.

---

### Post by NoThanksM$ on 2007-09-22
That's true, I should have qualified.  I meant that was the only way to do it using only the nvidia control panel.

---

