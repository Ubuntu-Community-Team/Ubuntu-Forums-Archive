---
title: "Problems with /etc/apt/sources.list"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by sarracenia88 on 2006-10-07
This is my first time using Ubuntu and now my software won't let me update or add programs or anything. when I try to start add programs, I get a message that says

"Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'."


Any help with this would be appreciated.

Thanks

---

### Post by grim918 on 2006-10-07
Which version of Ubuntu are you running. and if possible can you post the contents of your sources.list file

---

### Post by jordanmthomas on 2006-10-07
could you post the outputs of these commands please?\
```
ls -l /etc/apt
```
and
```
cat /etc/apt/sources.list
```

**edit** forgot to mention that you put these commands in at the terminal (Applications --> Accessories --> Terminal)

---

### Post by sarracenia88 on 2006-10-08
I just reinstalled ubuntu because other parts of it were messed up. Now it is working fine. I tried to install xgl without knowing how to. I really want to get xgl running though.

---

### Post by dolphinsonar on 2006-10-08
This just means you should update Ubuntu.  Go to the terminal:

Applications>Accessories>Terminal

Then type 

```
sudo apt-get update
```

Sudo just means that you are giving administrative privelege so that another user can't junk your system up.  The other command will update your system.  Also, go to:

System>Administration>Synaptic Package Manager and click "mark all upgrades"  Then click apply.  That will cover it from both command line and graphical user interface (GUI).

Just for fun, run update manager also.  Then everything should be current.  It will be a good learning experience as well :)

> **sarracenia88 said:**
> I just reinstalled ubuntu because other parts of it were messed up. Now it is working fine. I tried to install xgl without knowing how to. I really want to get xgl running though.

---

