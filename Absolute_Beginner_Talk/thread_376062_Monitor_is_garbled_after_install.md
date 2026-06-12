---
title: "Monitor is garbled after install"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Deguello on 2007-03-04
Hello all....I am trying to install Feisty-Herd with the Wubi installer. I can get it installed, but when the system reboots into Ubuntu, my screen is jumbled, as if the resolution is not set correctly. 

I have the nVidia 6200 video card and cannot find a way to get it to be clear. Is there something I can do with the drivers? Or is there a safe mode to go into to set the resolution.

I have tried a search, but as this is new to me, it is like reading Greek. Thank you!

---

### Post by toasterofirony on 2007-03-04
By jumbled, do you mean it doesn't start X and dumps you back at the CLI?

If so, try reinstalling the graphics driver. Seems to cure a multitude of sins when it comes to graphical anomalies.

---

### Post by Deguello on 2007-03-04
The OS starts and boots into the login screen as I hear the startup sound. The problem is that I cannot see it. I get a screen that changes colors and has ghosting of what I am guessing is the login in screen. But it is not enough to see what is going on.

Can I re-install the graphics driver through the windows environment? If not, how is this accomplished through Ubuntu if I can't see what is on the screen?

Thanks for the fast reply.

---

### Post by toasterofirony on 2007-03-04
Okies, you need to hit crtl+alt+f1, to get to a CLI login.

Login as you would with the GUI, then install [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") (my personal suggestion as it makes sure you get everything up and running properly.

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb
sudo dpkg -i envy_0.8.2-0ubuntu1_all.deb
envy
```

This should sort you out.

---

### Post by Deguello on 2007-03-04
Thank you...I will try this and report back.

---

### Post by toasterofirony on 2007-03-04
aaargh.

Sorry! You're running Feisty! Envy might not work! 

>.<

I misread your post.

---

