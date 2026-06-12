---
title: "bash's source is not working in Gusty"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by uthpalawe on 2008-01-09
I am working with Gusty and I its source command is not working. I changed the .bashrc to export a dummy value (export A="message") but even after I execute source .bashrc the variable is initialised. I think this is a bug. When a new terminal is opened the variable is there. If anyone has a work around please make a post.
regards.
Uthpala

---

### Post by Cypher on 2008-01-12
The following seems to work for me..
```

Me@Dante:~$ uname -a
Linux Dante 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
Me@Dante:~$ cat /etc/issue.net 
Ubuntu 7.10
Me@Dante:~$ cat > foo.env
MYMSG="This is my message"
Me@Dante:~$ source ./foo.env
Me@Dante:~$ echo $MYMSG
This is my message
Me@Dante:~$ set | grep MYMSG
MYMSG='This is my message'
Me@Dante:~$ bash --version
GNU bash, version 3.2.25(1)-release (i486-pc-linux-gnu)
Copyright (C) 2005 Free Software Foundation, Inc.

```

---

### Post by uthpalawe on 2008-01-13
Yes, I tried your code and it works for me also. But the problem seems to lie with the .bashrc file. I added the line,
echo "Hello"
to .bashrc and exectuted source .bashrc but nothing happened. If the code is added to file like foo.env it will give the desired result. I guess this worked in the privious versions of Ubuntu and bash. Any ideas, Finally Cypher thanks for your reply.

---

### Post by uthpalawe on 2008-01-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/bash/+bug/160405](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/160405) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This bug was listed in launchpad. Anyway thanks for your quick feedback
[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/160405](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/160405)

---

