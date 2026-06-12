---
title: "Problem with screen"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Ozcu on 2007-02-28
So ya, couple of days ago, I crashed my X by closing 'xorg'-proces. Then I had to configure xserver-xorg by using:
```

sudo dpkg-reconfigure xserver-xorg
```

And now my X works. And drivers should be installed. BUT my screen isn't sharp at all, even I have all settings set correctly. (It was before X crashed). 

Im using Kubuntu 6.06 Dapper, and I have ATI RADEON X700

What should I do? :popcorn:

---

### Post by Ozcu on 2007-02-28
**B**ring
**u**p
**m**y
**p**ost

---

### Post by an.echte.trilingue on 2007-02-28
> **Ozcu said:**
> **B**ring
**u**p
**m**y
**p**ost

Since the most people will probably see your post on the "unanswered posts" search link (at least for the fist 24 hours or so); bumping is probably counter-productive.

Your post is a little light on details.  Why did you have to reconfigure X?  This is a key piece of information for people who want to help you.

The reconfigure command you used leaves backups of your old configuration files.  You will find the file in question is "/etc/X11/xorg.conf".  The backup of the old file has the same name with the date and time of the change appended to the end of the file (for example, xorg.conf.20070117202532).  You can go back to the old configuration file with the crisp screen by renaming it /etc/X11/xorg.conf (thus overwriting your current configuration) and restarting your Xserver with CTRL+ALT+Backspace.

I hope this helps.  If not drop a line.

Take care
-mat

---

