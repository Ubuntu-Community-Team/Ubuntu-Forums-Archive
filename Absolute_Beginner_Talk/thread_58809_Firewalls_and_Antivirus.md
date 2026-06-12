---
title: "Firewalls and Antivirus"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by alquimista on 2005-08-21
Hi,
I'm comming from WinXP world and now I'm a happy Kubuntu user; now about 80% of the time I stay in Kubuntu. I know that in Linux therer are less virus treath arround. Yet, would it be necessary to install an antivirus or personal firewall? I have Kubuntu on a Toshiba notebook.

Thanx!
Guillermo

---

### Post by RastaMahata on 2005-08-21
[QUOTE=alquimista]Hi,
I'm comming from WinXP world and now I'm a happy Kubuntu user; now about 80% of the time I stay in Kubuntu. I know that in Linux therer are less virus treath arround. Yet, would it be necessary to install an antivirus or personal firewall? I have Kubuntu on a Toshiba notebook.

Thanx!
Guillermo[/QUOTE]
 There are no viruses in linux, so you dont need an antivirus.
You could install a firewall though: [Firestarter](http://www.ubuntuguide.org/#firestarter)

---

### Post by weasel fierce on 2005-08-21
Not quite true that you dont need antivirus. If you receive infected files, and send them to someone else, they can still be affected.

---

### Post by sapo on 2005-08-21
[QUOTE=weasel fierce]Not quite true that you dont need antivirus. If you receive infected files, and send them to someone else, they can still be affected.[/QUOTE]

Thats their fault for using windows without anti-virus.. not yours... shame on them :p

---

### Post by Kvark on 2005-08-21
Do some online port scans/firewall tests (most security companies got these tests on their websites) on ubuntu without a firewall, all ports are closed so it is impossible for intruders from the outside to connect to your computer.

The network manager sucks though and doesn't allow you to monitor and manage your own programs' network access and bandwith priority (like the system manager does with proccesses and CPU/memory usage) so you might want to get something for that task.

---

### Post by DJ_Max on 2005-08-21
[QUOTE=weasel fierce]Not quite true that you dont need antivirus. If you receive infected files, and send them to someone else, they can still be affected.[/QUOTE]
This is the case when you are running a mail server for mail transfer such as Postfix, Sendmail, etc.. These are used for webservers, not for desktops. Then you would use something like ClamAV.

Otherwise, don't worry about having any anti-virus software. If you want to interface you're built-in firewall, use Firestarter.

---

