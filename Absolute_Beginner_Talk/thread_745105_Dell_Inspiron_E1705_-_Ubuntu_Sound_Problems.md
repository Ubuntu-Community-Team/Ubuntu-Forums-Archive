---
title: "Dell Inspiron E1705 - Ubuntu Sound Problems"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by duke_420 on 2008-04-04
hey guys,

aight so i installed linux ubuntu on my laptop(no windows nothing but ubuntu on my laptop).

i have been listening to music for a long time now ever since i got it installed, i put it to sleep and then when i brought my computer back up, the screen was blank and i had to do a manual shutdown. when i booted up my laptop, THE SOUND STOPPED WORKING.

this stinks for a guy who loves his music... can someone help me and figure out why my sound is messed up?

i did this in the terminal:
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa


and rebooted and nothing works. i thought it may have been my music files so i tried to open the songs in rhythembox, amarok, and watever other default comes wit the install. NO SOUND.!!!

someone please help me get my sound back.

---

### Post by northern lights on 2008-04-04
Can you post the output of ```
cat /proc/asound/cards
```
and, have you checked ```
alsamixer
``` for low volume or a muted master, e.g.?

---

