---
title: "Failed to start /  bus failed"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-02-12
I have an error at ubuntu start up, system can not login

It prompts to root without coming to login screen. I get the following error:
```
sys/devices/platform/i8042/serio0/serio2/bus failed
check, force check
serio2 bus failed checking root system
/dev/sda3 contains a file system with errors, check forced.
Inode has illegal blocks
/dev/sda3: unexpected inconsistency: run fsck manually
fsck died with exit status 4
the reoot filesystem  is currently mounted  in read-only mode
maintenance shell will now be started
bash: no job control in this shell
bash: groups: command not found
bash:lesspipe: command not found
bash: dircolors: command not found 
root@test:~#
```

would you SHOW the steps?
thank you
findik1

---

### Post by jpeddicord on 2007-02-12
As soon as you see root@test:~#, type in "fsck" and press <Enter>. That might fix your problem. It attempts to check the file system again and try to fix any errors. If it still doesn't work, post back here.

Jacob

---

### Post by findik1 on 2007-02-14
yes it worked! thanks. Though I dont understand why it gave error, I just started brand new day with that error.

---

