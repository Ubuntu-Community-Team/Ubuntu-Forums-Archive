---
title: "[SOLVED] StartUp Programs"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-10
In windows there is MSconfig which shows you all your startup programs
and allows you to disable them. I use AutoRuns which is a really cool program 
that does the same and more.

I was curious if Ubuntu has anything similar. 
How do you tell what is running in Ubuntu.

With windows you just uncheck what you don't want and
reboot.  Is it that simple in Ubuntu or do things work differently.
I know in windows you have to keep this under control
or your machine will slow to a crawl.  Seems everyone wants
something running in your system tray... ex. quicktime, winamp,
ect. ect.......

So does Linux work totally different or is this a concern in Linux
as well.....

I'm so use to Windows and don't have any experience with Linux
I kinda feel out of control since I don't know how to use it.

---

### Post by MenZa on 2007-08-10
It's possibly to specify start-up programs in System -> Preferences -> Session. Also, applications run as root are stored in /etc/rc.local.

---

### Post by Inxsible on 2007-08-10
System --> Preferences --> Session is what you are looking for to handle startup apps.

Also you can see what programs are currently running using the System -->Administration --> System Monitor tool.

or using ```
top
``` on the command line.

```
free
``` will tell you how much RAM you are currently using and how much is buffered or cached

---

### Post by Orbital75 on 2007-08-10
Thank you..... That's exactly what I was looking for.
Seems very similar to Msconfig.

Thanks

---

### Post by Inxsible on 2007-08-10
> **Orbital75 said:**
> Thank you..... That's exactly what I was looking for.
Seems very similar to Msconfig.

ThanksMake sure you mark the thread as solved :)

---

