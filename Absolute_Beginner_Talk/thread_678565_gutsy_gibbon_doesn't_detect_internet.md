---
title: "gutsy gibbon doesn't detect internet"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Famicommander on 2008-01-26
I have both a WiFi card and an ethernet PCi card in my computer, and neither of them work. Ubuntu doesn't detect either of them or something. I have no idea what to do.

---

### Post by Famicommander on 2008-01-26
Please help. I forgot to mention that I already tried bypassing my router, and it still won't work.

---

### Post by Famicommander on 2008-01-26
Help?

---

### Post by Demz on 2008-01-26
> **Famicommander said:**
> I have both a WiFi card and an ethernet PCi card in my computer, and neither of them work. Ubuntu doesn't detect either of them or something. I have no idea what to do.
have you installed any wifi drivers?

---

### Post by Famicommander on 2008-01-26
> **Demz said:**
> have you installed any wifi drivers?

I haven't done anything. I just installed Gutsy about an hour ago. I hooked up my ethernet connection and I can't get on the internet. It doesn't detect my wifi card at all.

---

### Post by mortsahl on 2008-01-26
Have you tried going to System->Administration->Network and configured your wi-fi and ethernet?

---

### Post by bwtranch on 2008-01-26
Please  open a terminal and post the output of ifconfig

Do you know how that works? If you don't I can give you detailed instructions.

---

### Post by Famicommander on 2008-01-26
It tells me that I'm not allowed to access the system configuration.

That's weird, because this is a one-user computer with an install only hours old. 

Any ideas?

---

### Post by ugm6hr on 2008-01-26
> **Famicommander said:**
> It tells me that I'm not allowed to access the system configuration.

That's weird, because this is a one-user computer with an install only hours old. 

Any ideas?

That is very weird.  Did you install yourself?

Post the output from:
```
groups
```

---

### Post by roboxking on 2008-01-26
Ok, let me try to help. First of all, to gain root access, go to System-->Administration-->Users and Groups, and change the root password to match your user password. That doesn't really help your problem, bubt it's good for the future. Anyways, you probably have unused Restricted Drivers, so go to System-->Administration-->Restricted Drivers Manager, and enable everything you see there. If neither the Ethernet nor the Wifi Card is there, then your problem is a little bit trickier.

---

