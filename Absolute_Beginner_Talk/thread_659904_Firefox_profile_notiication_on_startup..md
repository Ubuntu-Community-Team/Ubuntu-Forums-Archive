---
title: "Firefox profile notiication on startup."
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Aidan James on 2008-01-06
so, i'm running xubuntu, and everytime i try to launch firefox, a window pops up, asking me to create a new profile. it says your settings, preferences and bookmarks will be stored in /home/idan/mozilla/irefox. so, i click finish, and click on my profile, but, firefox says 'cannot use te profile 'aidan' because it is in use. to continue, close the running instance of firefox orchoose a different profile'. so, i create another profile, but get the same message. i can't open fireox without making a profile, which i do, but firefox can't open the profile - any help? thanks.

---

### Post by TBerben on 2008-01-06
You can try running
```
~$ ps aux | grep firefox
```
To see whether any instance of firefox didn't terminate correctly. If you get any output from that command, kill every instance of firefox (using kill <pid> where pid is the Process ID, should be the second column of the output)

If that doesn't help, check the file permissions on the firefox profile directory
```
ls -l ~/.mozilla | grep firefox
```
Which should be 700 (drwx------)

---

### Post by nowshining on 2008-01-06
more than likely ur normal profile has become corrupted and u'll need to create a new one :) in ur home folder, press ctrl + h and find .mozilla, then firefox and find ur profile name and right click open in new window and find ur bookmarks, settings and move them into ur new profile or u can simply try a reboot of the  computer.

---

