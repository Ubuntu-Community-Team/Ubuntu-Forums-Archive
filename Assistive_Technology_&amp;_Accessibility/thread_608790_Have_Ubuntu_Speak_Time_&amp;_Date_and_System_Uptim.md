---
title: "Have Ubuntu Speak Time &amp; Date and System Uptime"
date: 2007-11-10
forum: Assistive Technology &amp; Accessibility
---

### Post by dancallo1190 on 2007-11-10
Want to learn how to get Ubuntu to speak the time of day, date, and system uptime to you.  Here's how:

Open an X Terminal Window by clicking on Applications > Accessories > Terminal.  Next, at the prompt, type in:

sudo apt-get install saytime

Enter your root password when prompted.  The installation will start and Ubuntu will grab any dependencies that are required.  At the conclusion of the installation, type in the following:

sudo apt-get install saydate

The installation will start for this application and Ubuntu will grab any dependencies that are required.

Now, any time you want to know the time and you want Ubuntu to speak it to you, open a Terminal window and type in:

saytime

and press the Enter key.  Ubuntu will give you the time of day down to the second.  If you want to know the date and how long your system has been up and running, type iin:

saydate

It's as simple as that.  Enjoy!

---

### Post by K.Mandla on 2007-11-14
Moved to Accessibility Discussions.

---

### Post by kd7swh on 2007-11-14
you can use the:

```
uptime
```

command from the terminal with orca.

that will give you the current time in 24-hour format, followed by uptime, number of users, and cpu load average.

or you can use the 'date' command

---

