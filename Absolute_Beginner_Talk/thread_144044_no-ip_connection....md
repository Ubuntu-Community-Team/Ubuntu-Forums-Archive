---
title: "no-ip connection..."
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-03-13
I am having trouble working with no-ip. I created my account and created a host account with them. I also forwarded my ports on my router. I went to 
canyouseeme.org to see if the ports were blocked, but it says that that my ISP is not blocking the ports. I am trying to run ssh on port 22. when I try to connect to the server with putty I get an error saying that the connection was refused. Does anyone know what is going on. I have done everything else correctly and have had no problems, except for trying to do the actual connection. I would appreciate any help.

---

### Post by Iowan on 2006-03-13
That the connection was refused suggests you may be reaching the machine.  Some versions of SSH default to blocking root-user logins, but I'll need to check my machine (at home) to see what I did to enable logins.

---

