---
title: "Keyboard shortcut for bringing up command line?"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by resander on 2007-07-12
I have installed 7.04, but the mouse is not working. It does not move and does not send clicks. This is on a a dual boot with Windows XP. Seems to be a mouse driver problem, because the mouse works for Windows XP, Linux Puppy and Ubuntu 6.06 LTS on the same PC (Pentium III 700MHz w 256RAM).

If/when a patch is available I would need to do something from the command line  (am a newbie, so don't know what yet). 

How can I bring up the command line when the mouse is not working?

---

### Post by sad_iq on 2007-07-12
Don't know of any shortcut...but you can press ALT+Ctrl(F1-F6) to get to a cli...and work from there...to return to the Gui press ALT+F7!!!

---

### Post by sad_iq on 2007-07-12
Ok...so let's try to get your mouse working...boot ubuntu LiveCd(the one that has a working mouse)..open the terminal...and type ```
nano /etc/X11/xorg.conf
``` Then scroll down and find this section: ```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection
```
Remember the  **Option "Device" "/dev/input/mice"**  and **Option "Protocol" "ImPS/2"**...yours should be different....write these values down...Next boot your Ubuntu installation, press ALT+Ctrl+F1, type 
 **sudo nano /etc/X11/xorg.conf** find the above section and replace the Option "Device" "/dev/input/mice" and Option "Protocol" "ImPS/2" with what you wrote down from the LiveCd session!!! Save(Ctrl+x..Enter)...Reboot...and hopefully it will work!!!

---

### Post by resander on 2007-07-12
Thanks for your suggestions.

I'll see what I can get when using the keyboard shortcuts you suggested.

I have tried the lIveCD, the alternate distribution, but the mouse does not work on any of these. This really looks like a mouse driver bug.

---

### Post by UnixAnt on 2007-07-12
I don't know of a key combination to bring up a terminal, but I do use a nifty program called Tilda.  Quite simply, Tilda brings up a drop-down terminal, similar to the console found in Quake (and other games).

Its actually quite useful:

[http://tilda.sourceforge.net/wiki/index.php/Screenshots]("http://tilda.sourceforge.net/wiki/index.php/Screenshots")

Failing that, you could always press CTRL + ALT + F2 to move to a CLI login.  From there you can get by quite happily without a mouse with such programs as w3m for web browsing, slrn for newsgroups, irssi for IRC, etc.  Or you could edit config files to try and get your mouse working I suppose.  Switch back to the main GUI with CTRL + ALT + F1

---

### Post by sad_iq on 2007-07-12
Then...what mouse do you have??? Ps2, Usb???
 > Seems to be a mouse driver problem, because the mouse works for Windows XP, Linux Puppy and Ubuntu 6.06 LTS on the same PC (Pentium III 700MHz w 256RAM).
 Then try what I suggested using puppy....or try downloading Knoppix (also a LiveCd...it has a really good hardware detection)...and if possible replace the mouse and see if anotherone works. Also your box isn't a laptop is it? Here is where you can download Knoppix: [http://www.knoppix.net/get.php](http://www.knoppix.net/get.php)

---

