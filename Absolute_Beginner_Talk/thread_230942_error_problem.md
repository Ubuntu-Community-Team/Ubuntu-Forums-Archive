---
title: "error problem"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by jdm2 on 2006-08-06
I still pretty new to linux but I'm getting better but I don't know how to fix this error.  Can you help me out?  Thanks

I was install a package and something went wrong and now I have a error message.  Here the message.  

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

here's the terminal output

jdm@jdm-desktop:~$ sudo apt-get install -f
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Can you help me out?  Thanks

---

### Post by jdm2 on 2006-08-06
Thanks for taking the time to look at this post but I have fixed it.  Thanks again

---

### Post by ColdDeath on 2006-08-06
What was wrong? (If you say it will help others who have this problem)

I think you had Synaptic / Update running at the same time, but I'm not sure.

---

