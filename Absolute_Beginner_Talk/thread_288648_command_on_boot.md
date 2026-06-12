---
title: "command on boot"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by hnaamyilkemku on 2006-10-30
i am trying to get the following command to execute successfully everytime i boot (see [http://ubuntuforums.org/showthread.php?t=100169](http://ubuntuforums.org/showthread.php?t=100169) for the context of this command):

```
3ddesk --acquire=100
```

i edited crontab by running the command

```
sudo crontab -e
```

and inserted the following line

```
@reboot /usr/bin/3ddesk --acquire=100
```

this does not execute whenever i reboot, however, and i have to manually type 

```
3ddesk --acquire=100
```

to get it to work. what am i doing wrong? thanks in advance.

---

### Post by blind0wl on 2006-10-30
I dont think crontab is the best solution for you, a cron job is set to run at specific dates and times, not on startup.

If your running gnome, I'd recommend this posting:

> **andypaxo said:**
> You can start programs on login using gnome sessions.
Go to Desktop->Preferences->Sessions on the main menu, then click on the 'Startup Programs' tab.
Add any program you like here, and it will run as soon as you log in

HTH

Blindy

---

