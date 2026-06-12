---
title: "unable to login to administrative account"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by ejoftiduttu on 2008-02-10
i selected the recovery mode n tried these commands

useradd admin dinesh
shutdown -r now.

Then i was able to get into d account named dinesh. But it wont have administrtative powers. How can i give this account the administrative power.

---

### Post by taurus on 2008-02-10
Why are you starting up a new thread when you could have continued with the previous one?

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
id
```

---

### Post by ejoftiduttu on 2008-02-10
dinesh@SHADOWMAN:~$ id
uid=1000(dinesh) gid=1000(dinesh) groups=1000(dinesh)

n dis user wont have administrative power..I want to make an account with administratiove power..

---

### Post by taurus on 2008-02-10
Boot into recovery mode from GRUB menu and edit /etc/group

```
nano -Bw /etc/group
```
Scroll down near the end and add **dinesh** to the end of **admin**.  Save it with <Ctrl>o and exit with <Ctrl>x.  Reboot 

```
shutdown -r now
```
and see if group admin appears from the output of this command.

```
id
```

---

### Post by ejoftiduttu on 2008-02-11
I did the above thing. n der was no such fiile...named group..

---

### Post by taurus on 2008-02-11
Post the output of this command from a terminal.

```
cat /etc/group
```

---

