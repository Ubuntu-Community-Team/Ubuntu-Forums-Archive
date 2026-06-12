---
title: "Error updating GNOME Power Manager 2.14.xx to 2.15.92"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Roelski on 2006-08-31
Okay, this is my first serious post, so show me what you got, forum members!

The problem: when unplugging the powercord from my HP NX7010 laptop running Dapper, the Gnome Power Manager detects "critical power level" and shuts down the machine, even though the battery is charged fully.

The apparent solution: update GPower Manager to version 2.15.92 (kudos to Dangson in another tread).  My first attempt ever to compile anything on Ubuntu worked out flawlessly.

I restarted X by pressing Ctrl-Alt-Backspace and could see the power manager icon chaged to a new one.

However, when X is started, I get an error message that says "GConf schema installer error, battery_low_percentage cannot be zero".  That's where I kinda loose it... :D See also screenshot attaced.

My best guess is a programming error (I don't mean to shoot at the developer here off course) or a value that states zero where it should be something else.

So here's my question to the Community: what's next???

Thanks for any help!

Best regs,


Roelski!

---

### Post by Roelski on 2006-09-02
Apparently, the solutions is to restart your machine after compiling... So there is still a bit of Win-influence... :-)

Anyway, let's wait for GNOME 2.16 that is due September 6.


roelski

---

### Post by Jim Rockford on 2007-01-18
> **Roelski said:**
> Apparently, the solutions is to restart your machine after compiling... So there is still a bit of Win-influence... :-)

Anyway, let's wait for GNOME 2.16 that is due September 6.
roelski
-------------------------------------------------------

Apparently, this problem didn't get fixed in GNOME 2.16.

Jim

---

