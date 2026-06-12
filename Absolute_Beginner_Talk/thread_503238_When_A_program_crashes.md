---
title: "When A program crashes"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Mekanto on 2007-07-17
I had a problem which i had to fix by restarting my computer.

I could not open Firefox because it was already open or someting.

Well I was wondering if there is a way to see a list of the processes like on windows there is task manager. please help?:popcorn:

---

### Post by dfreer on 2007-07-17
System > Administration > System Monitor should help you out :)

---

### Post by Motoxrdude on 2007-07-17
Yuep, sure is. Press alt+f2 and enter 
```
gnome-system-monitor
```

---

### Post by reckless2k2 on 2007-07-17
I'm sure there is a GUI friendly way of doing it but the command line is a way to do it. Open a terminal and do the following:

$ps

It'll display the running processes and one of them should be firefox. I think you might be able to "push" it to the foreground by using fg and the process ID number like this:

$fg <PID>

If not, just use kill to kill it:

$kill <PID>

Run ps again to make sure it's gone. Sometimes and I mean sometimes it can be a little pesky to kill so you have to do it like this:

$kill -9 <PID>

The PID will be the number is the "ps" output next to the command running. Try that out or I'm sure someone will bounce back with a GUI way or correct mine if it's worng.

---

### Post by Mekanto on 2007-07-17
> **dfreer said:**
> System > Administration > System Monitor should help you out :)

This worked, thanks alot!

---

