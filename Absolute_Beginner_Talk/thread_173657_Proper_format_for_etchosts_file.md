---
title: "Proper format for /etc/hosts file?"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by bcdeck on 2006-05-10
Hi all,

I'm an Ubuntu noob experiencing hostname issues, and I found steps in a thread outlining a way to fix the issue through recovery mode. I seem to be making progress, but I now get an error message stating my hostname can't be found and that I may need to add it to the /etc/hosts file.

My problem is that I'm not sure how it should look. The /etc/hosts file looked like this (I replaced the IP address with X's just in case it's something I sould keep private):
> XXX.X.X.X localhost.localdomain localhost 

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


and I had added this:
> XXX.X.X.X localhost.localdomain localhost 
**hostname mybox**
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


I'm guessing that wasn't right... Can anyone point me in the right direction?

---

### Post by nanotube on 2006-05-10
well, first things first - at what point are you being told that your hostname cant be found and that you should add it to /etc/hosts?

but also, yes, you are doing it incorrectly. :)
just add your hostname "mybox" at the end of the first line, so that it looks like
```
127.0.0.1 localhost.localdomain localhost mybox
```

---

### Post by bcdeck on 2006-05-10
The error message was coming up at login. I had inadvertently deleted the hostname (silly noob that I am), which is why the hosts file had nothing in the spot where I needed to add the name. I fixed the hosts file as you indicated, and now no error message! :) 

Thanks for setting me on the right track :KS

---

### Post by nanotube on 2006-05-10
great! have fun with ubuntu. ;)

---

