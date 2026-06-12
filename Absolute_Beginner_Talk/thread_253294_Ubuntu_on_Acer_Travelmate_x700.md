---
title: "Ubuntu on Acer Travelmate x700"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by steffeo on 2006-09-08
Hi! I have problems when x starts up. The screen goes blank. I know this is because the wrong driver starts up. I have tried to change the driver in the xorg.config to vesa, fglrx and vga, but I get error messages such as no screens found, or no driver found. I know there are drivers available at the ati website, I can however not find out how I install these drivers from the terminal, as I have no gui to do this in. Could anyone help me to download and install these drivers from the shell?

Any help, thank you!

---

### Post by Apple 101 on 2006-09-08
Try this command in the terminal: *pkg-reconfigure -phigh server-xorg*

---

### Post by steffeo on 2006-09-08
And what would this do? Dont I need to install a new driver before anything will work?

---

### Post by aik2 on 2006-09-08
[http://ubuntuforums.org/showthread.php?t=143283](http://ubuntuforums.org/showthread.php?t=143283)

Could this solve it for you...?

---

### Post by steffeo on 2006-09-10
Hey, this looks like something that could work, I will try this asap! Thank you very much for that link.

---

### Post by steffeo on 2006-09-11
Hi! I found a link that works. Apparently the driver works just fine and dandy. However, when it is a laptop, one has to add an option in xorg.conf that is should send image to a laptop screen, and not a secondary screen. Heres the link so that other people searching for this could get use of it. Thank you all!

[http://ubuntuforums.org/showthread.php?t=190036&highlight=x700]("http://ubuntuforums.org/showthread.php?t=190036&highlight=x700")

---

