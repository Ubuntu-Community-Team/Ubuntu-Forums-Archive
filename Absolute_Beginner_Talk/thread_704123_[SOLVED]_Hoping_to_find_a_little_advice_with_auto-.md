---
title: "[SOLVED] Hoping to find a little advice with auto-loading stuff every time I logon."
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by bmachia on 2008-02-22
I know there has to be multiple ways to accomplish this task, but whats the smartest way?

Every time I turn my Laptop, Reboot, or Logon, I need to two two things.  
1)Go into Terminal mode and type: modprobe ndiswrapper<CR>
2)Then start KNETWORKMANAGER to in order to establish a wireless connection to my network.

What's the best way to automate this for all users on this laptop?

Bill

---

### Post by lespaul_rentals on 2008-02-22
First off, you can make KNetworkManager start up automatically at login by the following steps:

Run KNetworkManager, then right click the tray icon.  Mouse over "Options," then click "Configure Autostart..."

If you want that shell script to run at bootup, make a file that says the following:

```
#!/usr/bin/bash
modprobe ndiswrapper


```

Save it as *<filename>.sh* then right-click it, select "Properties," and in the "Permissions" tab select "Make Executable."  Then, drop it in */home/<yourusername>/.kde/Autostart*.  If you are running Gnome just assume the ".kde" says ".gnome".

---

### Post by bmachia on 2008-02-22
That worked PERFECTLY.  Thank you very much

Bill

---

### Post by kpkeerthi on 2008-02-22
The right way to load modules is to add it to your **/etc/modules** file

---

### Post by justleen on 2008-02-22
the above would only work for the current user. to have this for all users, you could simply add a line to /etc/profile (the system wide.profile)...

for modules, you could offcourse add them to /etc/modules

And as a last option, you could write your own startup script in /etc/init.d (use one thats already there as a template)

---

