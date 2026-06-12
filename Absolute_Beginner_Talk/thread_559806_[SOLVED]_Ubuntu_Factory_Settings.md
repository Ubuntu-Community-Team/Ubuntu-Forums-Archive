---
title: "[SOLVED] Ubuntu Factory Settings"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by juantastico on 2007-09-25
Hi,
I have been experiencing many problems after trying to install compiz (lost of min. and max. buttons, lost of the 3D cube and lots of main task bar) I do not know if this problems are due to compiz installation, or not, but I am tired of trying to find and endless solution.

Could someone tell me if there is a way to restore the setting of ubutu to the Factory settings (settings that came with the fresh installation) I am dual booting with windows XP.
If I reinstall Ubuntu will I experience any problems with the different disk partitions 


Thank you

---

### Post by skymera on 2007-09-25
i think you need emerald themes.

i have beryl installed and beryl manager reunning, but i using comp-fusion

that sorted my qwindow manager

---

### Post by juantastico on 2007-09-25
Ok, but is there any way to restore to factory settings

---

### Post by master_kernel on 2007-09-25
Not that I know of. Only way I know is by fresh install.

---

### Post by Technophobia on 2007-09-25
you could try to jump out of terminal 7 and try to remove compiz. 

WARNING that his might delete some settings.

Hit **ctrl+alt+f2**

login

**sudo apt-get remove compiz** (will ask to take the life of ubuntu-desktop and desktop-efftects also)

**sudo apt-get install ubuntu-desktop desktop-efftects compiz**

**sudo reboot**


I really have no idea if this will work, in theory it should. Good luck.

---

### Post by juantastico on 2007-09-26
Ok thank you all for you help, however  i reinstall Ubuntu to avoid nay further problems

regards 

JM

---

