---
title: "[SOLVED] Firestarter (firewall)"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-12-04
Is there a way to make firestarter boot automatically during start up? currently, I have to manually start the process....

---

### Post by Paqman on 2007-12-04
Firestarter isn't a firewall, it's a GUI for configuring the built-in firewall called iptables. You don't want to have it running all the time. Just run it, make your changes, then close it.

However, for reference, to start a program at login you can go to System > Administration > Sessions and add a new entry for the appropriate program.

---

### Post by PeterJS on 2007-12-04
Firestarter itself isn't actually the firewall. The firewall is Iptables and it automatically start early in the boot order so you don't have to worry about your system being protected once you configure the firewall. Firestarter is just a graphical tool for configuring and monitoring Iptables.

 Also unless you've installed network services like smb you really don't need a firewall. Ubuntu defaults to not running any programs that listen to the network. So unless you've installed something extra a fire wall isn't going to help to much, there's no point in protecting something that isn't there.

---

### Post by ericartman on 2007-12-04
Check here it has a great PDF for firestarter. 

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

Cart

---

### Post by fmbugdadi on 2007-12-04
Ok guys, thanks the info....

---

