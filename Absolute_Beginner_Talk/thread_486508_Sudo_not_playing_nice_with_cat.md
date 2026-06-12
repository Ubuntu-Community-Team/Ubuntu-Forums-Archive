---
title: "Sudo not playing nice with cat?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by mynamewastaken on 2007-06-28
I'm sure theres a quick answer to this I don't know about :p , but when I try to do something like this:

```

tim@aerlinthe:~$ sudo cat /dev/null > /etc/issue
-bash: /etc/issue: Permission denied

tim@aerlinthe:~$ sudo less /dev/null > /etc/issue
-bash: /etc/issue: Permission denied

tim@aerlinthe:~$ sudo echo /dev/null > /etc/issue
-bash: /etc/issue: Permission denied

tim@aerlinthe:~$ ls -l /etc/issue
-rw-r--r-- 1 root root 19 2006-10-19 17:49 /etc/issue

```

I am unable to. Gives me permission denied when I try. I can edit the file by sudo'ing vim or logging into root just fine. Just wondering if there was something I was missing.

---

### Post by mvaniersel on 2007-06-28
I think sudo gives you permission for only the first part of the statement, so only for accessing /dev/null, not for writing to /etc/issue.

If you do it in two steps it should work though:

```
sudo cat /dev/null > tempfile.txt
sudo cp tempfile.txt /etc/issue
```

Or this should also work:

```

sudo -i
cat /dev/null > /etc/issue

```

---

