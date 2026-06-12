---
title: "Is it OK to execute from /etc/init.d manually?"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by JimTDI on 2006-11-23
Is it Ok to execute scripts (they are scripts right?) in the terminal window from the /etc/init.d folder?

Im my case, I want to stop Postgres 8.1 so I can edit config files it uses, and restart it.

I have discovered if I run /etc/init.d/postgresql-8.1 stop - that does the trick (at least it tells me Postgres has been stopped).  Am I messing with system files (/etc/init.d) that I should stay out of, or am I on the right track.

Just some reassurance (before I mess things up good) from some of you Ubuntu "experts" would be appreciated!!

Much Thanks!!

---

### Post by taurus on 2006-11-23
Yes, it is perfectly fine to stop and start things in /etc/init.d from a terminal.

---

### Post by Gustav on 2006-11-23
I see no problem with that.

---

### Post by JimTDI on 2006-11-23
Cool!  :) 

Thanks all!

---

