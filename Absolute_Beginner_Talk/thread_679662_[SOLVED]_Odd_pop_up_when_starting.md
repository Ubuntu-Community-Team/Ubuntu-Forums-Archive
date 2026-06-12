---
title: "[SOLVED] Odd pop up when starting"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by blueridgedog on 2008-01-27
When starting X, the attached image comes up every time.  The tag line is "The X system keyboard settings differ from your current GNOME keyboard settings".  Clicking wither option still results in it appearing on next boot.

---

### Post by Kilz on 2008-01-27
Please go to  System >Preferences >Keyboard > Layouts tab
What does Keyboard model: say?

---

### Post by jan quark on 2008-01-27
I have exaaaaaactly the same problem

my story:

I just wanted to install compiz to see if it works. I am not that fond of eye candy but was just curious if it works in the first place
everything worked fine, I had to install xserver-xgl to start the x-session, ok no problem 
the next time I started linux, I changed the session to run xclient scrpt and the compiz effects worked,

then I uninstalled xserver-xgl, restarted changed the session back to gnome and there I have this pop up, 
it is not a very dangerous or critical thing but annoying
see the pics for my keyboard layout
I use a German keyboard by the way

---

### Post by blueridgedog on 2008-01-27
model is Generic 105-key (Intl) PC

Layout is U.S. English, but "default" is not checked.

I will check it and see if that changes anything.

---

### Post by blueridgedog on 2008-01-27
More information:

Now that I look at the error, it reminds me that I originally installed Ubuntu and used it for a while with a PC101 keyboard, but switched to a PC105 keyboard.  Gnome sees the PC105 keyboard, and xorg.conf has the correct information: 

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

So, I am stumped as to where the old keyboard setting still resides.

---

### Post by Kilz on 2008-01-27
> **blueridgedog said:**
> More information:

Now that I look at the error, it reminds me that I originally installed Ubuntu and used it for a while with a PC101 keyboard, but switched to a PC105 keyboard.  Gnome sees the PC105 keyboard, and xorg.conf has the correct information: 

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

So, I am stumped as to where the old keyboard setting still resides.

It is in your xorg.conf file in /etc/X11, other than that I dont know.

---

### Post by blueridgedog on 2008-01-27
The only place I can find that still points to the pc101 keyboard is:

```
root@ripstop:/etc/X11# grep pc101 /home/james/.gconf -R
/home/james/.gconf/desktop/gnome/peripherals/keyboard/kbd.sysbackup/%gconf.xml:                <stringvalue>pc101</stringvalue>
```

---

### Post by blueridgedog on 2008-01-27
Editing /home/james/.gconf/desktop/gnome/peripherals/keyboard/kbd.sysbackup/%gconf.xml

and replacing the 101 with a 105 solved the problem (at least after a reboot)

---

