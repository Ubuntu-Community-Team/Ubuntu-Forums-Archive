---
title: "users and groups help"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by dougleduck on 2007-12-11
I'm trying to install matlab, which I think would work fine just using sudo.I'm concerned about some unknown program have root access though.

Is there a way using groups to let it have only the necessary permissions? I've tried to find some documentation on users and groups but couldn't find anything quite relevant.

Thanks.

---

### Post by SupaSonic on 2007-12-11
You need root privileges to install something, but that doesn't necessarily mean you need them to run the installed application. If you run the app without sudo then you'll be fine. You really needn't worry about groups and stuff.

If however you run the app as a normal user and then choose to save your work anywhere outside /home/<yourusername> - then you'll get a 'permission denied'.

---

### Post by dougleduck on 2007-12-11
I haven't installed the app yet and I need to give it root privelages to do so. I just want to know if I can avoid it having having full root access using groups.

---

### Post by SupaSonic on 2007-12-11
Well for that you'd have to know where the files it installs would go. Then change the owner of those directories to a new group. Or use acl to add permissions for that group. Anyway, it's definitely not worth the trouble. I seriously doubt there will be any malicious software in the installation (be it a deb file or sources). And as long as you don't **_run_** the app as a root you don't have to worry.

EDIT: Found this page: [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB) maybe it'll help.

---

### Post by dougleduck on 2007-12-11
I'd like to know a bit about users and groups anyway if anyone knows somewhere that explains what can and cannot be done with them. At least the command so I can look at the man pages.

Thanks.

---

### Post by SupaSonic on 2007-12-11
man chown
man chmod

---

