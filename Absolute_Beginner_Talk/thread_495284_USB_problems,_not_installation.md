---
title: "USB problems, not installation"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Rapidsnow on 2007-07-07
I am using ubuntu feisty i386 version with an AMD 64x2 processor. Ok fun stuff out of the way. When I plug in a usb memory stick into the socket of the lap top it does not recognize the device. I go to places and computer (I also do this in the terminal) and I do not see it, I tried to mount it once, but it didn't work since it couldn't find the device. Other USB devices (namely my mouse) work fine, just the three different brand memory keys I have used do not work... any ideas?

---

### Post by p_quarles on 2007-07-07
I had the same problem a couple days ago. I was able to fix it using this (terminal) ```
sudo /etc/init.d/dbus restart
```

Try it. It won't hurt anything, even if it doesn't fix the problem.

---

### Post by Rapidsnow on 2007-07-07
Didn't work... thanks though.

---

### Post by p_quarles on 2007-07-07
I forgot to mention that I also had to restart the GUI after doing that. Either go to the shutoff menu and select "Log Out", or press ctrl-alt-backspace. Then log in again.

---

### Post by Rapidsnow on 2007-07-07
Yea I tried that originally, I'm still not sure what is going on. 

Edit: It actually worked, I had to restart the whole computer not just the GUI. Thank you so much!!!

---

