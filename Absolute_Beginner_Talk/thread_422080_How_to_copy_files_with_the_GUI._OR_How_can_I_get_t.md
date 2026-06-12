---
title: "How to copy files with the GUI. OR How can I get the file Browser to run a command wi"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by ps6000 on 2007-04-24
I am used to copying files from a CD to my hard drive by dragging the files from the cdrom and dropping them into the proper directory. I cannot do this.

How can I get the File Browser to run a command with SuperUser privileges?

---

### Post by aktiwers on 2007-04-24
Type this into terminal:
```
gksudo nautilus
```

And navigate to the folder.
Or if you install Automatix2 you can install gnome scripts with it. One of them is called Root-nautilus-here. Then you just rightclick in the folder you are in, pick scripts and Root-nautilus-here. Very nice.

But your Filebrowser is called Nautilus and superuser is sudo. gksudo is for sudo to open a GUI apps. So the command is very logical :)
Good luck.

---

### Post by Toxicity999 on 2007-04-24
Running Nautilus as root is _generally bad practice_, you would do better to learn about /etc/fstab, and how to make the CD mount with full privileges to you, assuming that is the problem.

---

### Post by jimrz on 2007-04-24
> **ps6000 said:**
> I am used to copying files from a CD to my hard drive by dragging the files from the cdrom and dropping them into the proper directory. I cannot do this.

How can I get the File Browser to run a command with SuperUser privileges?

you should not need sudo for this. in the fli browser window that opens when you insert the disk just select the file(s) you want to copy, right click and select copy. the. navigate to the folder where you wish to put the files, right click  and select paste.

---

### Post by ps6000 on 2007-04-24
The reason I needed to do this was to copy the pk4 files from the doom3 cds. The folder I needed to place the files was /usr/local/games, that dir was protected. Just used to Windows I guess. I copied the files to my user dir then moved them all to the proper directory. But that seemed like an extra step.

I didn't know about the gksudo command (knew about sudo though) whats the difference?

If I occasionally run nautalis as root what do I risk having happen? The only thing I can think of Is doing something stupid and messing up the system.

---

### Post by mac.ryan on 2007-04-24
> I didn't know about the gksudo command (knew about sudo though) whats the difference?i don't know what is the algorithmic difference, but gksudo should be used when you want to launch X/Gnome applications, while sudo is for CLI commands. There are cases in which running a Gnome prog with sudo might break the system. (read more [here]("http://www.psychocats.net/ubuntu/graphicalsudo"))

---

