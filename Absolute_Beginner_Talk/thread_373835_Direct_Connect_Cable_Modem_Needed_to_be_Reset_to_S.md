---
title: "Direct Connect Cable Modem Needed to be Reset to See New NIC"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by rada on 2007-03-01
Just couldn't get my new ubuntu host to connect to the Internet through my (nearly new) Comcast cable modem. Been searching all over this forum and google.com/linux and reconfiguring networking like crazy. Nah... didn't need to. Setting DHCP and enabling the NIC was all that was needed in ubuntu. The problem was:

> **Gerard Barberi said:**
> 
Some modems bind themselves to the mac address of the device that is attached to them.  So when changing the device, you need to reset the modem, so that it will rebind to a new device.
 [http://ubuntuforums.org/showthread.php?t=371284](http://ubuntuforums.org/showthread.php?t=371284)

Even though all the command line diagnostics and sudo'ing were painfully unnecessary today, I earned an awful lot of good stuff along the way. It'll come in handy soon enough.  Thanks to all of you. What a community! :)

For real overkill, but totally step by step instructions to reset such modems see the ff. webpage. (I only had to cycle power on my cable modem, not the new ubuntu machine.):

[http://www.linuxquestions.org/questions/showthread.php?t=242394](http://www.linuxquestions.org/questions/showthread.php?t=242394)

---

