---
title: "binding ports"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by xodiox on 2007-09-10
Ok, i have a wield problem i when i try to run a logonserver on ubuntu it starts up, then says Bind unsucsessful on port 3724.Bind unsuccessful on port 8093. Then exits the logonserver.

Anyone know how to bind ports 3724 and 8093 to the logonserver ?

---

### Post by bwhitaker on 2007-09-10
Could something else be using those ports?

```

netstat -an | grep 3724
netstat -an | grep 8093

```

Also I'm not quite sure what you mean by logonserver, please provide more info.

Thanks,

---

### Post by Polt3rg31st on 2008-06-20
By logonserver he means the portion of a world of warcraft private server that is essential in creating the realm and allowing users to join the server.

---

