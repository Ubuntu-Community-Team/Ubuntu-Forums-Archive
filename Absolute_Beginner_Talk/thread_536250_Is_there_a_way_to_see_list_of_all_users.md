---
title: "Is there a way to see list of all users?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Ozcu on 2007-08-27
So I just got my linux working after hard 5 days. And now it doesn't accepy my username, or password either. So is there anyway to retrieve the password or even see list of users?

---

### Post by aysiu on 2007-08-27
You can't retrieve your password, but you can reset it.

Reboot

Select recovery mode (usually the second boot option)

Type ```
passwd *username*
``` where *username* is your actual username. ```
reboot
``` Select your normal boot option.

---

### Post by rkrug on 2007-08-27
Can you log in as root?

---

### Post by Ozcu on 2007-08-27
Yeah it should log in as root when booting into recovery mode

Now I also see I got some "oem" user, that I found was Original Equipment Manufacturer. After istallation was complete, I was suposed to run a command, but cant remember what it was again, anyone knows?

---

### Post by dwhitney67 on 2007-08-27
> **Ozcu said:**
> Yeah it should log in as root when booting into recovery mode

Now I also see I got some "oem" user, that I found was Original Equipment Manufacturer. After istallation was complete, I was suposed to run a command, but cant remember what it was again, anyone knows?

Command to do what?  Do you want to remove the "oem" user account?  Do you want to list all user accounts?  Please be specific.

---

### Post by shields on 2007-09-01
OK -- when my son is SSH'ed into my desktop and I type "users" he doesn't show. :(

Any ideas why? :confused:

Thanks! :)

---

### Post by dwhitney67 on 2007-09-02
That's odd.  Usually each user who is logged into a system would be shown.  Which account did your son use to login?  Is it different from yours?

You can also verify he is logged in by examining any processes he is running.  You can run:

[FONT="Courier New"]$ ps -ef | grep <userID>[/FONT]

where <userID> is the login ID your son uses.

Yet another alternative is to examine /var/log/auth.log.  This ASCII file contains information as to who has logged into the system.  You can view this file using this command:

[FONT="Courier New"]$ sudo more /var/log/auth.log[/FONT]

---

