---
title: "Can’t access anything!"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by LoicNyssen on 2007-07-05
I recently upgraded to version 7.04 and I can now no longer access anything remotely… ssh won’t connect, with vnc I get the same thing… I was also running a web server on it, which no longer comes up…But when I am on the machine if I type in localhost, every thing works fine… did this new version install a firewall that I am not aware of ? any ideas?

---

### Post by jasonlfunk on 2007-07-05
It shouldn't have, Fiesty doesn't come with a firewall by default. Just in case you can run a ```
ps -ea 
``` to make sure all the processes you think are running should be. Check for sshd, httpd and whatever vncserver you are using. Look for any processes that might be a firewall. 

Nothing changed with your ISP/Router did it?

---

