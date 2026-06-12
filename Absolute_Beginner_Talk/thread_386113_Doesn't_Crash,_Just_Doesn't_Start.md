---
title: "Doesn't Crash, Just Doesn't Start"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by falciron on 2007-03-16
Here's the steps I've taken to set up my computer and get my screen resolution right:

1. Burned a good copy of the Edgy Eft .iso file to a cd.
2. Installed the OS with a good set of partitions. Worked perfectly.
3. Downloaded and installed all of the updates.
4. Restarted to completely install the updates.
5. Installed the ATI fglrx driver.
6. In the terminal, typed in sudo aticonfig --initial
7. Restarted to "allow the initialization to complete."
8. My computer gets to the loading screen where the bar fills up, then blacks out when it's done with that. The login screen is next, and I can tell this because of the kettle drum sound that occurs right after I type in my login correctly.

What do I need to do? My dad's computer uses the same graphics card as mine (an Integrated ATI Radeon Xpress 200) and that setup worked just fine for him: the graphical interface appears. We may have installed something else on his computer but can't remember.

Tell me if you need any other info.

---

### Post by jenhsun on 2007-03-16
Do you want to try this ?
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Stone123 on 2007-03-16
After 3 ubuntu editions i gave up on fglrx driver. IF you want screen back:
Try pressing Ctrl+Alt+F1, then login and type "sudo killall gdm"
OR:
Start ubuntu in rescue mode from grub

Then
type sudo dpkg-reconfigure xserver-xorg

Choose ati as driver . restart computer  or /etc/init.d/gdm start

 when you are done see that you find correct xorg.conf tweak for your card and read:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)


aticonfig doesn't allways work

good luck

---

### Post by falciron on 2007-03-16
Jenhsun, Envy caused the same problem when I tried it previously.

---

