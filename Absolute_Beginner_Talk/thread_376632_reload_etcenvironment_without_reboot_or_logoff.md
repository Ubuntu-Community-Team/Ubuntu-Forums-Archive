---
title: "reload /etc/environment without reboot or logoff"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by jonbob on 2007-03-05
Hello 

i am new at ubuntu.

i have change something in the /etc/environment. Now i wont to relod it but without reboot or logoff.

who does it work? work it as well with the /etc/profile? If I want write my own export file, where/ who have i add it that it start by booting.

thanks for your help

---

### Post by x1a4 on 2007-03-05
From a terminal run 

*source /etc/environment*

---

### Post by jonbob on 2007-03-05
thank you very much.
:guitar:

---

### Post by x1a4 on 2007-03-05
> **jonbob said:**
> thank you very much.

You're welcome very much.

---

### Post by xbYdx on 2007-08-17
Is there a gui for setting environment variables?  It seems like this would be fairly simple to implement in Ubuntu since it's only a matter of editing /etc/environment and running "source /etc/environment".  I'd be willing to try to implement something like this if it hasn't already been done.  It might be a good first contribution to open source.

FYI:
I had looked for an answer to the question of setting environment variables without having to login or restart on several occasions, but couldn't find an answer.  I finally got fed up with having to log off / on when changing my JAVA_HOME environment variable and spent a considerable amount of time searching for an answer, refusing to believe there wasn't a better way.  Eventually I found this forum with the google query: 
ubuntu reload /etc/environment
I tried others such as:
ubuntu refresh /etc/environment
ubuntu set environment variables
linux set environment variables
*also using above with variations of:
without rebooting
refresh
reload
gui

Sorry, this is long, but I'm writing in the hopes that google or other search engines will find this page when people who think like I do try to find it.

---

### Post by xbYdx on 2007-08-17
It looks like I responded too soon.  This seems to not work like I was expecting. Using the command 'env' I see that the changes I made to /etc/environment only exist in the terminal I ran 'source /etc/environment' in.  Is there anything like 'rehash' for Ubuntu?

---

