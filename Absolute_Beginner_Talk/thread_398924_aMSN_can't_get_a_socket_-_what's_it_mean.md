---
title: "aMSN can't get a socket - what's it mean?"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by thefoolisme on 2007-04-01
My aMSN was working fine when I first installed it.  Now henever I try to open it, a get an error message that says:  "Unable to get a socket from localhost.  Check your /etc/host file, please"

I would gladly check file /etc/host file if I knew what I was looking for.  I thought maybe an update changed something in it, so I uninstalled it, restarted, and then reinstalled it.  Still getting the same message.  Can someone please help me fix this, or at least let me know what I should be checking in the file?  

Thanks.   ](*,)

---

### Post by Maestro23 on 2007-04-01
In terminal type:

> cat /etc/hosts

Copy/Paste output here.

---

### Post by thefoolisme on 2007-04-01
leah@leah-laptop:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       leah-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
leah@leah-laptop:~$ 

OK, what's next?

---

### Post by thefoolisme on 2007-04-05
Bump.  Thought 3 days was enough time.  :-)

---

