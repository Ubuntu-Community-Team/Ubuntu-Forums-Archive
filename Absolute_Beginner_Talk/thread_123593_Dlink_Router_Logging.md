---
title: "Dlink Router Logging"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by lexor on 2006-01-30
I have a Dlink DL-524 Router that gives me the option of sending the logs to a server. I am running Ubuntu 5.10 and have set the ip to send the logs to Ubuntu on the network.

I know I should look in System Logs to view logs but cant see any from the router, I am sure thats cause I havent set it up correctly, cause I am not sure how to.

I would like to put the router logs in a file like router.log and not in any other logs.

I read this thread, but it dont give me a starting point to change syslog.conf and its location.

[http://www.ubuntuforums.org/showthread.php?t=109115&highlight=router+logs](http://www.ubuntuforums.org/showthread.php?t=109115&highlight=router+logs)

If anyone can give me a step by step on how to set it up. 

\\:D/  \\:D/  \\:D/

---

### Post by mips on 2006-01-30
Have you installed/configured a syslog server on your pc ?

---

### Post by lexor on 2006-01-30
No I havent configured a syslog server, just whats on Ubuntu by default.

---

### Post by mips on 2006-01-30
Hmm, Debian has such nice documentation, maybe look here:
[http://www.aboutdebian.com/syslog.htm](http://www.aboutdebian.com/syslog.htm)
[http://www.debian-administration.org/articles/24/print](http://www.debian-administration.org/articles/24/print)

---

### Post by lexor on 2006-01-30
I see that local7 logs messages from a Cisco router, is it safe to think that its the same for a Dlink router. 

What about opening ports on the router or client that will recive the logs, will I have to do that?

Thx for the links it all seems about clear to set up.

---

### Post by mips on 2006-01-30
I have never setup a syslog server before, just used them :)

Dont assume anything, rather read up. You know what they say about assumptions ? "Assumption is the mother of all f____ ups!" ;)

---

