---
title: "[SOLVED] Firestarter - Doesn't open on StartUp"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by BOZG on 2007-10-04
I have to manually start Firestarter whenever I log on.  Any suggestions for auto-start?

---

### Post by PmDematagoda on 2007-10-04
You an just go to:- System>Preferences>Sessions and add it to the start-up programs, the command is gksu /usr/sbin/firestarter. But doing this means you have to enter the password on every log-in.

---

### Post by BOZG on 2007-10-04
Thanks.

---

### Post by frodon on 2007-10-04
There's no need to have firestarter GUI opened, your firewall is started on boot automatically, the firestarter frontend is useful only when you have you change the rules or wish to stop/restart the firewall.
Having the firestarter GUI always opened is a windows reflex, because on windows having the GUI opened means having the firewall running but on linux it is different because the firewall is integrated in the kernel so you don't need to open the GUI to have the firewall running, it is running by default.
If you want verify this by yourself, boot your computer, open a terminal then paste this command :
```
sudo /etc/init.d/firestarter status
```You will see that your firewall is already running.
Having the GUI opened all the time may decrease the global security of your system as you would only need to get remote control over the GUI to deactivate the firewall.

---

### Post by BOZG on 2007-10-04
Thanks a lot.  My instinct is to look for icons.

By the way, how do I get GAIM to autostart.  I tried using the same command replaced with GAIM but it still won't autostart.

---

### Post by Hospadar on 2007-10-04
> **BOZG said:**
> Thanks a lot.  My instinct is to look for icons.

By the way, how do I get GAIM to autostart.  I tried using the same command replaced with GAIM but it still won't autostart.

Did you put in "GAIM" or "gaim" for the command? it should be lower case, also you can right click the game launcher in the menu and go to properties and look at the launcher command and use that.

---

### Post by BOZG on 2007-10-04
I used lowercase and it wouldn't work.

I added it to session with just gaim as the command and no path and it works fine.  Thanks a lot.

---

