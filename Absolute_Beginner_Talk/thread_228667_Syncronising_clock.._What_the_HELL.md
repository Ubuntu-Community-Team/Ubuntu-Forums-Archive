---
title: "Syncronising clock.. What the HELL"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by anaconda on 2006-08-03
Every time I boot Ubuntu without internet connection booting takes about 2 minutes longer, because it is trying to 
"Syncronice clock with www.ubuntulinux.org"

What is this? It seems that my computer is connecting to [www.ubuntulinux.org](www.ubuntulinux.org) or somewhere each time I boot.. WHY?.. is it some kind of spyware?, or is ubuntu keeping track how often my system boots or what? 

How can I disable this? waiting 2 extra minutes with each time I boot without connection is waaay too long...

---

### Post by carlosqueso on 2006-08-03
what it is doing is setting the system clock to the actual time.  Windows machines do it with ntp.microsoft.com (I believe), and most *nix machines do it with a public server.  Ubuntu just uses it's own.  To skip it when you don't have a connection press CTRL+C  when you see the syncronizing clock thing and it'll skip.

---

### Post by anaconda on 2006-08-03
Thanks for the info. Ctrl+C is good to know.

IS there any way to disable this feature completely, 

Or does the system clock need to be on "syncronised" time.. why?

---

### Post by ColdDeath on 2006-08-03
Take a look here: [http://ubuntuguide.org/wiki/Ubuntu#Synchronizing_clock_to_ntp.ubuntulinux.org..._.28taking_too_long_to_load.29](http://ubuntuguide.org/wiki/Ubuntu#Synchronizing_clock_to_ntp.ubuntulinux.org..._.28taking_too_long_to_load.29)

I hope it helps.

---

### Post by anaconda on 2006-08-03
Thanks. Will look to it.

---

### Post by confused57 on 2006-08-03
Also, might want to check this out:

[http://www.ubuntuforums.org/showthread.php?t=89491&highlight=boot+process](http://www.ubuntuforums.org/showthread.php?t=89491&highlight=boot+process)

---

### Post by deanlinkous on 2006-08-04
Likely adjusted in the services tool or maybe some other admin tool but I would bet on services.

---

