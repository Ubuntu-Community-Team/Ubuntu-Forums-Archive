---
title: "I would like to run a STMP server"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Abstract on 2006-09-01
Hey all,

  I was wondering if there is a recommended/easy to use STMP server for Ubuntu. I'd like to set one up so I can send mail from localhost.

Thanks in advance.

---

### Post by kidders on 2006-09-01
Postfix is the SMTP server of choice for lots of people. It's not exactly what you'd call "simple" to operate, in that you have to tweak it a little to get it going, but it's tremendously powerful.

There are plenty of other options around ... it just happens to be one I like, so I can walk you through the setup if you need a hand. It would allow you to use your own computer to handle all outgoing (and also incoming, if you wanted) email for multiple users, and has plenty of really flashy optional features.

If you'd like to try it, remember two things:
[LIST=1]
[*]Make absolutely certain that port 25 is only accessible from **your** side of your LAN.
[*]Focus on /etc/postfix/main.cf for settings you might want to mess with.
[/LIST]

Any help?

---

