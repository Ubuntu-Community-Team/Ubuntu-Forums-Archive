---
title: "Moving Files"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by gibs on 2006-09-04
Hello, I need to move around around 10gb from my remote machine to my linux box at my house. What would be the fastest solution? 


Thanks.

---

### Post by Miademora on 2006-09-04
One of many options would be to run on the remotebox

```
scp files_to_copy name_or_ip_of_linux_box:/tmp/
```

or run from your home

```
scp name_or_ip_of_remote_machine:/files_to_copy ~/
```

---

### Post by gibs on 2006-09-04
Okay, from my remote PC i'm sshing into my ubuntu box. Can I copy by file or can I move by directory. So if the remote pc's IP is 24.222.50.72 how would I do this? o.o; what would the command be?

---

### Post by Miademora on 2006-09-04
For copying a full directory use

```
scp -r 24.222.50.72:/directory/ /home/gibs/ 
```

---

### Post by gibs on 2006-09-04
actually, im having problems, any ideas how to rectify this?

There are no firewalls etc. and both can ping/tracert each other Oo;. 

ian@linuxbox:~/mp3$ scp -r 24.222.50.72:/D:/stuff/ /home/gibs/mp3
ssh: connect to host 24.222.50.72 port 22: Connection timed out

---

### Post by FuriousLettuce on 2006-09-04
If you can SSH into the box, but the scp command is giving you hassle, download WinSCP, a graphical SCP tool - it works just like an FTP transfer program. The only downside is that you can't use sudo commands or su commands to allow downloading of root-owned files. If you need to download anything owned by anyone else but you, the best thing to do is to gather it all in your home folder (chown it if you have to) then transfer it across.

---

### Post by gibs on 2006-09-04
> **FuriousLettuce said:**
> If you can SSH into the box, but the scp command is giving you hassle, download WinSCP, a graphical SCP tool - it works just like an FTP transfer program. The only downside is that you can't use sudo commands or su commands to allow downloading of root-owned files. If you need to download anything owned by anyone else but you, the best thing to do is to gather it all in your home folder (chown it if you have to) then transfer it across.

Thank you very much, this is exactly waht I needed

---

