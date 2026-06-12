---
title: "Telnet"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by Link360 on 2006-11-22
I am trying to telnet on Ubuntu using the default terminal. I have the Dapper  version. Everytime I try to telnet to a website this comes up: 
"telnet: Unable to connect to remote host: Connection timed out"
Do I need a different terminal or something. Please help. Thanks.

---

### Post by Link360 on 2006-11-22
bump

---

### Post by taurus on 2006-11-22
What site are you talking about and please do not use telnet!  Instead, use ssh since it's more secure...  As far as I know, nobody is using telnet anymore unless you happen to live in the 80's or early 90's!!!

---

### Post by steve.horsley on 2006-11-22
The chances are that the web site ignores telnet connection requests, although if you are insode a corporate network, it could be your corporate firewall that is dropping the connect request. **telnet hostname** from the command prompt is indeed the correct way to connect to a telnet server.

---

