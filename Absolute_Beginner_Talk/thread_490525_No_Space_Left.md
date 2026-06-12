---
title: "No Space Left"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by stevelasvegas on 2007-07-02
Ubuntu installed using Wubi. After typing my username and password I get the message "Your session only lasted less than 10 seconds blah blah.
mkdtemp : private socket dir : no space left on device
It's been working fine for a month. This happened after I installed VPN
I'm a newbie. Learning the hard way.

Now what do I do?
Not another reinstall please.

---

### Post by AlexenderReez on 2007-07-02
i'm not really understand your situation ...but..i have experienced one situation that quite similar ..
while using beryl few month ago....i tried to record for full lugin and at the same time change to .avi format.....at the moment i don't realized that i have only few gb space...(about 2)...then while recording...for sudden..it hang..... i restarted the system...and it state that,session can't log in because of not enough space......i used to solved this problem with.....boot in save mode....which is recovery mode .... and uninstall few software that quite big such as amarok music player....and i reboot....i manage to log in and then move record avi that quite big to other harddisk.....after that install software that i removed before....in your case....try to uninstall that particular software which  your last installation......and when you can log in...think other solution.....

---

### Post by stevelasvegas on 2007-07-02
I recovered by typing sudo apt-get clean. I will google that to find out what it does, but it fixed it. Now my question would be, how do I prevent this from happening again and apparently I need to increase the size of available space. I need to figure out how to do that. I may not live long enough to figure out Linux. :o

---

### Post by mpeters on 2007-07-02
You should be able to log on to the GNOME Failsafe mode (under "Sessions" at the login screen). That should give you a terminal where you can type:

[INDENT]df[/INDENT]

Which should show how much space you have available on each of your partitions. One of them, probably the / partition is most likely 100% full. At the console again, try:

[INDENT]sudo apt-get clean[/INDENT]

and then run df again to see if that has cleared up any space. If not you can run:

[INDENT]sudo du -h --max-depth=1 /[/INDENT]

which should show you which directories are taking up the most space, from which you can hopefully find something which is taking up a lot of space and is safe to delete.

---

### Post by mpeters on 2007-07-02
> **stevelasvegas said:**
> I recovered by typing sudo apt-get clean. I will google that to find out what it does, but it fixed it. Now my question would be, how do I prevent this from happening again and apparently I need to increase the size of available space. I need to figure out how to do that. I may not live long enough to figure out Linux. :o

Guess I didn't type fast enough.  ;)

"apt-get clean"  basically cleans up files left over when installing software. Running it from time to time will probably help.

---

