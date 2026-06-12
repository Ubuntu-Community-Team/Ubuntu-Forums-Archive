---
title: "Startup scripts"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by My-dial-up on 2006-04-16
Where do I put a script I want to always run on reboot?

---

### Post by sYs^ on 2006-04-16
Hi, this way: [https://wiki.ubuntu.com/AddingProgramToSessionStartup](https://wiki.ubuntu.com/AddingProgramToSessionStartup)

---

### Post by My-dial-up on 2006-04-16
In terminal mode?

---

### Post by sYs^ on 2006-04-16
I'm not sure, but it worth a try:

Create your script, make it executable, copy to /etc/init.d and create a simlink to /etc/rc2.d.
For example your script name is apache.
```
sudo ln -s /etc/init.d/apache /etc/rc2.d/S20apache
```

I dont know the details but I think it'll work :>

---

