---
title: "SSH through Terminal"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by StifflerNewb on 2006-10-27
Hi!

I got a server using CentOS (text based), and when I try to SSH to it from linux I cant choose root as username. Instead it says "[my accountname on laptop]@[servers ip-adress] Password:"

Anyone know how I can change the username when I try to login?

---

### Post by amo-ej1 on 2006-10-27
ssh automatically uses you current user name to log in. In order to change a different username use

```

ssh myUserNameOverThere@hostname

```

(Which can also be used in scp

```

scp myFile.txt User@hostname:

```

)

(see man ssh, man scp)

---

### Post by StifflerNewb on 2006-10-27
worked perfectly :) thanks!

---

