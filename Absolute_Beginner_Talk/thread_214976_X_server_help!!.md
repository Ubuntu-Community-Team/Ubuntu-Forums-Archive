---
title: "X server help!!"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by csk on 2006-07-13
hi all

i was reading the help file which comes standard with ubuntu and i found out that my 3D driver was not detected. following the instructions i did: -

sudo apt-get install xorg-driver-fglrx
sudo dpkg -reconfigure xserver-xorg

after asking me a series of questions i was told to restart the computer. when i did i got 

"Failed to stqart the Xserver (your graphical interface). It is likely that is is not set up correctly. Would you like to view Xserver output to diagnose the problem"

when i say yes i get in summary

"No devices detected
Fatal server error

no screen found f"  
in addtion it asks wheither i want to see the "detailed out server output as well"
and does a whole lot of output 

anyone know how to fix this? i just want to know how to revert it back to the original way. i tried uninstalling the pacakage i installed but that didnt get me anywhere

someone please help
csk

---

### Post by taurus on 2006-07-13
Look in /etc/X11/ to see if the system made a backup copy of your xorg.conf before it overwrote it with the new one!  If you are not sure what to look for, just paste the output of this command, from a terminal, here then.

```

ls -la /etc/X11

```

---

### Post by Paerez on 2006-07-13
you need to edit "/etc/X11/xorg.conf"

to edit on the command line use:
```
# sudo nano -w /etc/X11/xorg.conf
```

find the line that says:
```
Driver "fglrx"
```
and change to:
```
Driver "ati"
```
then run:
```
# sudo /etc/init.d/gdm restart
```

---

### Post by csk on 2006-07-13
thanks
i think i got it working
csk

---

