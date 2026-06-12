---
title: "Some VNC questions"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by notwist on 2006-06-04
I've just got VNC to work from Windows to my Ubuntu server (running graphically since I'm too much of a noob to run SSH prompt yet).

Anyway, I was wondering if there is any way to have apache, mysql and VNC and everything running even though I'm not logged in on the system.

I tried to connect earlier while on the login-screen, but it refused my VNC connection. When logged in, it works fine.

Do I have to be logged in to be running apache/mysql as well, or is it just VNC thats running strictly on login? If so, how can I make it run all the time?

Thanks :)

---

### Post by notwist on 2006-06-08
Bumpy bump

---

### Post by uzi09 on 2006-06-08
not 2 sure, but y not just leave the computer running and you're self logged on - if anyone else needs it, they could just switch user.

---

### Post by notwist on 2006-06-08
[QUOTE=uzi09]not 2 sure, but y not just leave the computer running and you're self logged on - if anyone else needs it, they could just switch user.[/QUOTE]
I imagine that the computer takes less resources when not logged in, but I'm not sure.

---

### Post by clarkth on 2006-06-08
[QUOTE=notwist]I imagine that the computer takes less resources when not logged in, but I'm not sure.[/QUOTE]

I wouldn't think that the difference in resources would matter that much, and since you can't use it for anything else while waiting for a logon, you're wasting resources right there.

If it's that much of an issue, why not set up a WOL so the computer can be turned off, and have an auto login so you can turn on and off as needed.  (I haven't set up WOL in Linux, but have in Windows).  Just a thought.

---

### Post by Amduscias on 2006-06-08
Well, when you logout your shell is terminated and with the end of the shell all your running processes are terminated / ended. You can prevent that by adding the 'nohup' command in front of your program / script.
Note, that all output that would show up in the Terminal is then redirected to a file named nohup.out (in the current directory or in ~ )

---

