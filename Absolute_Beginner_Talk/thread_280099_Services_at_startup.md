---
title: "Services at startup"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by PCSpectra.com on 2006-10-18
I need to enter the following at my command prompt whenever I reboot...

>  sudo /opt/lampp/lampp start


How can I have this done automatically at bootup, possibly without using sudo as well, so I don't get prompted for the password???

Is there an autoexec.bat or similar file?

Thanks :)

---

### Post by mssever on 2006-10-18
Put the command sans sudo in /etc/rc.local *above* the line that says exit 0.

---

### Post by mssever on 2006-10-18
You also need to make a script that stops lampp on shutdown, since mysql can lose data if it isn't shut down properly.

A much better way to handle this is to remove lampp (you don't need it) and install what you need through Synaptic. They'll be automatically set up properly, you'll automatically get updates, and you won't have to worry about lampp's horrendous security holes.

---

