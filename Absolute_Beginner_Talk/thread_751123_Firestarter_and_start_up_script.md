---
title: "Firestarter and start up script"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Kenzo on 2008-04-10
During boot up of Ubuntu Firestarter is stopped and restarted several times.  Why is that?

---

### Post by Sam Lars on 2008-04-10
Firestarter, being the firewall, is restarted every time something is set up for the network during the boot.  You may be able to disable this through the preferences; there are soms settings for starting the firewall on dial out, etc.

---

### Post by takuhii on 2008-04-10
I was always under th eimpression Firestarter was just a GUI to configure IPTables, which is the real "firewall"

---

### Post by qamelian on 2008-04-10
> **takuhii said:**
> I was always under th eimpression Firestarter was just a GUI to configure IPTables, which is the real "firewall"
And your impression is correct.

---

### Post by bodhi.zazen on 2008-04-10
The linux firewall is iptables.

Iptables is a powerful tool, but unfortunately there is no gui to access all the features.

Firestarter is a gui tool that allows access to some of the most basic functions, but firestarter is not a firewall. Firestarter runs as root and is a security risk. So run it, configure iptables, and close it. Your firewall (iptables) remains configured and active, even on reboot, without firestarter running.

There are many tutorials suggesting you should run firestarter all the time. This is not needed and is a security risk.

Firestarter should NOT be used to monitor your network traffic.

---

### Post by Sam Lars on 2008-04-10
So I guess what it's doing is starting the iptables firewall with the Firestarter settings?

---

