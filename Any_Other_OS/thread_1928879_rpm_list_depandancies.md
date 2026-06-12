---
title: "rpm list depandancies"
date: 2012-02-20
forum: Any Other OS
---

### Post by conradin on 2012-02-20
Hi all,
I am wondering what command to use to list all dependencies for a package. Both for what the package requires, and for what packages require the package.

will the command```
rpm -qpR <package> 
```

do that for me, or is it more involved?

---

### Post by cortman on 2012-02-20
The Fedora forums are pretty active, you'd probably have good luck asking around there.

BUT, I do know Synaptic will do that for you.

---

### Post by boydrice on 2012-02-21
> **conradin said:**
> Hi all,
I am wondering what command to use to list all dependencies for a package. Both for what the package requires, and for what packages require the package.

will the command```
rpm -qpR <package> 
```

do that for me, or is it more involved?

There are a couple of ways to do that.  One is using yum deplist package
 [http://docs.fedoraproject.org/en-US/Fedora/14/html/Software_Management_Guide/ch05s11.html]("http://docs.fedoraproject.org/en-US/Fedora/14/html/Software_Management_Guide/ch05s11.html")

another would be  rpm -qa | grep package

---

