---
title: "GKrellM Auto-start"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by dgifford on 2006-08-01
How do I set GkrellM to auto-start (Ubuntu 6.0.6)?

The menu on GKrellM has no options for this.

---

### Post by da1nonlymikeo on 2006-08-01
system>prefs>sessions>startup programs. 

 add this line.

 /usr/bin/gkrellm

---

### Post by dgifford on 2006-08-01
DOH!  Thanks!  that'll do it!

---

### Post by mohdridha on 2006-12-31
How to do that using CLI (not from X)?
THanks :-k

---

### Post by taurus on 2006-12-31
Are you talking about a console?

---

### Post by mohdridha on 2006-12-31
Yes Taurus,

Using console...:p

---

### Post by taurus on 2006-12-31
Gkrellm is a X program so you need to have X running first before you can use it.  I don't think you can run gkrellm in a console...

---

### Post by mohdridha on 2006-12-31
What i mean there must be somewhere in the Ubuntu filesystems that we can add/edit the startup programs files from terminal. 

These are my finding on other forum:

[li]edit their xinitrc files[/li]
[li]To start gkrellm automatically when you log into fluxbox you need to edit/create the ~/.xsession file (assuming that you login with xdm or gdm).

First check the X11 configuration in /etc/X11, look for a file called config or (on my debian sid system) Xsession.options. [/li]

They are all not using GNOME, so I think i cant do the same.

---

### Post by taurus on 2006-12-31
For fluxbox, add this line to ~/.fluxbox/startup...

```
gkrellm &
```

---

### Post by mohdridha on 2006-12-31
pssstt.. I'm using GNOME :D

---

### Post by taurus on 2006-12-31
> **mohdridha said:**
> pssstt.. I'm using GNOME :D

System -> Preferences -> Sessions -> Startup Programs -> Add.  

Then, just type gkrellm and save it.  Log out and back in again!!!

---

### Post by mohdridha on 2006-12-31
heheheh i found it..

~/.config/autostart

[email]kapla@mrn:~/.conf[/email]ig/autostart$ cat gkrellm.desktop
[Desktop Entry]
Name=No name
Encoding=UTF-8
Version=1.0
Exec=/usr/bin/gkrellm
X-GNOME-Autostart-enabled=true

and yes its easier to go to Systems>Sessions>Startup Programs to edit that..
phew.. Sorry

---

