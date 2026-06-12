---
title: "Can anyone help?"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by dittyman1 on 2006-08-25
I'm configuring the audio on wine because I have a copy of "Starcraft" that I'd like to try and play in Ubuntu.  I'm getting the following message: "can't create mcop directory"  What does this mean?  Here's a screenshot that might help.

---

### Post by Bachstelze on 2006-08-25
Try running winecfg as root with **gk**sudo.

---

### Post by dittyman1 on 2006-08-25
Thanks for the tip.  I have one more question: how is "gksudo" different from "sudo?"  I'm sorry I'm such a noob.  Might be investing in a Linux command reference book.

---

### Post by Bachstelze on 2006-08-25
gksudo is used instead of sudo when you want to run graphical apps (gedit for example) as root in GNOME (in KDE it's kdesu). If you use sudo to run those, you can mess up your permissions very badly.

---

### Post by dittyman1 on 2006-08-25
Hymn (or anyone else),

Well, then it's a good thing I didn't use "sudo."  Anyway, I tried "gksudo."  It tried to configure the audio again.  But the ending message was the same.  "can't create mcop directory."  And, screenshots.

---

### Post by benfindlay on 2006-08-25
gksudo should be used when you're executing sudo commands that run apps external to the terminal I believe

You should use              (* is a wildcard)
```
gksudo gedit *
```

not 
```
sudo gedit *
```

In reality, with things like gedit it doesn't make that much of a difference, but I believe its far more important for certain complicated functions.

---

### Post by dittyman1 on 2006-08-25
Okay.  I'll keep it in mind.  Thanks.

---

