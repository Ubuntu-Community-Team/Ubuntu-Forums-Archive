---
title: "Edgy update manager error"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Tucatts on 2006-10-30
Ok, got Edgy installed and since I can't find Easy ubuntu I used Aotmatix which seemed to work fine. I had a Automatix update today on the update manager and when I tried to update I got the following error. E: dpkg was interupted, you must manually run 'dpkg --configure -a' to correct the problem. I went to terminal and put the command in and I got the following:
dpkg: requested operation requires superuser privilege.
What is that? Thanks for any help.

---

### Post by Kateikyoushi on 2006-10-30
You can't run it as user, try this:

```
sudo dpkg --configure -a
```

Read this to understand what is superuser and sudo. [LINK]("https://help.ubuntu.com/community/RootSudo")

---

### Post by coolbian57 on 2006-10-30
That means you need to either run the command or be the root user.  In linux, the root user is the"superuser" meaning it can do just about anything.  

If you want to run that command, I would either use the ```
sudo
``` or ```
su
``` command at the terminal first. 

 I don't suggest logging in as root, because it is not secure at all.  But if you truly feel a need to, then do it at your own risk.

---

