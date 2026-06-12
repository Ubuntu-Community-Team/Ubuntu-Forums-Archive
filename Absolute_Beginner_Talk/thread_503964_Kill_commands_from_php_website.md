---
title: "Kill commands from php website"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by arsenik on 2007-07-18
I want ot make a website I can go to on my server and be able to kill commands running on the server so my friends can restart their game server when it needs restarted... is this possible?? if so how?

---

### Post by asmoore82 on 2007-07-18
can you just ssh into the server?

---

### Post by Raineer on 2007-07-18
Seconded, do ```
sudo apt-get install openssh-server
``` and just telnet (ssh) in when you need to run a command.  Not exactly sure I'd want to provide shell access via PHP.

---

