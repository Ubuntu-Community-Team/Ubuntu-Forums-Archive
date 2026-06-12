---
title: "run command on startup"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by wookaru on 2007-06-13
I searched for this, but everything I found was a bit over my head...

I want to know, in general, what script to edit to run commands after a user logs in.  I'm trying to run the command to start synergy on user login: /usr/bin/synergys --config /etc/synergy.conf 

I tried editing the file /etc/X11/gdm/PostLogin/Default - but that didn't seem to work.  I was able to get it to run going to system->preferences->sessions and adding that command as a startup, but I want to know how to get the same behavior through editing scripts.

---

### Post by gerscht on 2007-06-13
~/.gnome2/session seems to be the file to edit 
add
```

[NUMBER],RestartCommand=/usr/bin/synergys --config /etc/synergy.conf 

```
Replace NUMBER against the number in order you want to start this

---

### Post by rfurman24 on 2007-06-13
I think there is a section in session manager that will allow you to start apps and login.

---

### Post by lazyart on 2007-06-13
> **rfurman24 said:**
> I think there is a section in session manager that will allow you to start apps and login.

Yes, in System>Preferences>Sessions

---

### Post by sisco311 on 2007-06-13
> I was able to get it to run going to system->preferences->sessions and adding that command as a startup, but I want to know how to get the same behavior through editing scripts.

to get the same behavior you must create (edit) a .desktop file in the /home/**your_user_name**/.config/autostart directory

```
gedit /home/**your_user_name**/.config/autostart/**new_startup_command.desktop**
```

copy and paste something like this:
> [Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=*new_synergys*
Exec=/usr/bin/synergys --config /etc/synergy.conf 
X-GNOME-Autostart-enabled=true


save and exit (Ctrl+s, Alt+F4)

now you have a new entry in System->Preferences->Sessions (*new_synergys*)

---

### Post by terabite on 2007-06-13
Well... for noobs... theres always bootup manager (BUM)...
Its availlable ubuntu repos..

---

