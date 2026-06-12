---
title: "inetd on ubuntu"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by illusion on 2006-03-08
Hey,

Trying to get inetd started in ubuntu.  Any documentation on that would be graat.  The file inetd.conf is in the /etc directory to list the services to listen for, but can't get the inetd super server to start.  What is the command to start inetd manually?  Once again any documentation on this would be great.

thanks in advance,
Illusion

---

### Post by illusion on 2006-03-08
Hey,

Found the answer to my problem in the ubuntu as server forum.

thanks,
Illusion

---

### Post by deBaas on 2006-03-08
For all those who are curious:
```

#sudo /etc/init.d/inetd restart

```

---

### Post by DA_uf on 2006-07-10
> #sudo /etc/init.d/inetd restart

I had to install netkit-inetd on Dapper to get this.

---

