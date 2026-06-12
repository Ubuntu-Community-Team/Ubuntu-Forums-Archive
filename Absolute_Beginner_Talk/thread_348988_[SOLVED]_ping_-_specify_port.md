---
title: "[SOLVED] ping - specify port"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by olejorgen on 2007-01-29
How do I specify what port, ping should use?

I've tried ping ip:port, but that did not work. Man pages does not help much either.

---

### Post by Jussi Kukkonen on 2007-01-29
Short answer: you can't.

Ping does not operate on ports even though it uses the TCP/IP stack -- it has it's own protocol  (ICMP) and own command (echo). 

You'll probably want to use telnet for your port debugging...

---

### Post by olejorgen on 2007-01-29
Hm, could I use telnet to send some random data to a port?

---

### Post by steve.horsley on 2007-01-29
What are you trying to achieve? What's wrong with ping?

Most ports aren't listening for incoming calls. The default Ubuntu install isn't listening on **any** ports.

---

### Post by Jussi Kukkonen on 2007-01-29
Well, with some constraints (it is text after all). You can e.g. connect to a web server and write the proper requests by hand and get the page as result.

---

### Post by olejorgen on 2007-01-30
I'm just trying to debug a extremly simple "server" (shcool exercise of a friend). I guess I can wipe up a qiuck java app to do it, but I reallly thought this should be easy from the commandline too?

---

### Post by Jussi Kukkonen on 2007-01-30
Telnet should do. What does the server expect to receive?

---

### Post by steve.horsley on 2007-01-30
If it's a server, I guess it's listening for TCP connections. You can try it out by telnetting to that port. You put the port number after the IP address in the telnet request like this:
telnet 1.2.3.4 5678

If it's a UDP server (less likely), you can use** nc -u **instead of telnet, but it may well choose not to answer.

---

