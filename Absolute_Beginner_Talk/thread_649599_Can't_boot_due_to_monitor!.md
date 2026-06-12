---
title: "Can't boot due to monitor?!"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by stenella on 2007-12-25
In trying to correct the resolution of my HP monitor I went into the screns and graphics menu. Couldn't find my exact monitor so chose one with a similar resolution, restarted and got a message box telling me I need to restore the setting...then gave me a nice blue window with no options apart from closing down etc.. I-m now operating off the live CD, which gives me access to my regular installation of Ubuntu. Can anyone tell me how to restore the monitor settings from here, or will I have to reinstall Ubuntu?
Cheers!

---

### Post by lgambett on 2007-12-25
Do not use the live CD for this. Try first to access a terminal console; also if your graphical screen appears messed up you should be able to access a terminal console pressing Ctrl + Alt + F1.
Log into the terminal console and then reconfigure the X Server with;
*sudo dpkg-reconfigure xserver-xorg*
Once done reboot the PC et voilà.

---

### Post by stenella on 2007-12-25
Cheers!
I'll try it and let you know how I get on...

---

### Post by stenella on 2007-12-26
That was interesting. I can now boot up again, but only into Gnome Safe mode. I assume I missed, or did something while plowing through all the questions and blanks in the terminal.
Can anyone help with this?
Cheers.

---

