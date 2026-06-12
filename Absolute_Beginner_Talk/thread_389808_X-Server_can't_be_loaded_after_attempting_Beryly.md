---
title: "X-Server can't be loaded after attempting Beryly"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by waytorun on 2007-03-21
Hi, I tried to install and run Berly on my laptop with NVIDIA Geforce FX Go 5200.

After I installed Beryl, nothing was happening so I tried installing NViDIA driver

using Envy Script and boom the x-server (gnome) isn't working anymore.

 "Failed to start the X server(your graphical interface). It is likely that it is not set up correctly"


How do I fix this?

I am a beginner in ubuntu scene and not fluent with command so,

step by step would be greatly appreciated.


My Ubuntu was 6.10.


(I found exactly same question thru searching but nobody answered his/her
 post...)

---

### Post by taurus on 2007-03-21
Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again.  

```
dpkg-reconfigure xserver-xorg
```
If you are not sure about a question, just take the default.  However, use **vesa** driver for your graphic card for now until you get X up and running again.  Then, use envy to install nVidia driver for it.

When you are done reconfigured, reboot with

```
shutdown -r now
```

---

### Post by waytorun on 2007-03-21
Thank you for your reply, that solved my problem beautifully !

Really appreciate it.

This forum is great.

---

