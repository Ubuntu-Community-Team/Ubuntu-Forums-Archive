---
title: "[SOLVED] Shut Down Freezing Up"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by LeChacal on 2007-11-07
Since I upgraded to 7.10 if I click the power button in the corner to shut down or select Quit from the System menu everything freezes up, if I let the PC sit for a few minutes then the screen to select what you want to do comes up. You can still move the mouse but you can't click on anything, you can do a ctrl-alt-backspace and restart the x11 while it is frozen but that isn't always a helpful thing to do. If I hit ctrl-alt-F2 to drop to CLI the GUI disapres and I am stuck at a black screen with a blinking underscore nothing ever comes up, and hitting ctrl-alt-F7 doesn't bring me back I am stuck at this blank screen. Also hitting alt-F2 to run something doesn't work when it is frozen. I have a gDesklet that shows CPU load and that keeps moving while the PC is frozen but it doesn't go up really high or do anything strange it just bounce up and down around 0-2 which is like ideal for the PC. If you hit the shut down button at anytime it acts the same I have tried it  right after the PC has booted and everything is done loading, and it is the same. If I hit shut down and then cancel out and keep working then hit it later it comes up normally no freezing.  I have ignored the problem since I upgraded figuring that the problem would get solved by an update or something but that hasn't happened so now I am looking for help. Thank you.

---

### Post by P4man on 2007-11-08
Something you might want to try: rather using the gnome shutdown thing, open a console and type:
```
sudo reboot
```
then you have output and you may see where it is choking

---

### Post by LeChacal on 2007-11-08
That is why I was trying to switch to CLI before but I didn't know that I could do that from a normal terminal window. Tried it and it work, but you seemed to be talking of some kind of message output also and I didn't see anything, the screen flicker and with in a second it had switch to the Ubuntu splash for shut down. I will use this method for now but I am still looking for a way to fix the GUI because it is easier when it works. Thank You..

---

### Post by P4man on 2007-11-08
Sound like you are bitten by this bug:
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910)

---

### Post by LeChacal on 2007-11-09
Well the above mentioned bug is my problem for why I can't see tty1-6 (which I didn't know was another problem I had) and I have gone through some of fixes and they didn't help but that is also a different problem then what I am looking for help on in this post. So I am still looking for help with my shut down freezing problem.

---

### Post by matthewcraig on 2007-11-10
I have the exact same thing going on here, LeChacal.  Are you running the 64-bit install?  Just curious.  Send me a PM if you open a bug report on this issue: I will want to subscribe to it.

---

### Post by LeChacal on 2007-11-11
The solution can be found on this post:
[http://ubuntuforums.org/showthread.php?t=608361](http://ubuntuforums.org/showthread.php?t=608361)

---

