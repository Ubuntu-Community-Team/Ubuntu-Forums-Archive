---
title: "[SOLVED] Monitor not working after login"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by pacoramirez on 2008-02-04
I just started using another monitor (older), and after the login screen (Ubuntu 7.10) I see nothing. I can hear the login sound but the screen goes blank right after that? Why is this?

---

### Post by amingv on 2008-02-04
Probably your new (old) monitor can't handle the resolution/refresh rate from your old (new) one.

Just reconfigure X and set a more suitable resolution.

<edit=Instructions>
Press Ctrl+Alt+F1, it will switch you to a full shell mode, then type:

```
sudo dpkg-reconfigure xserver-xorg
```

It will ask you for some settings to reconfigure your display, then use Ctrl+Alt+F7 to go back to graphic mode and finally Ctrl+Alt+Backspace to restart X.
</edit>

---

### Post by oedha on 2008-02-04
but you can go to console mode :==> ctrl+alt+F
login and
sudo nano /etc/fstab
manually change the monitor resolution to..."800x600"
under monitor section
save it and then sudo /etc/init.d/gdm restart

---

### Post by oedha on 2008-02-04
sorry.....it supposed to be ctrl+alt+F2

---

### Post by pacoramirez on 2008-02-04
I wont be able to use the other monitor anymmore. But in the login screen I selected "Select session..." and selected "Failsafe terminal"  I typed what u said but then it asks for something and I dont know what to do then, hep!

---

### Post by oedha on 2008-02-04
but you can login right ?
what does it say.....

---

### Post by pacoramirez on 2008-02-05
If I login normal, it doesnt say anything. I can hear everything though. If I login in "Failsafe terminal" I get a terminal window then I press CTRL + ALT + F2, then I log in and I get this message about Ubuntu programs being free software.... NO WARRANTY..... blah,blah,blah then I typed what you said but I get nothing about monitor section

---

### Post by oedha on 2008-02-05
uppsss.....my very sorry
it supposed to be :==> sudo nano /etc/X11/xorg.conf
and look under the section "screen"
change it manually.....
save it and restart the gdm

sorry :)

---

### Post by pacoramirez on 2008-02-05
YES! It works, thank you my man for all of your help. I still have many issues but I will see if there are any other threads that could help me. Thanks a bunch.

---

### Post by oedha on 2008-02-05
you're welcome !
is this solved ? if yes...could you scroll up and click on thread tool and mark this thread as solved.......thank you

---

