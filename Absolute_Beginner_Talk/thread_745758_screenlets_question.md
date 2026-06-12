---
title: "screenlets question"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Chapeen on 2008-04-04
I'm logged with the root account , I just installed screenlets.
When I execute the screenlets manager a popup appears

" Important! You are running this application as root user, almost all functionality is disabled. You can use this to install screenlets into the system-wide path. "

How do I get the screenlets to work as root account?

---

### Post by reeseslover531 on 2008-04-04
why do you want to run screenlets as root?

---

### Post by Tatty on 2008-04-04
it is very bad practice to log in as root...
I highly reccomend that you dont do it

[https://help.ubuntu.com/community/RootSudo?highlight=%28rootsudo%29]("https://help.ubuntu.com/community/RootSudo?highlight=%28rootsudo%29")

---

### Post by Chapeen on 2008-04-04
I'm a noob with Linux.
I'm programming with PHP but couldn't because it didn't let me write into the www directory.So now I login as root and it let's me create PHP files into the www directory.
As previously asked is there a way to make the screenlets work as root?

---

### Post by Tatty on 2008-04-04
> **Chapeen said:**
> I'm a noob with Linux.
I'm programming with PHP but couldn't because it didn't let me write into the www directory.So now I login as root and it let's me create PHP files into the www directory.
As previously asked is there a way to make the screenlets work as root?

Log in as normal then load a terminal and type:

```
gksu nautilus
```

This will load nautilus (the file browser), but it will have root privilages.  This is much better practice than logging in as root.

---

