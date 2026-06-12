---
title: "My sudo don't working"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by edu.reche on 2006-01-16
Hello people... 
I was playing with my users and groups, permissions and etc, when I did something wrong and my [COLOR="Red"]**sudo**[/COLOR] command stopped.

Now, when I try to execute any command I've the following message:

```
sudo: /etc/sudoers is owned by gid 1002, should be 0
```

What can I do?

Thanks

Eduardo :confused:

---

### Post by Inarius03 on 2006-01-16
try:

su
visudo

Paste contents here

---

### Post by edu.reche on 2006-01-16
I try, but I haven't set up a root password before... 
So, I think my problem just have a solution: format and reinstall ubuntu... 
Is this?

---

### Post by edu.reche on 2006-01-16
I try, but I haven't set up a root password before... 
So, I think my problem just have a solution: format and reinstall ubuntu... 
Is this?

---

### Post by edu.reche on 2006-01-16
I try, but I haven't set up a root password before... 
So, I think my problem just have a solution: format and reinstall ubuntu... 
Is this?

---

### Post by kaamos on 2006-01-16
You can boot in recovery mode to get root access. Just select that in grubs menu.

---

### Post by edu.reche on 2006-01-17
Ok Kaamos, I did!

Thank you guys.

---

