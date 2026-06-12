---
title: "Machine unresponsive after X start."
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by gullf1sk on 2006-01-24
Hi there!

I've had some problems the last few days with my nvidia driver. At first i installed the driver with synaptic, and it worked pretty well, xcept for that i didnt have dual-screen. I scratched my head a bit, and tried downloading the drivers from nvidia. After some time with more headscratching, i managed to compile and install the drivers. Dual-screen worked, and all seemed well untill i wanted to use a GLX application. GLX didnt work. So i removed all nvidia drivers\software from my machine, and downloaded the drivers from synaptic again. Hooray i thought, because everything was perfect. GLX worked, dualscreen worked, i was one happy camper! ...  untill i rebooted my machine. Now, after the machine boots, and it starts X, it goes unresponsive. Im fairly new at linux but i take it thats a bad sign. Anyone else experienced such problems?
Im completley unable to interact with my linux now :(

---

### Post by dueY on 2006-01-24
By unresponsive do you mean it goes to a screen full of weird colors?

You can try pressing CTRL+ALT+F1 to get to command line and type ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by gullf1sk on 2006-01-24
Unresponsive as in, screen black, and the machine doesnt accept input from the keyboard at all. Nothing goes through.

---

### Post by gullf1sk on 2006-01-24
Noone knows what this could be?

---

### Post by gullf1sk on 2006-01-24
Guess i'll chuck it out and go on using Windows.

---

### Post by gullf1sk on 2006-01-25
On second thought, screw going back to Windows. IM NOT GIVING UP!

---

### Post by schdefan on 2006-01-25
Did you use a USB keyboard or mouse. Boot into recovery mode and post of
```
$ less /var/log/Xorg.0.log | grep EE
```

schdefan

---

### Post by gullf1sk on 2006-01-25
I got a USB mouse yeah.
I'll try that stuff you typed, thanks man, lets hope i can figure this out!

---

### Post by gullf1sk on 2006-01-25
root@ubuntu:~# less /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
root@ubuntu:~#

---

### Post by gullf1sk on 2006-01-25
Duude, after i went in to recovery-mode, wrote down that stuff and rebooted, X started normally :D
I have no idea what happened, but it works now :)
Thanks all that posted :)

---

