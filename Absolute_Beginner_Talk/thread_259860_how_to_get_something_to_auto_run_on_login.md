---
title: "how to get something to auto run on login?"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by spasmoid on 2006-09-18
I guess I'm looking for the equivilent of the windows StartUp group.

I want to run a shell script when the user logs into his desktop.

Thanks for any help.

---

### Post by jordanmthomas on 2006-09-18
For Gnome logins only...System --> Preferences --> Session
In the startup tab, add a new one
```
sh script.sh
```
or however you need to run it.
If you want to run it every time a user logs on period, put it in that user's ~/.bashrc

---

### Post by hearnden on 2006-09-18
> **jordanmthomas said:**
> For Gnome logins only...System --> Preferences --> Session
In the startup tab, add a new one
```
sh script.sh
```
or however you need to run it.
If you want to run it every time a user logs on period, put it in that user's ~/.bashrc

Won't ~/.bashrc run only every time they open a terminal, not on login?

If you want to start applications, then use that Session menu from the previous post.  If you want to start applications on particular virtual desktops (e.g. email on desktop 1, browsing on desktop 2, editing on desktop 3, ...) then that's harder, as you can't specify a desktop when launching an application.  You could try devilspie, which worked in Breezy, I'm not sure about dapper.

If you want to set environment variables, then you can try /etc/environment.

I think there are also desktop manager-specific places for startup things too (gdm/xdm).  The reason there's not one universal place for startup scripts is that there are many different types of startup (default, safe, recovery, ...).

---

### Post by andb on 2006-09-18
It is possible to set which desktop to start to, even window geometry & state with devlispie in dapper. Works great. More info at [http://wiki.foosel.net/linux/devilspie](http://wiki.foosel.net/linux/devilspie)

---

### Post by spasmoid on 2006-09-18
The session panel was the perfect solution.

Thanks.

I just wanted compiz to start.

Your help is much appreciated.

---

