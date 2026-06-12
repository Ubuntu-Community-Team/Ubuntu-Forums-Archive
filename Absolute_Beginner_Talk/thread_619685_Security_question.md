---
title: "Security question"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Splat! on 2007-11-21
I just ran GRC.com's ShieldsUp! against my machine
running Gutsy. In the ports vulnerability tests my
WinXP machine shows everything secure as "Stealth".
However, my U-machine shows "closed" status on
all ports tested and GRC says my machine "fails"
in this area of their testing.

Is this something I should be concerned about?

Is it possible to hide the ports? If so, how?

TIA - Splat!

He'p me! He'p me! The paranoids are after me!

---

### Post by shae on 2007-11-21
It should not be a problem, but if you feel paranoid, you should install firestarter (firewall).

---

### Post by overdrank on 2007-11-21
> **Splat! said:**
> I just ran GRC.com's ShieldsUp! against my machine
running Gutsy. In the ports vulnerability tests my
WinXP machine shows everything secure as "Stealth".
However, my U-machine shows "closed" status on
all ports tested and GRC says my machine "fails"
in this area of their testing.

Is this something I should be concerned about?

Is it possible to hide the ports? If so, how?

TIA - Splat!

He'p me! He'p me! The paranoids are after me!

HI this link may help
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by schorsch on 2007-11-21
"Closed" is better than "stealth" so you are on the safe side :-)

---

### Post by mikewhatever on 2007-11-21
Iptables, the built in firewall, does not seem to stealth the ports, as long as no ports are open, you are in no danger. The above mentioned firestarter is not a firewall, but rather is a gui for iptables and it does not have the stealth function.

---

### Post by Taboo Mirage on 2007-11-21
"Stealth" is a buzz-word that simply breaks common networking standards in that a reply isn't sent back in the event you transmit packets to a TCP port.

Actual security is better than security by obscurity.  "Closed" ports do not have daemons listening on them, therefore no connections can be received by those ports.  You are secure.

---

### Post by stunner on 2007-11-21
The whole 'stealth' thing arose as a tactic to hide from portscanners, but as others have said here, you're safe with 'closed' - someone may know that there is a machine at your ip address, but if you don't have any services running, they can't/shouldn't get in.

If it really bothers you, you can stick a NAT box between your comp and your internet connection.  Most that I've used result in 'stealth'.

To turn off services, go to System -> Administration -> Services and uncheck any http, ftp, file-sharing, ssh, and other network-based services.  Also, go to System -> Preferences -> Remote Desktop and uncheck "Allow other users to view your desktop".  Using firestarter is a good idea as well.

---

