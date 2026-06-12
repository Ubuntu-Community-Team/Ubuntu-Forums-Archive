---
title: "SSH from XP to Ubuntu"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Frank_F on 2007-07-29
Hello

Thanks to everones suggestions, I was successfully able to install SSH and get it working. However, unlike Telnet, which is installed on my XP machine, SSH is not. How would I go about SSH from an XP machine to  my Ubuntu machine which has SSh running ? 

In addition, if I did this outside my network, do I need to open any ports on my router ?


Thanks,
Frank

---

### Post by tgm4883 on 2007-07-29
Get Putty
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

The standard port for SSH is 22

---

### Post by Emerzen on 2007-07-29
You have several options.  If you want a GUI in Windows, install WinSCP.  If you simply want a CLI, you can install PuTTY.  You'll have to open port 22 on the server (Ubuntu) end if I understand your setup correctly.

---

### Post by ekravche on 2007-07-29
> **tgm4883 said:**
> Get Putty
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

The standard port for SSH is 22

what he said. Get putty

---

### Post by hyper_ch on 2007-07-29
and you need to install the openssh-server on your linux box:

```

sudo aptitude install openssh-server

```

---

