---
title: "Dapper Power Manager Warning"
date: 2006-06-02
forum: Bug Reports / Support
---

### Post by jblaty on 2006-06-02
I upgraded Breezy to Dapper, yesterday, using apt-get.  Everything seemed to work fine.

One bothersome quirk is that I'm now getting a warning dialog box every time I log into my system using the NX client (it doesn't appear when logging in at the console, as much as I've seen):

"Warning
This program canot start until you start the dbus session service.

This is usually started automatically in X or gnome startup when you start a new session."

I hit the "Close" button, and all appears to be fine.

Oh, one other annoyance -- the File Browser starts every time I log on -- either at the console or via NX.

Any ideas?

---

### Post by karthik085 on 2006-06-02
[QUOTE=jblaty]I upgraded Breezy to Dapper, yesterday, using apt-get.  Everything seemed to work fine.

One bothersome quirk is that I'm now getting a warning dialog box every time I log into my system using the NX client (it doesn't appear when logging in at the console, as much as I've seen):

"Warning
This program canot start until you start the dbus session service.

This is usually started automatically in X or gnome startup when you start a new session."

I hit the "Close" button, and all appears to be fine.

Oh, one other annoyance -- the File Browser starts every time I log on -- either at the console or via NX.

Any ideas?[/QUOTE]
For file browser to not start up every time you log on, comment out similar following lines in .gnome2/session
4,id=default4
4,Priority=10
4,RestartCommand=nautilus --no-default-window --sm-client-id default4

---

### Post by jblaty on 2006-06-08
Thanks, the file browser stopped popping up, but that got rid of my desktop background. :( 

Also, no response on the warning popup?  Anybody?

---

### Post by Getwild2 on 2006-06-08
[QUOTE=jblaty]Thanks, the file browser stopped popping up, but that got rid of my desktop background. :( 

Also, no response on the warning popup?  Anybody?[/QUOTE]
I'm watching this thread as I have the same problem.  

Someone told me to update to the latest NVidia drivers and it'll fix the problem, I did so and the problem went away...for the most part.  Right now I ONLY get the error when I log in remotely via FreeNX.  When I boot/log in at home I do not get the error.  

See my thread on this subject here: [http://www.ubuntuforums.org/showthread.php?t=189753](http://www.ubuntuforums.org/showthread.php?t=189753)

---

### Post by jblaty on 2006-06-08
Thanks.  I updated the nVidia driver, and still have the same issue.  Generally, I only log onto this box via FreeNX, as it's "headless" on my network.

---

### Post by jblaty on 2006-06-19
Any update on this issue?  Has anyone isolated why this is happening on FreeNX?

---

### Post by Getwild2 on 2006-06-22
[QUOTE=jblaty]Any update on this issue?  Has anyone isolated why this is happening on FreeNX?[/QUOTE]
Not that I know of.

---

