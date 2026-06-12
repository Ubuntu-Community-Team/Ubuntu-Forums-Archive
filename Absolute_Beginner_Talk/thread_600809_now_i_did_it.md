---
title: "now i did it"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by mookie_jones on 2007-11-02
i just tried to install advanced desktop effects. when i rebooted my computer, it said the display driver is not recognized. even worse is when ubuntu finishes loading, im getting a really funky screen with just blurbs of lines n stuff. how can i fix this from the command prompt?

---

### Post by overdrank on 2007-11-02
> **mookie_jones said:**
> i just tried to install advanced desktop effects. when i rebooted my computer, it said the display driver is not recognized. even worse is when ubuntu finishes loading, im getting a really funky screen with just blurbs of lines n stuff. how can i fix this from the command prompt?

Hi and could you tell us what video card you are using?

---

### Post by rudeboyskunk on 2007-11-02
The "quick fix" is to go hit CTRL+ALT+F1 once you're logged in, and type in "sudo apt-get remove compiz" (or whatever the compiz package is).  But let us know what your video card is before you try that.

---

### Post by mookie_jones on 2007-11-02
its a nvidia card

a toshiba p25-s509 laptop

---

### Post by mookie_jones on 2007-11-02
i havent been able to get advanced desktop effects to work and i thought i tricked the system.. oops

im on my windows side right now until i get it fixed

---

### Post by rudeboyskunk on 2007-11-02
Which nVidia card?  It shouldn't be a problem if it's nvidia or ati.

---

### Post by mookie_jones on 2007-11-02
fx go5200 32mb  is what im guessing from google

---

### Post by mookie_jones on 2007-11-02
what can i do to get it to use default driver again?

---

### Post by overdrank on 2007-11-02
> **mookie_jones said:**
> what can i do to get it to use default driver again?

Hi when you reach the login screen use the keys ctrl, alt, F1 all at the same time or from recovery mode command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by mookie_jones on 2007-11-02
ok, im back up and working.. how do i find out why my desktop effects isnt working??

---

### Post by SOULRiDER on 2007-11-02
This may sound silly, but have you installed the nvidia drivers?

---

### Post by overdrank on 2007-11-02
> **mookie_jones said:**
> ok, im back up and working.. how do i find out why my desktop effects isnt working??

Have you enabled the restricted drivers? And have you tried Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
To install the drivers for you graphics card.

---

### Post by mookie_jones on 2007-11-02
um i can tell you right now when i boot up, im showing a nvidia display...

---

