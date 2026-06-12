---
title: "Problem with desktop"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by disc on 2006-11-02
Okay, I just recently tryed to install the Xubuntu desktop-environment on my system(changing from Ubuntu to Xubuntu) with the terminal command:
```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

I allowed the terminal to finish executing the commands, then I rebooted my computer. Upon booting up, it gave me an error that reads:

Failed to start the X server(your graphical interface.) It is likely that it is not set up correctly. Would you like to view an output to diagnose the problem?

I press Yes, and I get:

Fatal server error
No screens found

It then says that X server is now disabled, and to restart GDM when it is configured correctly. Then it takes to a standard terminal command line. Any suggestions to get my desktop working?

---

### Post by kerry_s on 2006-11-02
Try-> sudo dpkg-reconfigure -phigh xserver-xorg   <or> sudo dpkg-reconfigure xserver-xorg

---

