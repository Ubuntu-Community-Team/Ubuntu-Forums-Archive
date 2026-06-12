---
title: "Is this command not right?"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-09-13
Ive installed lm-sensors and sensord daemon so i can monitor my hardware. Im looking to alter sensord so it reads the system temp every 60secs instead of every 60mins. 

Im following this link
[http://www.lm-sensors.org/wiki/man/sensord](http://www.lm-sensors.org/wiki/man/sensord)


The command "sensord -h" works..

But when i try type "sensord -l 60s" which is meant to be the command to change the time log for sys temp to 60secs it returns 

"fopen("/var/run/sensord.pid")ermission denied

Whats going on?

---

### Post by Timothy Butwinick on 2006-09-13
Try "sudo sensord -l 60s"

---

### Post by halcyon on 2006-09-13
I've never used the program myself, but it looks like you need root privileges to run that command.

Try "sudo sensord -l 60s" instead and see if that works.

EDIT: Beaten again! ](*,)

---

### Post by meniscus on 2006-09-13
Thanks!It worked!!

Is there any where you can reccommend where i can lookup basic command line commands for ubuntu? What does sudo mean anyway?

---

### Post by meniscus on 2006-09-13
Sorry i meant whats the difference between sudo and root? Why is there a need for a sudo?

---

### Post by jordanmthomas on 2006-09-13
The basic commands in Ubuntu are the same as in any other linux.  I don't have a link handy, but it's pretty easy to find references to commands

sudo means "super-user do" and allows your user to run something with root privileges

---

### Post by halcyon on 2006-09-13
You're welcome, and sudo means "super user do", basically, run this command with administrator privileges.  For a list of commands, I'd recommend here: [http://www.ss64.com/bash/]("http://www.ss64.com/bash/").  You can click each command for more info on it.

---

### Post by jordanmthomas on 2006-09-13
When I first started out, I read through this:
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

I liked it.

---

### Post by teddy879 on 2006-09-13
Go [here]("https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html#root-and-sudo") for more info on using sudo.

In general, the [Ubuntu Documentation Site]("https://help.ubuntu.com/6.06/") and the  [Unofficial Ubuntu Linux Starter Guide]("http://ubuntuguide.org/wiki/Dapper") are excellent resources that have helped me a bunch in learning how to do what I need to do with Ubuntu.  :p

---

