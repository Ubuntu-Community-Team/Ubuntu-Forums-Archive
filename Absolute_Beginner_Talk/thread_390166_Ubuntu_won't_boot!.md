---
title: "Ubuntu won't boot!"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by .oops on 2007-03-21
Just like the title says. It just freezes at **Configuring Network Interfaces** on the graphical boot screen, then on a text screen. Can anyone help me out?

---

### Post by oilchangeguy on 2007-03-21
have you made any changes to your network hardware?

---

### Post by .oops on 2007-03-21
To the hardware, no. I just changed the settings at the Network Manager. :s Do I have to re-install?

---

### Post by fakie_flip on 2007-03-21
What changes did you make in the Network Manager?

---

### Post by oilchangeguy on 2007-03-21
do you know what you changed, so you can perhaps change it back?

---

### Post by .oops on 2007-03-21
I configured ra0, entered my ESSID (selected it from the drop-down) and activated it. Then I typed iwconfig to see if it was working (it wasn't, there wasn't even my ESSID there) and then I rebooted.

---

### Post by oilchangeguy on 2007-03-21
sounds like you'll need to boot into recovery mode. but i don't know what you'll need to type in the command prompt once you get there. why were you trying to make these changes anyway?

---

### Post by .oops on 2007-03-21
To get my wireless network working.

---

### Post by .oops on 2007-03-22
Any help on this? Do I really need to reinstall? :s

---

### Post by jkeyes0 on 2007-03-22
stupid question, but how long did you try waiting to see if it would boot? Sometimes, when I take my laptop to my parents' home (they have a wireless connection as well) it takes something like 5 minutes for the connection attempt to time out, before ubuntu will boot.

---

### Post by .oops on 2007-03-22
I didn't count how long, but it stood there for a while. Does the booter change to a text type page instead of the graphical booting screen while you're waiting?

---

### Post by jkeyes0 on 2007-03-22
No, mine stays at the graphical screen while I wait.

---

### Post by .oops on 2007-03-22
Mine doesn't... :( It just changes to a plain text screen, waiting for me to type something I suppose.

---

### Post by jkeyes0 on 2007-03-22
you could reboot, hit escape during the Grub stage 1.5 section, and choose the top "Recovery Mode" option (should be the second line). That will take you into a terminal where you can make changes to the system without loading everything up.

Once you're at that terminal, can you post the contents of your /etc/network/interfaces file?

---

### Post by .oops on 2007-03-22
How can I open it? I'm a newbie, so please, could you explain how can I open ~/interfaces from the recovery screen?

---

### Post by jkeyes0 on 2007-03-22
oh, sorry about that.

from a terminal screen, you'd have to use a text editor to view/edit the networking interfaces file, so from the terminal line, type in
```
nano /etc/network/interfaces
```

---

