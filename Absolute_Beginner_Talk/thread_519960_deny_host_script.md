---
title: "deny host script"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-08-07
in my previous installation of ubuntu i had a scipt to block IP's who tried to SSh my machine and failed 5 times.

i have had 2 or 3 attempts at SSh entry and i cant find tht script!

anyone know where or how to do this?

---

### Post by milosz.galazka on 2007-08-07
[http://www.pettingers.org/code/sshblack.html](http://www.pettingers.org/code/sshblack.html) ?

---

### Post by skymera on 2007-08-07
thanks :)

---

### Post by hyper_ch on 2007-08-07
Fail2ban:  [http://www.howtoforge.com/fail2ban_debian_etch](http://www.howtoforge.com/fail2ban_debian_etch)  (it's in the ubuntu repos, so yu can just follow that more or less)

denyhosts: [http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts](http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts) (also in the repos --> that's the one I use)

---

### Post by skymera on 2007-08-07
dam the second one!
thats what i had before thankoo!

---

### Post by skymera on 2007-08-07
ok i followed this all and my last bit

/etc/init.d/denyhosts start

i get this result

```

root@scott-desktop:/etc/init.d# /etc/init.d/denyhosts start
starting DenyHosts:    /usr/bin/denyhosts.py --daemon --config=/usr/share/denyhosts/denyhosts.cfg
DenyHosts could not obtain lock (pid: 6939)
[Errno 17] File exists: '/var/run/denyhosts.pid'
root@scott-desktop:/etc/init.d# 

```

is that normal?

---

### Post by Cerny on 2008-03-19
This is the script i've been looking for.

---

