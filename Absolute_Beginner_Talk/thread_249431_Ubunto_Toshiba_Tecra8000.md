---
title: "Ubunto Toshiba Tecra8000"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by ceperez48 on 2006-09-02
Could use some help.  Just installed Ubuntu 6.06 and it is working ok.  One problem I have is with the resolution.  Found a fix and states
" Add the following line to the "Monitor" section of /etc/X11/xorg.conf :

        HorizSync       36-52
        VertRefresh     36-60

You can then restart X by simultaneously pressing Ctrl-Alt-Backspace."

Not sure I get around doing this.  Can some one suggest how I do this?

thanks

---

### Post by TFX360 on 2006-09-02
> **ceperez48 said:**
> Could use some help.  Just installed Ubuntu 6.06 and it is working ok.  One problem I have is with the resolution.  Found a fix and states
" Add the following line to the "Monitor" section of /etc/X11/xorg.conf :

        HorizSync       36-52
        VertRefresh     36-60

You can then restart X by simultaneously pressing Ctrl-Alt-Backspace."

Not sure I get around doing this.  Can some one suggest how I do this?

thanks


Open a terminal


Make a backup:


```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bck
```

edit the file:

```
sudo nano /etc/X11/xorg.conf
```

```
ctrl-x
```
```
Enter
```
```
Enter
```

Saves the file.

Reboot 

see if it works

if it doesn't:

```
sudo cp /etc/X11/xorg.conf.bck /etc/X11/xorg.conf
```

To restore the old configuration and reboot:

```
sudo shutdown -r now
```

or

```
sudo reboot
```

---

### Post by TFX360 on 2006-09-02
Print this, it could come in handy :D !!!

---

### Post by ceperez48 on 2006-09-07
Been rather busy,  Will try your suggestion and let you know if it works

---

### Post by jdp on 2006-09-07
I run 6.06 on a Tecra 8000 as well.  You can hand edit the file if you want, or you can run **sudo dpkg-reconfigure xserver-xorg** from the terminal and follow the pompts.  In general accept what it gives you.  It should suggest the NeoMagic chipset, and when it asks for the monitor info (it'll ask what level you want to work at, Simple, Medium, Advandced, choose Medium) select 1024x768@60Hz.  Using the official software to set it up will ensure that your own typing mistakes, or improper values won't make your system unable to start X.

---

