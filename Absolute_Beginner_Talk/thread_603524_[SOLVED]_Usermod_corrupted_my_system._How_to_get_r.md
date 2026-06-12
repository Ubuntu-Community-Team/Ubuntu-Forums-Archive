---
title: "[SOLVED] Usermod corrupted my system. How to get root privileges back?"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-11-05
Hi,
I have executed the following command:
sudo usermod -G *newgroup* *myuserid*

but it looks like my userid has been deleted from all groups and add my user to group newgroup. I just can't believe it looks like the same command works fine on Suse Linux, but has another meaning on Ubuntu. According to documentation on Ubuntu I should execute:
sudo usermod -a -G *newgroup* *myuserid*

So because myuser has been deleted from admin group I can't execute sudo commands anymore.

How to login with root user (it is disables by default and it is disabled in my case) to repair mess.

Thanks,
Abcuser

---

### Post by Bliepo32 on 2007-11-05
Recovery mode?

---

### Post by kellemes on 2007-11-05
Every info you need to recover..
[http://www.psychocats.net/ubuntu/sudo]("http://www.psychocats.net/ubuntu/sudo")

By the way, you misunderstood the usermod command.. this is from "man usermod"

```

usermod -G groups
     Supplementary groups given by name or number in a comma-separated
     list with no whitespace. The user will be removed from any groups to
     which they currently belong that are not included in groups.
```

---

### Post by abcuser on 2007-11-05
Hi,
thank you very much for helping me out. You help me very very much!

It looks like I have mess something with usermod command. The correct syntax is:
sudo usermod -G group1, group2, ... groupN userid
But the command I should be executing is:
sudo usermod -a -G group1, group2 ... groupN userid

I should read man pages more carefully. Thank you very much for your effort. Problem solved!

Thanks,
Abcuser

---

### Post by kellemes on 2007-11-05
Glad I could help. :)

---

