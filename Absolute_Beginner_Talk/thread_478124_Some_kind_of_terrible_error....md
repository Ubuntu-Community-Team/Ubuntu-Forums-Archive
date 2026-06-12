---
title: "Some kind of terrible error..."
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by volksolwagen57 on 2007-06-19
i typed sudo nvidia-settings to change my resolution to 1280x1024 and 75hrz refresh rate and everything was fine. i go to restart and i'm asked if a want to delete an applet and i accidently pressed delete and now my windows don't work and the terminal doesn't work at all. i try to reload the windo decorator in beryl manager and nothing. i try to quit from beryl and nothing. by the way, my screen resolution is back to that funky 1024x768 which is aweful. the problem is that i totally forgot the name of the applet that i deleted i think it was like: ```
MIME::GNOME applet
``` and it asked if i wanted to delete it and like an idiot i hit yes. has this happened to anyone. i don't think i backed up my xserver-xorg. if i did, like when i did the beryl thing (i think i might have done it, but i don't remember), where can i find it and load it?
i appreciate your help in advance? please help, please??:(

---

### Post by dbbolton on 2007-06-19
> **volksolwagen57 said:**
> i typed sudo nvidia-settings to change my resolution to 1280x1024 and 75hrz refresh rate and everything was fine. i go to restart and i'm asked if a want to delete an applet and i accidently pressed delete and now my windows don't work and the terminal doesn't work at all. i try to reload the windo decorator in beryl manager and nothing. i try to quit from beryl and nothing. by the way, my screen resolution is back to that funky 1024x768 which is aweful. the problem is that i totally forgot the name of the applet that i deleted i think it was like: ```
MIME::GNOME applet
``` and it asked if i wanted to delete it and like an idiot i hit yes. has this happened to anyone. i don't think i backed up my xserver-xorg. if i did, like when i did the beryl thing (i think i might have done it, but i don't remember), where can i find it and load it?
i appreciate your help in advance? please help, please??:(
your old xorg.conf - if you made a backup - should still be in /etc/X11/

---

### Post by mikewhatever on 2007-06-19
You can try booting into the recovery mode. There is no GUI, just the command line. Look for the backup using ls command
> ls /etc/X11

Another option is to use the live cd, mount the root partition and look for the backup. Suppose you do have a backup named xorg.conf_backup, then the following command will restore it
> sudo cp xorg.conf_backup xorg.conf

---

### Post by volksolwagen57 on 2007-06-23
thanks for the help!!!!!!!!

---

### Post by octoberdan on 2007-06-23
> **volksolwagen57 said:**
> thanks for the help!!!!!!!!

Were you able to get it working?

---

