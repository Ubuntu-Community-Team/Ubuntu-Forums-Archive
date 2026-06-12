---
title: "[SOLVED] How to Reset Network manager"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by ThePinkWitch on 2008-02-05
I've been days trying to set up my wireless network and have had to reinstall Ubuntu 3 times because I can't figure out how to clean all info from Network manager and start afresh with Automatic not manual config. I keep messing with the settings and it won't let me wipe them.Anyone know how to do that so I don't have to reinstall Ubuntu for the FOURTH time lol Thanks :)

---

### Post by oedha on 2008-02-05
if you change the netwrok setting.....
you can open terminal and then type :==> sudo /etc/init.d/networking restart
it only restart the network service
in order to make your wirelees online...you have to know what is your wireless...and also check on system - administration - restricted drivers

---

### Post by ThePinkWitch on 2008-02-05
um...that didn't work, all the info is still in Network manager. I need to clear it all ..it keeps putting it back in. I can't reset it to have nothing in the settings.

---

### Post by ugm6hr on 2008-02-05
> **ThePinkWitch said:**
> I've been days trying to set up my wireless network and have had to reinstall Ubuntu 3 times because I can't figure out how to clean all info from Network manager and start afresh with Automatic not manual config. I keep messing with the settings and it won't let me wipe them.Anyone know how to do that so I don't have to reinstall Ubuntu for the FOURTH time lol Thanks :)

Are you talking about the "Network Settings" page?  Network Manager accesses this when you select *Manual configuration*.

If so - select the networking device (e.g. Wireless connection) and ensure the "Enable roaming" box is ticked.  This will return control to Network Manager (which uses "roaming" with DHCP as default.).

If that isn't the problem - use some screenshots to explain where the problem is - or describe the settings page you are using.

---

### Post by ThePinkWitch on 2008-02-05
I love you! If I wasn't old, fat and ugly I'd ask you to marry me. IT WORKS!!! OMG after messing around for 3 days it actually works. Whoohoo!!!!!! THANKYOU!!!!!! I have internet now :guitar::popcorn::lolflag:=D>

---

### Post by ugm6hr on 2008-02-05
> **ThePinkWitch said:**
> I love you! If I wasn't old, fat and ugly I'd ask you to marry me. IT WORKS!!! OMG after messing around for 3 days it actually works. Whoohoo!!!!!! THANKYOU!!!!!! I have internet now

Welcome to Ubuntu :)

---

### Post by ThePinkWitch on 2008-02-05
Thankyou very much :biggrin:

---

