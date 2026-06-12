---
title: "XServer Problems Ubuntu and Beryl"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Joka999 on 2007-03-23
Right i installed Beryl on Ubtuntu 6.10 and now when i boot up my laptop it says about Xserver so i tried:
```
Sudo spkg-reconfigure xserver-xorg
```

Then i typed "GDM" and logged in then it didn't get past the screen where it loads up Ubuntu( Nautilus i think). So i don't know what else to do any help appreciated. Thanx

---

### Post by jbayone on 2007-03-23
What kind of card do you have?  And how did you install the drivers for it?

---

### Post by Joka999 on 2007-03-23
I have no idea, i installed Beryl and it worked fine until i restarted laptop

---

### Post by jbayone on 2007-03-23
well which driver are you choosing when you reconfigure x

---

### Post by Joka999 on 2007-03-23
VESA i think

---

### Post by pillu on 2007-03-23
After you get stuck on the gnome screen press Ctrl+Alt+F1. This will take you to a non graphics terminal tty1. Login using your username and passwd. The type the command
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
and then 
sudo nano /etc/X11/xorg.conf
```

the first command will make a backup copy and the second command will open the file in a text editor. Now go to the section "Device". It will look something like
```
Section "Device"
        Identifier      "Generic Video Card" # this needs to match down below
        Driver          "i810" # works for this chipset, check with what you are using
        BusID           "PCI:0:2:0" # this should be set automatically
EndSection
```

Could you note down the contents of Identifier and Driver sections and post them here plz

---

### Post by Joka999 on 2007-03-23
Ok i'll do that now thanx for your reply and jbayone

---

### Post by Joka999 on 2007-03-23
Right i put ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` and it said "No command found"

---

### Post by Joka999 on 2007-03-23
Someone help please

---

### Post by macogw on 2007-03-23
No command found?  For cp?  Did you put a space somewhere extra that you shouldn't have maybe?

This belongs in Ubuntu Forums > Ubuntu Release Assistance  > Main Support Categories > Desktop Effects & Customization

---

### Post by Joka999 on 2007-03-24
Right i looked back at the command and tried again, here's what i got

Identifier: Generic Video Card
Drive: Vesa
Bus ID: PCI : 0:2:0

---

### Post by Joka999 on 2007-03-24
Any help?

---

### Post by Joka999 on 2007-03-25
No help then

---

### Post by pillu on 2007-03-25
If you think it is your x windows that is broke(and i don't know if it is) then the command to reconfigure is is
```
sudo dpkg-reconfigure xserver-xorg
```

On doing this you will get a bunch of questions about your video card and monitor. (Get as much info about your laptop as you can beforehand). Answer them and restart the computer and see if you can login now. I don't know much about this stuff and I just got out of tough beryl problem myself. Hope this helps.

---

### Post by Joka999 on 2007-03-26
I've tried reconfiguring it but it's still the same

---

