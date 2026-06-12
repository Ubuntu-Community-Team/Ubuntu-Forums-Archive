---
title: "Re-configure to Boot to Command Line"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Arronax on 2007-07-03
Okay, so I installed GNOME on Server...I admit it, I got scared. It's been about 8 years since I touched Linux and I wanted to feel safe. :P

Where/How can I set the server to boot BACK to command line? I punched a couple of search terms in but didn't see anything that caught my eye.

Thanks for the help!

---

### Post by Arronax on 2007-07-03
[editted]

Nevermind that option, I don't want to install sysv-rc-conf unless I need to for some reason...there's got to be a line in a file...I read something about inittab in /etc but I didn't see it ??

---

### Post by Arronax on 2007-07-03
Ok, so I installed sysv-rc-conf with apt-get and then ran it, changed runlevel2 to NOT run gdm and rebooted to test. It worked!

---

