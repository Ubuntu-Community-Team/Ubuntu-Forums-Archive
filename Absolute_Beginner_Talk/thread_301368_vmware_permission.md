---
title: "vmware permission"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-11-17
I am trying to fire up WINDOZE XP on my Ubuntu Dapper system. I am getting flack from the VMWARE player about permissions. Here are 2 screenshots to help. I am using Dapper (anyone recommend Edgy???).

---

### Post by Bachstelze on 2006-11-17
While you're logged in as root, do

```
chown -R your_login_here:your_login_here /home/your_login_here
```

If your files are owned by root, it means you created them being root, which is a very bad idea.

---

### Post by saintj0n on 2006-11-17
I have read that you should only use root when doing administrative tasks. Why would this not include installing programs? If I use sudo, why wouldn't it work? 

Btw, I did what you said and it did work. It says it cant find /dev/vmnet8 and that eth0 will start disconnected....Never used vmware before so I dont know what that is either...

---

### Post by BLTicklemonster on 2006-11-17
add a launcher to your desktop or taskbar with the command 

```

sudo vmware
```

I can't use vmware unless I sudo it.

*EDIT:

By that, I mean right click on your desktop or panel/taskbar, and choose to create a launcher (use terminal to launch it option) and enter that code up there. Or just open a terminal and type that in if you are having a hard time creating a launcher.

---

