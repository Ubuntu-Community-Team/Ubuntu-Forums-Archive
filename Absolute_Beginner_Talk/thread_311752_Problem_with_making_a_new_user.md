---
title: "Problem with making a new user"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-12-03
Hello,

If I make a new user, it cannot be saved at memory and if I come back to Users and Groups window I can't see it more.
Could you say me what is wrong?

Thanks

---

### Post by taurus on 2006-12-03
How did you create a new user?  A little more info would be more helpful...

---

### Post by linux-beginner on 2006-12-03
By System tab.
System->Administration->Users and Groups->add user

---

### Post by taurus on 2006-12-03
Applications -> Accessories -> Terminal
```
sudo useradd -m john
sudo passwd john
(assuming john is what you want to create...)
```

---

### Post by linux-beginner on 2006-12-03
If I type "sudo useradd -m john" I get the massage that the user john exists. But I cannot see it in the window of Users and Groups!!

---

### Post by taurus on 2006-12-03
What's the output of this command then?

```
cat /etc/passwd
```

---

### Post by linux-beginner on 2006-12-03
```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:101:101::/nonexistent:/bin/false
syslog:x:102:102::/home/syslog:/bin/false
klog:x:103:103::/home/klog:/bin/false
cupsys:x:100:106::/home/cupsys:/bin/false
messagebus:x:104:107::/var/run/dbus:/bin/false
haldaemon:x:108:108:Hardware abstraction layer,,,:/var/run/hal:/bin/false
hplip:x:105:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:106:111:Gnome Display Manager:/var/lib/gdm:/bin/false
mehdi:x:1000:1000:Mehdi,,,:/home/mehdi:/bin/bash
smmta:x:109:115:Mail Transfer Agent,,,:/var/lib/sendmail:/bin/false
smmsp:x:110:116:Mail Submission Program,,,:/var/lib/sendmail:/bin/false
mysql:x:107:113:MySQL Server,,,:/var/lib/mysql:/bin/false
avahi:x:111:117:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
guest:x:1001:1000:guest,,,,:/home/group:/bin/bash

```

---

### Post by taurus on 2006-12-03
> **linux-beginner said:**
> ```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:101:101::/nonexistent:/bin/false
syslog:x:102:102::/home/syslog:/bin/false
klog:x:103:103::/home/klog:/bin/false
cupsys:x:100:106::/home/cupsys:/bin/false
messagebus:x:104:107::/var/run/dbus:/bin/false
haldaemon:x:108:108:Hardware abstraction layer,,,:/var/run/hal:/bin/false
hplip:x:105:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:106:111:Gnome Display Manager:/var/lib/gdm:/bin/false
mehdi:x:1000:1000:Mehdi,,,:/home/mehdi:/bin/bash
smmta:x:109:115:Mail Transfer Agent,,,:/var/lib/sendmail:/bin/false
smmsp:x:110:116:Mail Submission Program,,,:/var/lib/sendmail:/bin/false
mysql:x:107:113:MySQL Server,,,:/var/lib/mysql:/bin/false
avahi:x:111:117:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
guest:x:1001:1000:guest,,,,:/home/group:/bin/bash

```

You don't have user john on your machine!!!  The only two users I can see are mehdi & guest...

---

### Post by linux-beginner on 2006-12-03
With john I meant guest.
Sorry that I wasn't clear!

---

### Post by taurus on 2006-12-03
> **linux-beginner said:**
> With john I meant guest.
Sorry that I wasn't clear!
Looks like guest belongs to group mehdi, 1000!!!

---

### Post by linux-beginner on 2006-12-03
I have also to say that I can't remember that I ever made a "root" account. I don't know the password of the "root"!!!

---

### Post by taurus on 2006-12-03
It didn't ask you for a root's password.  There is a root account but it's locked so if you need to write something to the system, you need to use sudo...

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by linux-beginner on 2006-12-03
To my stupefaction, I see now that the guest user is to see at the window "Users and Groups".
That's right, you didn't ask to password of root. But what is the usefulness of a root account when I don't know its password?

---

### Post by linux-beginner on 2006-12-03
To taurus: Thanks.

---

### Post by taurus on 2006-12-03
You need root account so when you boot into recovery mode, you would become root!!!  Otherwise, please use the sudo command...

---

