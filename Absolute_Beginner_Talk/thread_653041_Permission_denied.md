---
title: "Permission denied"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by haifisch27 on 2007-12-29
The task that I'm doing might not be that basic, but the error message could be. Therefore I'm posing this question here. I'm using Ubuntu 7.10 and want to use my Netgear WG111v2 wireless adapter. In other threads I found that I have to do the following with the netwg111.inf driver file

ndiswrapper -i netwg111.inf

which should install the driver in Ubuntu. However, I received the reply

couldn't create /etc/ndiswrapper/netwg111: Permission denied at /usr/sbin/ndiswrapper-1.9 line 152 

What could be the problem? :confused:

Thanks,
Michael

---

### Post by FuturePilot on 2007-12-29
Try the command by prefixing it with sudo
```
sudo ndiswrapper -i netwg111.inf
```

---

### Post by taurus on 2007-12-29
Try putting the sudo in front of the command since you don't have permission to write outside of your $HOME directory.

```
**sudo** ndiswrapper -i netwg111.inf
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

