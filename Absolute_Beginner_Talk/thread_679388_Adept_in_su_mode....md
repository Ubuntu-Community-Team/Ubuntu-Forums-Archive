---
title: "Adept in su mode..."
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by no-box on 2008-01-26
Hi, I'm having problems invoking adept in su mode. I have cheked the other threads regarding this and have tried the solutions, none of which work for me. Can anyone help me ?
Cheers, no-box

---

### Post by jken146 on 2008-01-26
```
kdesu adept
```

---

### Post by no-box on 2008-01-26
...ok, that gave me this->
root@****:/home/jon# sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
root@****:/home/jon# sudo adept
sudo: adept: command not found
root@****:/home/jon# adept
bash: adept: command not found
root@****:/home/jon# kdesu adept
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Launched ok, pid = 6694
OggS-SEEK: at 704 want 47096 got 23104 (diff-requested 46392)
OggS-SEEK: at 47040 want 1032 got 0 (diff-requested -46008)
sudo: adept: command not found




...havn't got a clue what's happening...

---

### Post by Kralizec on 2008-01-26
Adept isn't installed. Or its not installed in a place that your command line can find it (i.e. /bin, /usr/bin, /usr/local/bin, etc.) Are you sure you installed it? and if so, did you install it from source or from the repositories?

---

### Post by swoll1980 on 2008-01-27
in kubuntu adept is installed by default

---

### Post by emarkd on 2008-01-27
Are you running Ubuntu or Kubuntu?  If you're running Ubuntu, you want Synaptic, not Adept.  There's a menu item at System > Administration > Synaptic Package Manger or you can start it from the command line (in a graphical environment) using
`
```
gksu synaptic
```

---

### Post by no-box on 2008-02-07
I am running ubuntu....thanks for the advise so far. I'll have a look at/for synaptic.
Cheers, no-box

---

