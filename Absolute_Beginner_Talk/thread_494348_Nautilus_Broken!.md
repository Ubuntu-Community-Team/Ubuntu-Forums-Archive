---
title: "Nautilus Broken!"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Nekiruhs on 2007-07-06
After installing [timevault]("http://ubuntuforums.org/showthread.php?t=474973") my nautilus windows and my desktop wont show up. Nautilus is running, and eating up lots of CPU. I tried to run it from terminal, but no text came out, no errors no signs of life. I tried purging and reinstalling nautilus, but it doesn't work.:cry:
Please help. I just reinstalled today and dont wanna have to do it again....

---

### Post by Nekiruhs on 2007-07-06
$ whereis help
help: No where
$ echo "Bump"
Bump

---

### Post by Nekiruhs on 2007-07-06
Le Bump!

---

### Post by Rocket2DMn on 2007-07-06
For lack of anybody having more intelligent answers than came to my mind:
Did you uninstall timevault?  Also, since reinstalling nautilus didn't work, maybe the next step is to reinstall ubuntu-desktop?
Does it work in recovery mode?
I'll check up again when I get home from work, maybe something else will occur to me before then.

---

### Post by Nekiruhs on 2007-07-06
yes I have tried to uninstall Timevault. That doesn't fix anything. I may end up uninstalling ubuntu-desktop so I can reinstall it.

---

### Post by Bosambo on 2007-07-06
Exact same problem...I thought it was Compiz-Fusion at first then remembered the last change I made was to install TimeVault which said it would need to log out and back in to access Nautilus...I forgot about this and carried on my session. When I logged back in my desktop was gone...only the panel was showing and my mouse cursor.

---

### Post by Bosambo on 2007-07-06
No sooner had I posted this message did I decide to kill Nautilus from the System Monitor and start it manually from the run dialogue (Alt+F2)

Got Nautilus back, and my desktop. Logged out and back in just in case it was a fluke...it's up and running again.

---

### Post by Nekiruhs on 2007-07-06
I fixed it. Well, me and the author of timevault.
Open up a terminal and type 
```
jobs
```
type ```
fg
``` now open up another terminal and type ```
killall nautilus
``` No if you want TimeVault to work go to Applications > System > TimeVault click on the sytem tray item that appears and click preferences. Change the backup directory to anything but / ( like /backup) theres an error with the database handling that occurs if you try to start it while using / as the backup directory. The author is working on fixing it.

---

### Post by Bosambo on 2007-07-06
Wish I had bothered to come here first before panicking and uninstalling Compiz...back to Opencompositing.org for me...I'm a twit

---

### Post by Nekiruhs on 2007-07-06
> **Bosambo said:**
> Wish I had bothered to come here first before panicking and uninstalling Compiz...back to Opencompositing.org for me...I'm a twit
You mean that worked for you? Mine installed and worked until an update killed it.

---

### Post by FryerFox on 2007-07-06
Sorry about that guys - this was an error introduced into TimeVault 0.6.5, which has been removed from the download section. The bug which Nekiruhs found has been resolved in version 0.6.6.

---

### Post by Bosambo on 2007-07-07
Timevault now working perfectly (0.6.6) Plus I got my Compiz-Fusion back with no worries...life is good

---

