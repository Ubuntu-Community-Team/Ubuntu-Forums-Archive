---
title: "security problem port 8888 ? localhost:8888"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by aBitLater on 2008-02-09
I was researching a pdf problem in the ubuntu forums, and I saw where someone mentioned localhost:631 for cups management.  I went to my firefox browser and started to type in localhost:631.  Before I was done, the drop-down box, (which shows my URL history) showed these itiems:


> [http://localhost:8888/](http://localhost:8888/)
[http://localhost:8888/welcome](http://localhost:8888/welcome)
[http://localhost:8888/password_controller](http://localhost:8888/password_controller)
[http://localhost:8888/confirm_distro_controller?confirmation=1](http://localhost:8888/confirm_distro_controller?confirmation=1)
....
[http://localhost:8888/notes_controller](http://localhost:8888/notes_controller)

what are these and why do they appear in my browser history (URLdrop down box, auto-completion)???

---

### Post by neurostu on 2008-02-09
Have you ever configured your router via your browser?  Are you the only person with access to your computer?  Have you tried looking at localhost:8888?

---

### Post by aBitLater on 2008-02-09
hello neurostu

yes, I have configured my router through my browser.  I can't connect to localhost:8888

and yes, I'm the only one with physical access to my computer

---

### Post by neurostu on 2008-02-09
Well its my guess that when you connect to your router via: 192.168.1.1 or something like that it automatically forwards its content to port 8888 on your machine and then has your browser go to localhost:8888. 

Try logging into your router and then looking at your address bar to see if it changes from 192.168.1.1 to localhost:8888

If that doesn't work then the best thing to do would be to just close port 8888 and then see which service breaks, that will let you know which service was using 8888.

Again, though, I'm 99% sure it was your router.

---

