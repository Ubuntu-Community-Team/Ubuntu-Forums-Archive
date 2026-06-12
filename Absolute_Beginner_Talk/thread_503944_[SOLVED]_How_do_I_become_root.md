---
title: "[SOLVED] How do I become root?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Hickler on 2007-07-18
I'm having a problem, I cannot write/delete files to some directories such as my external hard drive or the "Home" folder. I believe I have to be root (admin in windows?) and I was wondering how I would go about becoming root. Thank you.

---

### Post by PgR on 2007-07-18
Hi,

You can either use ```
sudo <command_you_want_to_run>
```

or if you want to do more than one, then ```
sudo -i
``` will give you a session as root, which is ended with the command "exit"

---

### Post by Hickler on 2007-07-18
Okay, so how would I write a file somewhere using "Sudo"?

---

### Post by wormser on 2007-07-18
What command are you trying to run?

---

### Post by PgR on 2007-07-18
> **Hickler said:**
> Okay, so how would I write a file somewhere using "Sudo"?

What file are you trying to write to? What are you using to write it?

---

### Post by AlexenderReez on 2007-07-18
for window application ,please use gksudo instead of sudo....so if you want to run program...run with gksudo

---

### Post by aysiu on 2007-07-18
You should be able to write to your /home/*username* folder without being root.

If you need permissions to an external NTFS drive, read this:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

If you want to write to something outside your home directory, read this:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by Hickler on 2007-07-18
I just wanted to run file browser I suppose, I was trying to create a "Themes" file in Home as this thread says [http://ubuntuforums.org/showthread.php?t=491096&highlight=how+to+download+themes]("http://ubuntuforums.org/showthread.php?t=491096&highlight=how+to+download+themes")

---

### Post by aysiu on 2007-07-18
If you've downloaded a Gnome theme (GTK, Metacity, or icon set), just drag to the theme manager window, which should appear after you go to System > Preferences > Themes

If you've downloaded a login screen theme (GDM), go to System > Administration > Login Window to add and choose the theme.

---

### Post by DM was on fire! on 2007-07-18
> **Hickler said:**
> I just wanted to run file browser I suppose, I was trying to create a "Themes" file in Home as this thread says [http://ubuntuforums.org/showthread.php?t=491096&highlight=how+to+download+themes]("http://ubuntuforums.org/showthread.php?t=491096&highlight=how+to+download+themes")

You should be able to do that without being root. I've have quite a few folders in my home folder I created and I didn't log into root to do it.
But yes, ayisu is right. He is the man (...or maybe the woman. XD) with the answers.

---

### Post by Hickler on 2007-07-18
> **aysiu said:**
> If you've downloaded a Gnome theme (GTK, Metacity, or icon set), just drag to the theme manager window, which should appear after you go to System > Preferences > Themes

If you've downloaded a login screen theme (GDM), go to System > Administration > Login Window to add and choose the theme.

Hehe, much easier than what I've been trying, thank you very much.

---

### Post by aysiu on 2007-07-18
Well, even though you accomplished this task, you may want to read the links I posted earlier, as they'll help you with file permissions in general.

---

