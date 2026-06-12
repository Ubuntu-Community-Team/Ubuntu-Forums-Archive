---
title: "[SOLVED] Firestarter - Always On ??"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-02-25
Hiya

I just wanted to know if this was 'always on' by default ??

I usually use

System
Administration
Firestarter

to see the GUI and have the tray icon in my panel bar.

Is this necessary??

If it is off by default, how do I make it a service that is running all the time ?

Thanks :)

---

### Post by 23meg on 2007-02-25
You only need the Firestarter GUI to make changes to your settings. Firestarter is a frontend to iptables, which does the actual work of protecting you. You can exit it after making changes.

---

### Post by george29 on 2007-02-25
Firestarter is a graphically user interface for the linux firewall iptables. iptables is compiled into the linux kernel and is always on. firestarter allows you to configure iptables. your firewall should start immediately you boot into ubuntu.

---

### Post by chrome307 on 2007-02-25
Thanks Guys :)

---

### Post by Jimmy4eyes on 2007-02-28
Forgive me if this is a silly question, I've only just made the switch and am probably thinking in windows mode still. I installed Firestarter, an entry for it appears in applications/internet. When I click on it, I get something opening up with tabs for status, events and policy. I also get an icon in the top right hand corner, blue with a black arrow on it. When I close the box though, the icon also disappears. Does this mean the firewall has closed?

---

### Post by The Seeker on 2007-02-28
> **Jimmy4eyes said:**
> I also get an icon in the top right hand corner, blue with a black arrow on it. When I close the box though, the icon also disappears. Does this mean the firewall has closed?
Not at all. As others have stated, the icon that you mention is merely a graphical interface to [iptables](http://en.wikipedia.org/wiki/Iptables), allowing you to make changes as you see fit. Once you close the icon, your protection is still enabled.

---

### Post by orb9220 on 2007-02-28
No that means the gui firestarter closed not the firewall iptables.

---

### Post by Mumbo719 on 2007-02-28
I to came from Windows within the last 6 months and couldn't get over the Firestarter icon not being visible and understanding it was still running.

Here is a confirmation for you.

[www.hackerwatch.org/probe/]("www.hackerwatch.org/probe/")

The results will be the same when the icon is visible and not visible :popcorn:

---

### Post by steve.horsley on 2007-02-28
WARNING!

I understand that firestarter doesn't arrange fot the iptables filters to be automatically reinstated on rebootl - a freshly rebooted machine is wide open until you run firestarter again. 

Perhaps you should look at man iptables-save and iptables-restore. and somehow arrange for iptables-restore to run on reboot - perhaps add the command to /etc/rc.local.

---

### Post by Thaeos on 2007-02-28
That depends, as according to [this]("http://www.fs-security.com/docs/persistence.php") the firewall will be running all the time, even after a reboot - if you installed Firestarter from a binary package (e.g. if you installed it using synaptic).

---

### Post by szf on 2007-02-28
Indeed, iptables runs without a dependency on firestarter... now could someone please fill us in on how the notification icon can load at start-up?

I've tried *everything* I can think of to bring it back in Ubuntu (like it was in Fedora).

---

### Post by 23meg on 2007-02-28
[QUOTE=szf]now could someone please fill us in on how the notification icon can load at start-up.?[/QUOTE]

I recommend against this, but there you have it:

[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

---

### Post by 23meg on 2007-02-28
> **steve.horsley said:**
> WARNING!

I understand that firestarter doesn't arrange fot the iptables filters to be automatically reinstated on rebootl - a freshly rebooted machine is wide open until you run firestarter again. 

Perhaps you should look at man iptables-save and iptables-restore. and somehow arrange for iptables-restore to run on reboot - perhaps add the command to /etc/rc.local.

[http://www.fs-security.com/docs/persistence.php](http://www.fs-security.com/docs/persistence.php)

---

### Post by szf on 2007-02-28
> **23meg said:**
> I recommend against this, but there you have it:

[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

If [only]("http://ubuntuforums.org/showpost.php?p=1474916&postcount=5") [that ]("http://www.ubuntuforums.org/showpost.php?p=1586162&postcount=3") [worked]("http://www.ubuntuforums.org/showpost.php?p=2100188&postcount=7").

---

### Post by 23meg on 2007-02-28
> **szf said:**
> If [only]("http://ubuntuforums.org/showpost.php?p=1474916&postcount=5") [that ]("http://www.ubuntuforums.org/showpost.php?p=1586162&postcount=3") [worked]("http://www.ubuntuforums.org/showpost.php?p=2100188&postcount=7").

Just to rule it out: did you put your actual username instead of "username" there?

---

### Post by szf on 2007-02-28
> **23meg said:**
> Just to rule it out: did you put your actual username instead of "username" there? Oh, yes. This was a working implementation before I dropped Fedora...

---

### Post by 23meg on 2007-02-28
> **szf said:**
> Oh, yes. This was a working implementation before I dropped Fedora...

Sorry, I can't help you any further with it, since I don't use Firestarter like that, but a forum search may help; this gets asked often.

---

