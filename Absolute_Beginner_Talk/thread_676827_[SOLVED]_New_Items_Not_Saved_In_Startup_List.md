---
title: "[SOLVED] New Items Not Saved In Startup List"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by satman-ga on 2008-01-24
I am trying to have a script run when i log in. I have added the script to the startup list under System>Preferences>Sessions, but it is never saved. I read [[COLOR="DarkOrange"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=286883") and tried changing ownership of the autostart file to no avail. That thread dates back to Edgy, and I wonder if things may have changed. The thread mentions the ~/.config/autostart directory. I have no such directory, only and autostart file.

Also, once this is sorted is there a way to specify which workspace a startup item runs in?

TIA

---

### Post by linuxwizard on 2008-01-24
Try this
[https://answers.launchpad.net/ubuntu/+question/12430](https://answers.launchpad.net/ubuntu/+question/12430)

---

### Post by satman-ga on 2008-01-25
Thanks. That thread helped tremendously.

The new item is now saved, but the script does not seem to execute on startup. I'm guessing I've done something wrong at this point. I basically want a script to run in a terminal window on startup. I have entered the following to the startup programs.

Name: Welcome
Command: /home/brad/scripts/Welcome.sh

My terminal profile is set to hold the window open when a command exits, so I know it is not running and closing before I see it.

---

