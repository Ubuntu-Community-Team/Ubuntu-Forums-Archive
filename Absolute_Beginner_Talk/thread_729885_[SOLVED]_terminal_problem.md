---
title: "[SOLVED] terminal problem"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by N1N31NCHN41L5 on 2008-03-20
I need help to fix this - PLEASE


E325: ATTENTION
Found a swap file by the name "/etc/apt/.sources.list.swp"
          owned by: root   dated: Wed Mar 19 22:53:54 2008
         file name: /etc/apt/sources.list
          modified: YES
         user name: root   host name: xubuntu
        process ID: 10733
While opening file "/etc/apt/sources.list"
             dated: Thu Mar 20 23:40:45 2008
      NEWER than swap file!

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/apt/sources.list"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/apt/.sources.list.swp"
    to avoid this message.
"/etc/apt/sources.list" 59L, 3148C
Press ENTER or type command to continue

---

### Post by ruy_lopez on 2008-03-20
Delete the temporary file '/etc/apt/.sources.list.swp'

Sometimes Vim will leave a temporary file by accident. You cannot reopen the file because Vim thinks you are still editing it. The solution is to delete the temporary file. (It is always mentioned by name in the warning.)

If you are worried that another process is editing the file, reboot, then delete it. By then the other process will be finished writing to the file.

---

### Post by N1N31NCHN41L5 on 2008-03-20
ok - ive rebooted like 5 times an still get that - how do i delete it

---

### Post by ruy_lopez on 2008-03-20
> **N1N31NCHN41L5 said:**
> ok - ive rebooted like 5 times an still get that - how do i delete it

```

sudo rm /etc/apt/.sources.list.swp

```

---

### Post by N1N31NCHN41L5 on 2008-03-20
ty

---

