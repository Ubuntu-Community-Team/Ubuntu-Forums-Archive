---
title: "changed user ID + noob = bad becuase i forgot it"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by williamburn on 2007-06-08
Is there a way to recover an ID or somewhere that i can see what it might be.  I remember the password i changed, but for the life of me cannot remember the ID.

Im at the ubuntu login --- is there another account that I can try to recover from?  I think root is disabled by default.  Frankly, it was a VM-ware download, so i really havent lost that much, but nonetheless i would rather not re-download everything.

Much appreciated

Super noob!

---

### Post by Najand on 2007-06-08
Try to reboot in recover mode and in terminal type:
```

$ cat /etc/passwd

```
to find it out.

---

### Post by williamburn on 2007-06-08
i am running through vmware, do you know how to reboot to recovery mode?

btw thanks for the speedy reply

---

### Post by Najand on 2007-06-08
Shutdown. Boot again.  When booting, after BIOS, push Esc button and select the second option from above.

---

### Post by williamburn on 2007-06-08
Najand, thank you again.  I got in as root and reviewed the logs.  

I knew i changed it to something that was fitting!

user id:  noob


I am trying to get this whole linux thing working, thanks again for your help.

---

