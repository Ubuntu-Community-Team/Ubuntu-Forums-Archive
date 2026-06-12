---
title: "computer wont turn off"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by nonewmsgs on 2007-02-27
my desktop computer's turn off menu no longer has restart or turn off just hibernate.  the hibernate is much less than ideal because it's right next to my bed and the case has many lights (even with the one switch to off), so i want it dark and thus off.

the darndest thing i thought i posted this but i searched and didnt see it.

---

### Post by rjfioravanti on 2007-02-27
from a terminal try typing this command

sudo shutdown --shutdown

---

### Post by overdrank on 2007-02-27
> **nonewmsgs said:**
> my desktop computer's turn off menu no longer has restart or turn off just hibernate.  the hibernate is much less than ideal because it's right next to my bed and the case has many lights (even with the one switch to off), so i want it dark and thus off.

the darndest thing i thought i posted this but i searched and didnt see it.

Have you tried the power button on the tower?

---

### Post by rjfioravanti on 2007-02-27
or maybe

sudo shutdown --poweroff

---

### Post by nick24 on 2007-02-27
Just unplug it

---

### Post by nonewmsgs on 2007-02-27
but can i get back the turn off button under the power button item in the system tray?

---

### Post by Meson on 2007-02-27
try "sudo init 1" to restart and hopefully alls well when you boot back up.  This happened to me once and it was gone after the restart

---

### Post by nonewmsgs on 2007-03-01
it's still not fixed.  could it be that i installed kde?  i still almost exclusively use gnome but the splash screen says kubuntu, and i can turn it off from the login screen.

---

### Post by Meson on 2007-03-01
You could create your own links to the shutdown command.

You could also right click the panel, goto add, and add the quit item.

I'm not sure how to edit the menu specifically.  I'm sure its in your home folder somewhere though.

---

### Post by dewcansam on 2008-02-05
You have probably messed with the shutdown settings try this:

Go to 'Control Center' > 'Login Manager' > 'Shutdown' tab
Login as administrator mode 
Then make sure that in the 'Allow Shutdown' area. In the 'Local' drop-down select 'Everybody' . Then hit 'OK'

edit:
You will also have to log-out of kde and restart X (Ctrl+Alt+Backspace) to get the changes to work 

Also the command in the 'Halt' text box should be '/sbin/poweroff' or you could use '/sbin/shutdown -h now'

---

### Post by kryth on 2008-02-05
It's linux. It's not like windows. You never 'HAVE TO' shutdown ubuntu. :)  j/k

---

### Post by steveguy on 2008-02-05
The clue is that it happened after you installed KDE on top of Gnome. When you install KDE, you get asked if you want to make kdm the display manager. After this, you can still start Gnome, but it has no shutdown button. But you can 'logout' and then shutdown from the kdm login screen. You will have a shutdon facility in KDE though!

---

