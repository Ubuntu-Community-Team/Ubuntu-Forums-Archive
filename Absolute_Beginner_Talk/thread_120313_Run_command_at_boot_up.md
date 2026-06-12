---
title: "Run command at boot up"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by Titus A Duxass on 2006-01-21
Hi all,
I have a GiantDisc server set up on a spare pooter.
To get this to run you type gdd.pl at the command line and it runs.

I want this to happen at boot with no user influence.

The system is set up for one user "music" who is logged in automatically at boot.

Can anyone give me some pointers?

Thanks
Titus.

---

### Post by codejunkie on 2006-01-21
[QUOTE=Titus A Duxass]Hi all,
I have a GiantDisc server set up on a spare pooter.
To get this to run you type gdd.pl at the command line and it runs.

I want this to happen at boot with no user influence.

The system is set up for one user "music" who is logged in automatically at boot.

Can anyone give me some pointers?

Thanks
Titus.[/QUOTE]
if your using gnome as your desktop enviorment you can add that command to your session under System/Preferences/session if your not running a gui try adding it to your /etc/init.d/bootmisc.sh file.

---

### Post by Titus A Duxass on 2006-01-24
Okay, I've closed this one myself.
I have placed a script in /etc/init.d that runs my GiantDisc server at boot without having to login a specific user.

---

