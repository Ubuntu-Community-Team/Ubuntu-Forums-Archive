---
title: "SSH question..."
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2006-06-12
Is there a way to log off someone that has remotely connected to my pc?  I'm running tinyproxy over ssh so peps at my office can look at what they want.  If someone is logged on for longer htan i would like, i would want to log off for them.  Thanks.

---

### Post by nanotube on 2006-06-12
[QUOTE=echo $USER]Is there a way to log off someone that has remotely connected to my pc?  I'm running tinyproxy over ssh so peps at my office can look at what they want.  If someone is logged on for longer htan i would like, i would want to log off for them.  Thanks.[/QUOTE]
run command
```
sudo ps -u username |grep sshd
```
(replace username with the actual user that you want to log off) that will list their ssh login process. 
then just do a 
```
sudo kill -9 PID
```
where PID is the process id of the sshd process that you found from the previous command.

---

### Post by echo $USER on 2006-06-12
Sweet, worked like a charm.

---

### Post by nanotube on 2006-06-12
[QUOTE=echo $USER]Sweet, worked like a charm.[/QUOTE]
cool ;)

---

