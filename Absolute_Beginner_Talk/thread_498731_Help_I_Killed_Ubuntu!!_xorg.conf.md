---
title: "Help I Killed Ubuntu!! xorg.conf"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by FNDII on 2007-07-11
As World of Warcraft continues not to work fix after fix, scroll further and further down the help file. Well trying the fixes I can now boot up the game. It now crashes as soon as you enter the world, cant even take one step.

This is that latest fix i tried and now Ubuntu won't load up.


#

For users with an ATI video card: certain cards have trouble rendering games and video in opengl using current flgrx drivers which will cause your computer to hard locks when you attempt to enter a domain. This error will occur just after character creation/selection, as the game environment is loading, or possibly after a short period of play. In order to fix this error, add the following three lines of code to your xorg.conf file in the ATI device section:

 Option "Capabilities" "0x00000800"
 Option "UseFastTLS" "off"
 Option "KernelModuleParm" "locked-userpages=0"

You edit the file by doing this command:

 gksudo gedit /etc/X11/xorg.conf

The section should look something similar to this after editing:

 Section "Device"
   Identifier  "aticonfig-Device[0]"
   Driver      "fglrx"
   Option       "Capabilities" "0x00000800"
   Option       "UseFastTLS" "off"
   Option       "KernelModuleParm" "locked-userpages=0"
 EndSection

---

### Post by pizzutz on 2007-07-11
assuming it dumps you to a command prompt like it should, you just need to restore your backup xorg.con (you made a backup right?)  if not you can use a command line text editor to manually remove those lines.

sudo nano /etc/X11/xorg.conf

---

### Post by FNDII on 2007-07-11
No I did not make a backup :(

The only time I can get to the prompt is if I enter in Generic mode. 

Can i enter the command line you gave to fix my problem in generic mode?

---

### Post by FNDII on 2007-07-11
Ok i went to generic mode and put that linr in there and it opend up some sort of editor but the file was blank?

I am going to need to be walked through replacig the xorg.conf

---

### Post by yabbadabbadont on 2007-07-11
At the text console, try running ```
sudo dpkg-reconfigure -p high xserver-xorg
```  I think that should recreate the default xorg.conf file like you had right after install.

---

### Post by FNDII on 2007-07-11
That worked great!!

Good thing I had my ATI x800 fix handy.


Thx again

---

### Post by djspanky on 2007-07-14
That fixed it for me to. Thanks!

---

