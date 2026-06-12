---
title: "Startup programs reset?"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by daxLeet on 2006-11-05
When I go to SYSTEM>PREFERENCES>Sessions, and add some programs to the 'Default' session and then X out and re-open, the programs are no longer there.  Thus, the programs I add don't load on startup.

I checked 'automatically save changes', yet it still will not work.  I am using Edgy Eft.

Thanks!
-Dax

---

### Post by MasterOfDisaster on 2006-11-05
I have this problem also, but typically only occurs with compiz-tray-icon...

Bummer having to launch it every login.

---

### Post by daxLeet on 2006-11-05
Yeah I have to launch beryl + emerald every time I log in, other wise theres no title bar on any of my windows :(

---

### Post by anandi on 2006-11-08
I have the same issue. This happens no matter what startup program i add to the list, it just keeps disappearing again and again.

It seems the startup programs are stored in /etc/xdg/autostart, and i don't see the entries for new programs being created in that directory. Permissions issue ??

I created a file in the above directory to run conky and after reboot, i see conky running. However it should work from inside the UI itself.

---

### Post by matt221984 on 2006-11-15
I am having this same problem. I just ended up right clicking on the desktop and then selecting create launcher. I created the launcher for my script that I wanted to run at login, then I used the terminal to copy it into the /etc/xdg/autostart folder.

kind of a hackish workaround, but its doing the trick for me.

---

