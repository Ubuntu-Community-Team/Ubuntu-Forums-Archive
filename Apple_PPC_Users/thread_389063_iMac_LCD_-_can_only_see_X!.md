---
title: "iMac LCD - can only see X!"
date: 2007-03-20
forum: Apple PPC Users
---

### Post by Ububurns on 2007-03-20
Hi,

Switching to any terminal consoles (ie: <Ctrl> <Alt> <F1>) just gives me a blank black screen.

This means that if Xorg stops working, there's no way I can fix it!

Obviously xorg.conf controls X, which is working fine.  What file controls just plain output?

---

### Post by grazie on 2007-03-20
You can use ctrl+alt+{f1 to f6} as virtual terminals. To return to X use ctrl+alt+f7.

Do you have
```
Option "UseFBDev" "true"
```
in Section "Device" of your /etc/X11/xorg.conf?

---

### Post by the answer is 42 on 2007-03-20
If it is a G3 CRT IMac, then you can do this:

Ctrl alt f1 to a terminal
sudo su to get root prompt
run nano /etc/X11/xorg.conf
move down to the load dri and put a # in front of it
move down until you see monitor section:
Change the 
HorizSync to 60-60 and the VertRefresh to 75-117

then hit ctrl o to save the file ctrl x to get out of it.
Then kill gdm by running killall -HUP gdm.
It should work then.

---

### Post by Ububurns on 2007-03-21
As stated in the problem, no, I can't use Ctrl-Alt-(F1-F7) as terminals.  Text mode doesn't work!

Only graphical (X) mode works. *ONLY* graphical mode.

Thus changing anything in xorg.conf isn't going to fix my problem - it's something other than that!

(Thankyou for replying, anyway!)


If it's any help, it's a G4 iMac (one with the floating LCD monitor).

---

### Post by grazie on 2007-03-21
Ububurns,

I fully understand your problem and even though I don't know what the solution is, I can make suggestions. A combination of drivers and Xorg config is what makes the virtual terminals work. So having a correctly set up xorg.conf does affect virtual terminals. You have not stated whether you can successfully boot the OS without X which can be achieved using 
```
boot: Linux single
```

---

### Post by Ububurns on 2007-05-01
They must have changed something - Feisty works perfectly fine.

I even get a loading screen now!

Thankyou all for your help - I wish I could find out what the difference was...

---

