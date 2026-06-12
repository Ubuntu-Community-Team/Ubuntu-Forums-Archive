---
title: "Can't start Edgy on Dual Boot System"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by Julian David Pitt on 2006-12-01
I have a dual boot system and whilst I can start Windoze I cannot start Edgy. I see the menu.lst and select Edgy, whereupon I get the splash screen. The status bar then works its way across and when it gets to the end the screen goes blank and the monitor goes on standby. If I select the recovery operation on boot and then type startx at the prompt I get the same effect. Can someone tell me what is happening here as the system used to boot up ok and I haven't done anything that I can think might cause this. Thanks.

---

### Post by Bachstelze on 2006-12-01
A possible cause for this is that the X server for whatever reason tries to use a resolution your monitor can't handle. Try reconfiguring your X server to choose a lower resolution.

---

### Post by Julian David Pitt on 2006-12-01
Please can you tell me how I go about changing the display resolution if I cannot log in or see what I am doing. I presume I need to enter something at the terminal prompt, I will take a look around the forum to see if I can find what I need.

---

### Post by Bachstelze on 2006-12-01
```
sudo dpkg-reconfigure xserver-xorg
```

will prompt you for the resolution(s) you want to use, as well as a whole bunch of other stuff, if you don't know what to answer, stick with the defaults.

---

### Post by Julian David Pitt on 2006-12-01
Thanks very much I will do that when I get back to the system at home.

---

### Post by Julian David Pitt on 2006-12-01
> **Julian David Pitt said:**
> Thanks very much I will do that when I get back to the system at home.

I ran the command and was surprised by the complexity of all the questions I was asked, to cut a long story short I ended up with the resolution set at 640x480 and I now cannot change it. I tried to edit xorg.conf from a previous version, removing all mentions of the higher resolutions but now I have a blank desktop again. Is there not a command I can run to merely change just the default resolution. Cheers people.

---

