---
title: "Lenovo T60 Screen problems"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by BigFlatBrook on 2008-02-28
I have a Lenovo T60 with an ATI X1400 graphics card.

When originally installing Ubuntu, the screen resolution was fine, although I can't remember what it was.

However, in trying to get the Laptop to display reasonably on an external monitor, I attempted to change the screen resolution by going through System->Administration->Screens and Graphics.  

Somehow I reset the resolution to 640X480 and now that's the highest resolution allowed in the Screens and Graphics Panel. 

What can I do to get the resolution set to a reasonable level?  I really don't want to install ubuntu over what I have.

If this is the wrong forum for this question, please tell me the right forum?

Thanks!

---

### Post by BigFlatBrook on 2008-02-28
Sorry about the double post.  But now when rebooting the laptop, I get the message "The Greeter Application is crashing.  Trying a different application."  or something like that.

After clicking the OK button, nothing comes up.  

So without some help, I'm stuck.

---

### Post by Rocket2DMn on 2008-02-28
Try reconfiguring X (the GUI) - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
(The automatic way might work for you, too, rather than doing it manually.
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart X with CTRL+ALT+BACKSPACE)
This should fix your resolution problem, and hopefully the greeter app problem, too.  Do the reconfiguration without the external monitor plugged in so you can get back to square 1.

---

### Post by BigFlatBrook on 2008-02-28
Unfortunately, this procedure did not restore the original resolution I had.  It did bump it up to 800X600.  On rebooting I get a message saying that the screen and graphics card could not be detected, and that it's running in low graphics mode.

Would this be because I answered some of the questions wrong?

---

### Post by Rocket2DMn on 2008-02-28
Perhaps, but you will probably also want to enable the Restricted ATI drivers for your card - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Give that a try, and if you have to reconfigure X again, select the "fglrx" (proprietary/restricted) drivers rather than "ati" (open source).

---

### Post by BigFlatBrook on 2008-02-28
That seems to have worked!  I did need to run through the configuration process again.  Curiously, it seemed to go off into never-never land trying to detect the screen.  After growing impatient, I rebooted and, amazingly, it came up in the former resolution (1400 X 1059.  So I assume this is ok.  

I guess the thing to do now is backup xorg.conf in case I get into trouble again.

---

