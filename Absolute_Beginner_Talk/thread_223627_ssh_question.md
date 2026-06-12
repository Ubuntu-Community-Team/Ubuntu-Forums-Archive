---
title: "ssh question"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by b1g4L on 2006-07-26
I know ssh isn't strictly related to linux or Ubuntu, but I have a quick question. Once I ssh into a remote linux server, I want to transfer a file from my local computer to the remote computer. I assume I would use the 'cp' command. Assume that I have a file named 'test.cpp' in my home directory that I want to transfer. Can you give me the command I would use. Thanks!

---

### Post by joft on 2006-07-26
Hi,

do you mean scp?

On **your** machine  (not on server) call

```

scp local.file user@remoteserver:/path/to/destination/on/remote

```

(replace user with your username on the remote machine, replace remoteserver with the server's ip or name, etc.)

---

### Post by tzulberti on 2006-07-26
I cannot look for the command but it is not cp, I thinks that it is "scp". If the other computer is on Windows, you could use WinScp.

---

### Post by b1g4L on 2006-07-26
Ok, thats what I needed. Thanks!

---

