---
title: "Is it ok to keep port 22 open"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by jonward690 on 2008-03-20
Ok have been using ssh a lot doing remote logins and I am just wondering is there a lot I amhaving to worry about with port22 open?I have been using Nomachine and it is great but it uses port 22 and I just don't want to see my system broke into or anything.

---

### Post by jordanmthomas on 2008-03-20
No, though you'll want to make sure you have a good password and keep an eye on failed logins (they'll be in /var/log/auth.log).
 
There's also a neat program called fail2ban that will ban people from your system after so many failed login attempts.

---

### Post by Oldsoldier2003 on 2008-03-20
> **jonward690 said:**
> Ok have been using ssh a lot doing remote logins and I am just wondering is there a lot I amhaving to worry about with port22 open?I have been using Nomachine and it is great but it uses port 22 and I just don't want to see my system broke into or anything.

if you are running a ssh server on port 22 its prudent to install [ DenyHosts]("http://ubuntuforums.org/showthread.php?t=450853") to prevent a brute force dictionary attack.

---

### Post by Oldsoldier2003 on 2008-03-20
> **jordanmthomas said:**
> No, though you'll want to make sure you have a good password and keep an eye on failed logins (they'll be in /var/log/auth.log).
 
There's also a neat program called fail2ban that will ban people from your system after so many failed login attempts.

it just dawned on me that the OP may be saying he is doing remote logins FROM his machine, in which case there is no worry whatsoever, unless he has somehow managed to install a sshd on his machine...

---

### Post by jordanmthomas on 2008-03-20
> **Oldsoldier2003 said:**
> it just dawned on me that the OP may be saying he is doing remote logins FROM his machine, in which case there is no worry whatsoever, unless he has somehow managed to install a sshd on his machine...

+1

[offtopic]
at that point, it's time for a reinstall
[/offtopic]

---

### Post by jonward690 on 2008-03-20
> **Oldsoldier2003 said:**
> it just dawned on me that the OP may be saying he is doing remote logins FROM his machine, in which case there is no worry whatsoever, unless he has somehow managed to install a sshd on his machine...

no no my bad i am logging into my own pc lol my bad

---

