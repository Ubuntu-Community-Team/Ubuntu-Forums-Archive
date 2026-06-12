---
title: "No sound on Toshiba Satellite A135-S4427"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by vozzon on 2007-04-24
I installed Feisty on my laptop which is a Toshiba Satellite A135-S4427 ([http://www.amazon.com/Toshiba-Satellite-A135-S4427-Widescreen-SuperMulti/dp/B000M8WTEU](http://www.amazon.com/Toshiba-Satellite-A135-S4427-Widescreen-SuperMulti/dp/B000M8WTEU)) and there is no sound. No sound in flash, xmms, gaim, everything.

What is possibly the problem?

---

### Post by granite230 on 2007-04-25
Try 'alsamixer' in your terminal, or check out this page:

[http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207)

I have a Toshiba Sattelite A100 635. This worked for me:

A less hacky way to do the same is to edit /etc/modprobe.d/alsa-base and add to the end of the file:

Code:

options snd-hda-intel model=auto

Changes will take effect after a reboot.

---

