---
title: "SSH remote connectivity problem"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-08-27
Im using WinSCP to remotely access two ubuntu computers (ubuntu1 and ubuntu2) from a windows pc via ssh.  All three computers are on my little home network.  On the home network, i can remotely access ubunt1 and ubunt2 from the windows pc with no problem.  From an offsite location however, i can only remotely access ubuntu1 but have problems with ubuntu2.  I port forwarded ports 22 and 23 for ubuntu 1 and port forwarded 24and 25 for ubuntu2.  Is there a way that i can set up ssh on ubuntu2 to operate on ports 24 and 25 instead of the standard ssh ports? If so I would like for someone to tell me how to do this.  I don't think I can port forward the same port for two different PC's.   I want to do this because I suspect I'm having a forwarding problem.  Any help will be appreciated.

Thanks in advance,

VC

---

### Post by Malibu Illusion on 2007-08-27
```
sudo vi /etc/ssh/sshd_config
```

You can edit the listen port in there.

Port 23 is the telnet port by default and does not need to be open to remotely connect to an SSH daemon.  SSHds require one port which, by default, is 22.  I recommend not using any SSHd with the default port settings, lest you be a quick and easy target for those running random brute force SSH attacks against servers.

Take care.

---

### Post by kevdog on 2007-08-27
Kind of just to reiterate -- you only need one port open for ssh (its not like ftp).  By default its 22.

If you look in
/etc/ssh/sshd_config

You will find a line that states
Port 22

I would change this to a non standard port such as
222 or 
2222

Then port forward the selected port on the router to the computer.  

Although its not absolutely necessary, it would be best if you assigned your computers static IP addresses.  That way the port forwarding from the router to the machine IP address will always be correct.

---

### Post by KCPokes on 2007-08-27
Another option, depending on your setup is that some routers/firewalls have the ability to translate ports, thus you can open a couple ports externally, say 222 and 223, forwarding those ports to port 22 for each respective machine (i.e port 222 would go to port 22 for ubuntu-1, and port 223 would go to port 22 for ubuntu-2).

---

### Post by videocheez on 2007-08-28
> **Malibu Illusion said:**
> ```
sudo vi /etc/ssh/sshd_config
```

You can edit the listen port in there.

Port 23 is the telnet port by default and does not need to be open to remotely connect to an SSH daemon.  SSHds require one port which, by default, is 22.  I recommend not using any SSHd with the default port settings, lest you be a quick and easy target for those running random brute force SSH attacks against servers.

Take care.


Ok I'll try your advice but why can't i just type
```
sudo gedit  /etc/ssh/sshd_config
```

---

### Post by Malibu Illusion on 2007-08-28
You can edit it with whatever you like, I personally just find it easier to edit it with vi using the command line. 

You shouldn't use "sudo" to open graphical applications, though.  If you want to use gedit:

```
gksudo gedit /etc/ssh/sshd_config
```

kdesu if you're using KDE.

---

### Post by hyper_ch on 2007-08-28
on a sidenote: port 25 is used for smtp

---

### Post by videocheez on 2007-08-28
> **Malibu Illusion said:**
> You can edit it with whatever you like, I personally just find it easier to edit it with vi using the command line. 

You shouldn't use "sudo" to open graphical applications, though.  If you want to use gedit:

```
gksudo gedit /etc/ssh/sshd_config
```

kdesu if you're using KDE.

Ok.  I did not know what vi was.  As a side question, why can't or shouldn't use sudo to open graphical applications?

---

### Post by videocheez on 2007-08-28
> **hyper_ch said:**
> on a sidenote: port 25 is used for smtp

Thanks for the info.  and thanks for everyone who provided me with advice on this matter.  Once again, more successful advice on how to do something that I have no clue about was obtained from this forum.:)

---

