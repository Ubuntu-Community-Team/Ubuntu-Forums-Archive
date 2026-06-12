---
title: "There was an error starting the GNOME Settings Daemon."
date: 2007-12-08
forum: Apple PPC Users
---

### Post by umwelt on 2007-12-08
I have reviewed all of the suggestions listed in previous posts and none have worked.

If I try starting it from a terminal session I get

[I]ubuntu-desktop:~$ gnome-settings-daemon
[1197139307,000,xklavier.c:xkl_engine_start_listen/]    The backend does not require manual layout management - but it is provided by the application[1197139307,000,xklavier.c:xkl_engine_start_listen/]       The backend does not require manual layout management - but it is provided by the applicationCould not initialize GStreamer: Error re-scanning registry , child terminated by signal
user@ubuntu-desktop:~$ [/I]


I am getting really, really frustrated with the performance of 7.10. If anyone has a perfect solution to the GNOME error I will buy them a beer.

Thus far I have had to contend with a boot failure, Firefox crashing and the ever persistent "[I]There was an error starting the GNOME Settings Daemon. I have also found that apps such as add/remove wont open."
[/I]


I just want to get to a stage where I can actually use 7.10 without begging God to return me to the familiar world of Microsoft Windows.

---

### Post by MonkeyChewToy on 2007-12-09
I'm having the exact same problem. I tried [Joshua Swink's solution,](http://ubuntuforums.org/showpost.php?p=3776732&postcount=15) but that didn't solve anything. (Admittedly, his was a solution to another problem, but it was similar enough that I thought I'd try it.) If someone could find a solution to this, I'd greatly appreciate it, as would much of the PowerPC community, I would assume.

Thank you in advance!

---

### Post by Gen2ly on 2007-12-09
I've had something like this happen before and fixed it by deleting gnome preferences. Zero doubt it's a pain enter all the settings in again but it did the job.  mv .gconf .gconfd, .gnome, and .gnome2 and rename them, kill x server and try once more.

---

### Post by MonkeyChewToy on 2007-12-09
No dice. I still get the same error:
[QUOTE="Error"]There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

GNOME will still try to restart the Settings Daemon next time you log in.[/QUOTE]
It did, however, fix the error I managed to make after following the Swink fix.

*shrug*

Thanks for the help, though.

---

