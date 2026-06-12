---
title: "how do I revert back to open source ati drivers?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by thegreenman on 2007-04-24
I have an ati card and installed the restricted drivers, how do I revert back?

---

### Post by thegreenman on 2007-04-24
bump plz

---

### Post by scxtt on 2007-04-24
did you install fglrx? ... on PClinuxOS i had the "ati" driver working fine w/ Beryl+AIGLX - then installed fglrx, Beryl would only work w/ Xgl so i wanted to go back ... wasn't as simple as changing "fglrx" to "ati" ... had to totally uninstall fglrx ...

---

### Post by Paul41 on 2007-04-24
You can edit the xorg.conf file to set it back. First make a backup of the file you have now just in case.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

Then open the file

```
gksudo gedit /etc/X11/xorg.conf
```

Under "Section "Device" change the driver to "versa"

If that doesn't work you can also run:

```
sudo dpkg-reconfigure xserver-xorg
```

and select the versa driver there.

---

### Post by thegreenman on 2007-04-24
many thanks. :)

---

### Post by thegreenman on 2007-04-24
okay that totally crashed my desktop. I had to load the backup to get back. 
is there something missing?  Do I have to uninstall the current driver first? 

Thanks for the help so far. I'll keep experimenting.

---

### Post by Paul41 on 2007-04-24
You won't need to uninstall the current driver. Try the sudo dpkg-reconfigure xserver-xorg method if you haven't already tried that.

---

### Post by scxtt on 2007-04-24
FWIW, i tried using X reconfigure tools to switch from fglrx to ati - DID NOT work ... HAD TO uninstall fglrx, which sucks, but had to be done to go back ...

---

### Post by thegreenman on 2007-04-25
Well,  when I did uninstall the restricted driver then re-tried your vesa selection method it DID work, all is now sweet again! I'm back in the saddle. 

**THANKS again everyone. **

---

