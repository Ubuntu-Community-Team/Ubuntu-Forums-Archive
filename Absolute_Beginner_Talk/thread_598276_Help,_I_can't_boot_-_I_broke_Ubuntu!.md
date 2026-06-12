---
title: "Help, I can't boot - I broke Ubuntu!"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-10-31
Tried to do some sound card/driver fixing. Was instructed to reboot the pc & now I am stuck at a virtual prompt, no way to restore the system? I can't get past this point to the desktop. Help! :confused:

---

### Post by AndyCooll on 2007-10-31
At the prompt login and then type:

```
sudo dpkg-reconfigure xserver-xorg
```

Work your way through that wizard accepting the defaults unless you know particular requirements, then when its finished type:

```
startx
```

:cool:

---

### Post by discmaster on 2007-10-31
Thank you! That is very helpful info. I will print that for future reference!
:popcorn:

---

