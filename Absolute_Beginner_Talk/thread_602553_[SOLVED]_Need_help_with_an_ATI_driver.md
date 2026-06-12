---
title: "[SOLVED] Need help with an ATI driver"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-11-04
Hi, I was following a guide to get Compiz working on Gusty ([http://ubuntuforums.org/showthread.php?t=591445](http://ubuntuforums.org/showthread.php?t=591445)) but it failed. I am now having to use Ubuntu from a text interface and I really need my computer working by tomorrow. Can someone help me reinstall the driver for my ATI Radeon Xpress 200m through a text interface? Thanks.

Edit: By the way, the guide failed at step three for me.

---

### Post by overdrank on 2007-11-04
> **kevindubrow said:**
> Hi, I was following a guide to get Compiz working on Gusty ([http://ubuntuforums.org/showthread.php?t=591445](http://ubuntuforums.org/showthread.php?t=591445)) but it failed. I am now having to use Ubuntu from a text interface and I really need my computer working by tomorrow. Can someone help me reinstall the driver for my ATI Radeon Xpress 200m through a text interface? Thanks.

Edit: By the way, the guide failed at step three for me.

Hi, from the command line Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by carlosjuero on 2007-11-04
Quickest way for ATI to do this is ```
sudo aticonfig --initial --force
```, it resets the xorg configuration to pre-ATI driver installation values.

---

### Post by kevindubrow on 2007-11-04
Thank you all for the quick response, I'll jot these codes down and get back to you as soon as possible with their results.

---

### Post by kevindubrow on 2007-11-04
Everything is back to normal! Thank you all for getting me away from Windows...it is sad how problematic it can be. Ubuntu only stops working for me when I do something very dumb. Haha, thanks again for the help!

---

### Post by carlosjuero on 2007-11-04
> **kevindubrow said:**
> Everything is back to normal! Thank you all for getting me away from Windows...it is sad how problematic it can be. Ubuntu only stops working for me when I do something very dumb. Haha, thanks again for the help!
Heh, Windows can be quite annoying; If I could do everything in Ubuntu I would - but I stick here most of the time.

Lots of the people on this forum are glad to help new users get into Linux/Ubuntu - it is a much better experience (unless you do something crazy - I have done the same sorta thing [like trying to get Compiz working good with the bloody ATI fglrx.. it doesn't like newer cards :(]).

Happy Ubuntuing :D

---

### Post by kevindubrow on 2007-11-04
Thanks, same to you!

---

