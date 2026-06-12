---
title: "Saving nvidia settings"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by ryana on 2007-09-01
I've seen other people post similar things to this, but nothing has fixed this for me. When I restart my computer the video settings are set to 1024x768. I do a 'sudo nvidia-settings' and change resolution to 1152x864, press 'apply', press 'Save to X Configuration File'. Then the screen is the right size....until I restart and it reverts to 1024x768. How can I make this setting actually save after reboot? Also, If i go to screen resolution from system menu, it has that option to apply, but the refresh rate is a horrible 50fps...anything under 60fps bugs the **** out of me as I can see the difference.

If it matters I have nvidia geforce 5500fx video card.

---

### Post by wolfen69 on 2007-09-01
in terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

---

