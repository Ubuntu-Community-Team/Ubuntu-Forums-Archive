---
title: "Does my backup Backup?"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Wee Nyaff on 2007-04-15
Yet another beginners question.
I am one of those people who have been working at increasing my screen resolution and part of the process is to backup my xorg.conf prior to editing the original.
I cut and paste the command in to my terminal (I have learned not to trust my typing" and hit enter.  After asking for my password the terminal immediately starts a new line 
"person@person etcetera"
It all happens so quick that I do not know if it has worked or not.
I have done a file search for the xorg.conf-backup file but no files are found.

After one of my attempts at editing the conf file I got the dreaded black screen and when I entered the command to restore the xorg.conf file (my typing this time, but copied meticulously from a forum post) it claimed no such file existed.

Where is and how can I confirm that a backup file exists?

Thanks in advance
Alan

---

### Post by heimo on 2007-04-15
> **Wee Nyaff said:**
> 
Where is and how can I confirm that a backup file exists?

If you used a command like:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
```

Then the backup file will be /etc/X11/xorg.conf_bak and you can check it with:
```
ls -l /etc/X11/xorg.conf_bak
```

---

### Post by Wee Nyaff on 2007-04-15
> **heimo said:**
> If you used a command like:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
```

Then the backup file will be /etc/X11/xorg.conf_bak and you can check it with:
```
ls -l /etc/X11/xorg.conf_bak
```

:D  Thank you heimo,
You have once again proved that this is a great forum for getting help especially from you.
It will take wild horses to get me away from linux now.  I may be slow, dumb and old but feel good in this community.
You deserve more than a thanks.
Alan

---

