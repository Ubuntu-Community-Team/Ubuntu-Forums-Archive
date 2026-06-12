---
title: "Firestarter firewall"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by mikesmith36 on 2007-04-12
I have installed firestarter and configured it, in common with several users I cannot get it to run at boot, I have tried editing the /etc/sudoers file and adding firestarter to the start up programs but this seems to do nothing. I have now removed these entries.
I have setup firestarter using gksudo firestarter, but of course when I reboot the firestarter icon is gone.

Some posts say the firewall is running all the time and firestarter just makes changes - is this true??

Michael

---

### Post by oilchangeguy on 2007-04-12
it doesn't need to run at boot. firestarter is nothing but a control panel for the already built in firewall.

---

### Post by annda on 2007-04-12
> Some posts say the firewall is running all the time and firestarter just makes changes - is this true??

yes, it's true. the real firewall is iptables, firestarter is just a frontend that makes it possible to configure iptables via GUI.

---

### Post by Patrick K on 2007-04-12
That is true. Iptables, the default firewall is running all the time. Firestarter is a graphic frontend for it. As to if your setting stay between sessions, I can't say.

---

### Post by mikesmith36 on 2007-04-12
Thanks for the response - I'll just have to trust it's working!

---

### Post by milton1 on 2007-04-12
> **mikesmith36 said:**
> Some posts say the firewall is running all the time and firestarter just makes changes - is this true??

Yes. Firestarter is an app for managing your firewall. It really just edits your iptables for you in a nice friendly way. Your firewall settings should still be as you want them, even if firestarter is not running. However, if you really want to see that icon every time you run your machine, there are options in the firestarter settings menu to run on startup/login.

---

