---
title: "Synaptic problems"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by Matt Houston on 2005-11-19
Hi, 

Something strange has happened, when I try run synaptic I get the following:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
```

So when I try run that in the terminal I get the following:

```
requested operation requires superuser privilege
```

I can't help but get the feeling it's somehow related to this problem:

[http://ubuntuforums.org/showthread.php?t=92285&goto=newpost](http://ubuntuforums.org/showthread.php?t=92285&goto=newpost)

Any ideas?

---

### Post by estel on 2005-11-19
When you run it in the terminal, you need to preface the command with "sudo" and then use your root password. This does it as "superuser"

Run the command:
```
sudo dpkg --configure -a
``` instead

---

