---
title: "oops"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by YawnXen on 2008-02-03
I may not be an absolute beginner, but I am pretty close. I started with Dapper Drake and am now running 7.10.
I experimented with the services and now I can't run network, services, synaptic, or users and groups.
It keeps telling me that I need to see the administrator.
What did I do?
How do I fix it?

YawnXen

---

### Post by kellemes on 2008-02-03
Can you please explain what exact steps you're taking and what messages you're getting?

---

### Post by YawnXen on 2008-02-03
Under the system/administration menu:
Key ring manager will open
Language support won't open
Network won't open
Network tools will open
Printing will open
Restricted drivers won't open
Screens and Graphics won't open
Services won't open
Shared folders won't open
Shared sources won't open
Synaptic Package manager won't open
System log will open
System monitor will open
Time and date won't open
Update manager will open
Users and groups won't open
Windows Wireless drivers won't open

---

### Post by jan quark on 2008-02-03
type into the terminal
```

gksu network-admin
```

do you get any error message

---

### Post by YawnXen on 2008-02-03
Here is the System log:

---

### Post by YawnXen on 2008-02-03
> **jan quark said:**
> type into the terminal
```

gksu network-admin
```

do you get any error message

Yes

Failed to run network admin as user root
the underlying authorization mechanism (sudo) does not allow you to run this program, Contact the system administrator.

---

### Post by YawnXen on 2008-02-05
I just backed up my data and reinstalled the OS.

---

