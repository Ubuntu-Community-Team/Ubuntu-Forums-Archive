---
title: "Run a newly installed program in xubuntu?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by The Anomaly on 2007-02-01
Greetings,

I know this is about the lowest level of Ubuntu related question that there is, but I really wanted to get my wireless working. So, I installed kwifimanager with the add/remove program and now I jsut don't know how to run it! I mean, I have it installed, but it's not in the menus. In FC6 I'd just write in the terminal "kwifimanager" and it'd run....but for some reason that doesn't work here! How do I run the program I just installed?

btw, I'm using xubuntu, not Ubuntu.


Thank you for your help,
The Anomaly.

---

### Post by 3rdalbum on 2007-02-01
Go into Synaptic Package Manager, and look up "kwifi". Select the entry that appears, click on Properties, and go over to the Installed Files tab. You'll probably see some entries under /usr/bin; these will be the package's executables which you can run the usual way.

---

### Post by muguwmp67 on 2007-02-01
You can probably type "kwifimanager" into a command line to run it.  If not find the executable as explained above and run it from the directory its in.  It might need root privileges, so you might need to do 'sudo kwifimanager'

You can add it to the applications menu with Settings->Menu Editor in Xubuntu.

Oops, I forgot.  Synaptic isn't installed in Xubuntu by default.  To use it, install synaptic package manager from the add/remove programs app.  You'll want to do this regardless actually, because its much better than the Xubuntu app installer.

---

### Post by The Anomaly on 2007-02-01
Ah, thank you. That does the trick. I know this is not in the right topic, but while I'm talking about installing things...how do I install .gz files? I mean, I want to put this theme on Xubuntu, but I don't know how to install it.

---

### Post by ashmew2 on 2007-02-01
DO give this link a shot : [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
Im pretty sure itll help u

---

### Post by maxamillion on 2007-02-01
With all due respect, I beg of you to remove that package and all of its dependencies because every time you run the application to manage your wireless internet it will load kde-libs and qt which will slaughter your ram and system resources while running xubuntu. I recommend wifi-radar (it needs a little help for WPA, but its a wonderful app and much lighter on your system).

---

