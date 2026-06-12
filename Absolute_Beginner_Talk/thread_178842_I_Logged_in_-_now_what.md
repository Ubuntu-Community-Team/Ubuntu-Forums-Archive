---
title: "I Logged in - now what?"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by PastorEric on 2006-05-18
Forgive me if this is answered somewhere obvious but I can't find it. I got a Ubuntu CD, looked at the live CD, thought that was cool, installed the install CD and now have been left at a screen prompt that says eric@childrensministries~$. What now? Did I do something wrong. The interface I saw on the first CD looked something like windows and I can deal with that. The interface I now have looks something like dos with an apparently all-powerful sudo command that I know nothing about.

---

### Post by Dr. Nick on 2006-05-18
login at the text and run thic command

startx

It will most likely give you an error, it should boot up into the gui if all was installed right.

If you get errors then rin
sudo  dpkg-reconfigure xserver-xorg

and try to reconfigure it. If you need help just post back

---

### Post by Klaidas on 2006-05-18
It looks like you have installed yourself a server :) That is, no desktop environment.
Try ```
sudo apt-get install ubuntu-desktop
```
Id you have a slow internet connection, I would recomment to reinstall from the cd.

---

### Post by PastorEric on 2006-05-18
Dr. Nick, startx didn't work and the stuff that showed up when I typed the next command was way beyong my understanding.

Klaidas, I typed your command and a bunch of stuff happened. When it stopped it told me Media Change: please insert the Cd but that didn't help it.

---

### Post by nalmeth on 2006-05-18
sudo apt-get update 
sudo apt-get uprade
sudo apt-get install ubuntu-desktop

If you've successfully installed ubuntu-desktop, and rebooting (sudo reboot) didn't give you a graphical interface, then the video driver isn't working.

With the "sudo dpkg-reconfigure xserver-xorg" you can be safe with picking basically the default's across the board. Except when picking the video driver, pick vesa rather than the default.

Unless you know better, the safe thing is to hit enter all the rest of the way through.

---

### Post by user1397 on 2006-05-18
when i accidentally uninstalled the ubuntu desktop, i did what nalmeth said and i was up and running again after a few minutes.  Good advice nalmeth ;)

---

### Post by Mustard on 2006-05-18
[QUOTE=nalmeth]sudo apt-get update 
sudo apt-get uprade
sudo apt-get install ubuntu-desktop
[/QUOTE]

You've got a typo in there.  Second line should read..

```
sudo apt-get upgrade
```


PastorEric, when you run sudo dpkg-reconfigure xserver-xorg, just choose the **default answers** that are already set up.  The only change you should make is when it comes to the display drivers question.  Choose the 'vesa' drivers, as suggested in a previous post.

Alternatively you can edit the file manually using this command...

```
sudo nano /etc/X11/xorg.conf
#this command will open the xorg.conf file
#with the command line text editor called nano
```

You would look through the file for the section that might look something like this...

```
Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        **Driver          "nvidia"**
        BusID           "PCI:1:0:0"

```

and the section in bold (which shows my nvidia drivers setup) would be changed to this below..

```
Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        **Driver          "vesa"**
        BusID           "PCI:1:0:0"

```

Pressing ctrl + o will save the file, and pressing ctrl + x will exit the nano text editor. From there you can try starting the xserver again..

```
startx
```

or alternatively..

```
sudo /etc/init.d/gdm start
```

---

