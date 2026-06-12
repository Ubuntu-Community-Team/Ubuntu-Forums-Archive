---
title: "GUI not working"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by echomikeromeo on 2006-12-13
Just what it says: my GUI appears not to be loading. When I start up the computer (six-year-old Dell laptop running Edgy) the operating system begins to load as normal, but at the point where the login screen would appear, the screen goes black. After trying various key combinations, I pressed ctrl-alt-del, and the following error message appeared:

"Could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected."

Upon pressing enter I get a command prompt. There's a log of sort of system report things but I'm not entirely sure what it all means. I don't really know how to operate the system without the GUI and I have no idea at all how to fix it - could someone please advise?

---

### Post by kvonb on 2006-12-13
Do it again and when you get to the error report thing scroll down with the down arrow key and look for a line that has (EE) at the start, that is the error line.  Post back here what it says so that someone can maybe figure it out.  There might be more than one (EE) line.

Regards, Kev :)

---

### Post by echomikeromeo on 2006-12-13
I don't see any "EE", but this is what I see on my screen after I press enter:

```
After performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: dircolors: command not found
root@myusername:~# init: rcS process (1823) killed by signal 15
init: rc6 process killed by signal 15
syslogd: /var/log/auth.log: Read-only file system
syslogd: /var/log/syslog: Read-only file system
syslogd: /var/log/daemon.log: Read-only file system
syslogd: /var/log/kern.log: Read-only file system
syslogd: /var/log/lpr.log: Read-only file system
syslogd: /var/log/mail.log: Read-only file system
syslogd: /var/log/user.log: Read-only file system
syslogd: /var/log/uucp.log: Read-only file system
syslogd: /var/log/mail.info: Read-only file system
syslogd: /var/log/mail.warn: Read-only file system
syslogd: /var/log/mail.err: Read-only file system
syslogd: /var/log/news/news.crit: Read-only file system
syslogd: /var/log/new/new.err: Read-only file system
syslogd: /var/log/news/news.notice: Read-only file system
syslogd: /var/log/debug: Read-only file system
syslog: /var/log/messages: Read-only file system
```

... I hope that's some help.

---

### Post by kvonb on 2006-12-14
From my limited knowledge it looks like you are in "single" mode.

From that it looks a bit more serious than just the desktop.

Can you give some more info, ie what version of Ubuntu you are using, is this a new install or have you been using it for some time, what did you do just before it went bad etc'.

Try this:

Reboot, then when the boot menu appears press the "e" key which should take you into "edit mode".  Look on that line for the word "single" (this is from memory so you will have to poke around a bit :rolleyes:), if you see "single", delete it, then I think you press "enter", then "b" to boot.

See what happens.  Don't worry it won't write any of the changes.

I'm just wondering if you inadvertently saved "single" mode as your default boot.

Let me know what happens.

Regards, KEv :)

---

### Post by echomikeromeo on 2006-12-15
I don't see "simple" anywhere, though I've checked all the commands it's possible to edit from the menu.

I'm running Ubuntu 6.10 (Edgy), which I've had since it was released. This problem just occurred a few days ago, though, and up till this point I've been running the OS without any problems.

---

