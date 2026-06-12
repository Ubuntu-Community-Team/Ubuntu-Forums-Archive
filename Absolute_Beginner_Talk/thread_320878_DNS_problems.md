---
title: "DNS problems"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by LookTJ on 2006-12-18
I have a static IP set. And on wireless.

whenever I restart the computer, it doesn't set the DNS servers, so I have to manually input the DNS server myself which I put my router's IP(192.168.0.1). But it still doesn't auto set the servers when I restart.

Any ideas?

EDIT: another thing, the distribution is dapper LTS.

Router manufactor is D-Link.

---

### Post by compwiz18 on 2006-12-18
My suggestion: input the DNS servers, and then **chattr +i /etc/resolv.conf**, which will lock the file, so that NO ONE will be able to edit it.  To undo it, just **chattr -i /etc/resolv.conf**.  This will unlock it so that root can edit it.

---

### Post by LookTJ on 2006-12-18
When i tried to lock it

here is the output:

```

taylor@dapper:~$ chattr +i /etc/resolv.conf
chattr: Inappropriate ioctl for device while reading flags on /etc/resolv.conf
taylor@dapper:~$ sudo chattr +i /etc/resolv.conf
chattr: Inappropriate ioctl for device while reading flags on /etc/resolv.conf
taylor@dapper:~$

```

---

### Post by compwiz18 on 2006-12-18
Weird, **sudo chattr +i /etc/resolv.conf** works fine on my computer.  What file system are you using? ext3, fat32, xfs?

---

### Post by LookTJ on 2006-12-18
> **compwiz18 said:**
> What file system are you using? ext3, fat32, xfs?I have a Ext3 filesystem. Is there something wrong with my resolv file?

EDIT: I removed and redid the file, then locked it. Let me try restarting my computer.

---

### Post by compwiz18 on 2006-12-18
Shouldn't be...

maybe try restarting and doing it again?

---

### Post by LookTJ on 2006-12-18
ok the locking worked. thank you for helping :D

---

### Post by compwiz18 on 2006-12-18
good :D

---

