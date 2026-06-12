---
title: "KDE won't start session for my user"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by [S|G] on 2006-06-02
Well, the title pretty much says it. I logged off and when I logged back in the system would hang in the second phase of loading kde (loading system processes). 

I killed X and was able to start a fluxbox session normally. Then I tried kde again. Still wouldn't start. Then I logged into a terminal and tried to start kde as root, and it started normally. It also started as another user.

What can I do? My kde saves my session automatically on close, how can I clear saved session data? If I remove my $HOME/.kde folder will I lose my custom settings (such as desktop layout)? 

Any ideas? :confused:

---

### Post by aysiu on 2006-06-02
If you *remove* the ~/.kde folder, you will lose your customizations.

You can, however, just [i]move[i/] the folder: ```
mv ~/.kde ~/.kde_backup
``` log in and then slowly migrate portions of that folder back.

---

### Post by [S|G] on 2006-06-02
Thanks aysiu. I backed up my .kde folder and tried to restart X, but didn't work. Then I logged in as root, moved the whole bunch of .configuration directories and restarted X. It worked this time :)

Then I restored some directories (only the one for the apps I actually *knew* I used with some frequency), restarted and everything seems to be running fine again.

---

