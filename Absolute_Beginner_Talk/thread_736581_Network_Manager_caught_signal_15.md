---
title: "Network Manager caught signal 15"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Unstuck on 2008-03-26
Dell Inspiron 1420 shipped with Feisty preinstalled; recently updated to Gutsy.  Since the upgrade, I lose wireless at least once a day.  After losing the signal, the key manager pops up asking for the network password, the network manager tries to connect, you can see the icon “working” then it stops, and it is impossible to connect without rebooting.  When I reboot, I get this message
> NetworkManager: <WARN> nm_signal_handler ( ).  Caught signal 15, shutting down normally. at which point the reboot stops, and I finish the reboot by hitting CTRL+ALT+DEL.  After logging back in, everything works well...until the process repeats.  Any ideas?

---

### Post by Unstuck on 2008-03-27
bump

---

### Post by Unstuck on 2008-03-30
final bump...

---

### Post by gasull on 2008-05-27
This was happening to me.  It was due to overheat in the CPU.  Look for "signal 15" in /var/log/messages and /var/log/syslog.  And look for the lines just above.

---

