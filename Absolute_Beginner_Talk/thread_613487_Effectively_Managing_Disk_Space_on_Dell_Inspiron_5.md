---
title: "Effectively Managing Disk Space on Dell Inspiron 5000e"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Eric Lander on 2007-11-15
I'm brand new to Ubuntu, and I'm using 7.10 on a Dell Inspiron 5000e.  I've got the system running okay, but being new to Ubuntu, I'm unsure of how to clean things up a bit.  I've been using Windows for 10 years now, and this is my first machine using any Linux distro at all.

Checking the Dsk Usage Analyzer, I see that my 4.4GB drive is 86.9% full with 3.8GB of data stored.

This is a Ubuntu only machine, and I thought I could get by with this drive.  I'd like to see some ways in which I could free up storage space so I can begin using this as an actual production machine (web development, php authoring, graphical work, etc.)

How can I go about removing unnecessary components of Ubuntu?

---

### Post by Ozeuss on 2007-11-15
You can use synapic package manager to remove packages you do not need (but be careful of dependencies).

---

### Post by mikewhatever on 2007-11-15
sudo apt-get autoremove <-- To remove unmet dependencies, if any.

sudo aptitude clean <-- To empty cached packages from /var/cache/apt/archives.

If that does not free enough space, start uninstalling things.

---

### Post by Inxsible on 2007-11-15
Try this [link]("http://ubuntuforums.org/showthread.php?t=140920&highlight=cleaning+ubuntu+system"), but make sure you know what you are doing before blindly copy pasting commands and following instructions.

---

### Post by kpkeerthi on 2007-11-15
In my opinion 4 GB is too slim to be used in a in kind of environment you want to (web development, php authoring, graphical work, etc.). A base ubuntu install (GNOME with stock applications) easily takes 2 GB of space. You may want to consider adding more space to your system. Just my 2 cents.

---

### Post by Eric Lander on 2007-11-15
Thank you all for your replies... I do know that things with this system are slim, but I am open to upgrading, or replacing, the system.  Especially if I can adapt well to the environment.

Thank you again, and I'll read the link above and try some things out.  I really appreciate the willingness to help someone new in here.

---

