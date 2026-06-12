---
title: "Video Card Problem"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by prodigalson666 on 2007-09-08
I need help with my video display, nvidia 7100 gs pci-e, my monitors refresh rate 60, it can display 1280 x 1024 how ever the best I can get is 1064 x 768, how can I resolve this? I have tried resetting the x control, that did not help. Thanks

---

### Post by goatflyer on 2007-09-08
Open a terminal and type:
```

sudo dpkg-reconfigure xserver-xorg

```

Answer the questions with default answers until you get to the part dealing with screen resolution.  Then select the screen resolution you want to the xserver to use.  Finish the rest of the questions.

---

### Post by prodigalson666 on 2007-09-08
Ill try thanks. But what if it will not display all my possible screen resolutions like window does?

---

### Post by goatflyer on 2007-09-10
1280 x 1024 *is* one of the resolution choices given when doing "sudo dkpg-reconfigure xserver-xorg".  Just use the arrow keys to scroll down until that resolution is highlighted, then press spacebar to add it to the list of resolutions you want available for the GUI.  Enable any other resolutions you want to change to as well.

---

### Post by alienexplorers on 2007-09-10
Well if you have the correct video drivers loaded (ENVY), the you can us the nvidia-settings program.  Just enter in terminal:
> sudo nvidia-settings

---

