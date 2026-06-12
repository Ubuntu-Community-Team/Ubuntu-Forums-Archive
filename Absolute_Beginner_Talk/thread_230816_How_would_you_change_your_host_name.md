---
title: "How would you change your host name?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-08-06
Hi, I was just wondering how I would change my host name....

---

### Post by neilp85 on 2006-08-06
Select System->Administration->Networking. Click on the General tab and you can change your hostname. I believe you have to restart your computer for this to take effect.

---

### Post by dusu on 2006-08-06
The command hostname does the job, have a look at the man page (type man hostname in a terminal).
In the man page they say :
[I]When  called  with one argument or with the --file option, the commands
set the host name or the NIS/YP domain name.
Note, that only the super-user can change the names.[/I]

---

### Post by zxcvbnm on 2006-08-06
Ok now I have a problem I can't use Sudo....how would I fix this....I keep getting the getbyhost error

---

### Post by zxcvbnm on 2006-08-06
Please help


./etc/hosts
```
127.0.0.1 localhost Ubuntu
127.0.1.1 Ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

/etc/hostname

```
Ubuntu
```

---

### Post by picpak on 2006-08-06
Boot into recovery mode (hit Escape on boot-up, and go to the kernel that says "recovery mode"). Once you're logged in, type

```
nano /etc/hosts
```

At the top of the file, put

```
127.0.0.1 localhost ubuntu
``` (Replace ubuntu with the host name that you want.) Reboot.

Hope that helps!

---

### Post by christhemonkey on 2006-08-06
EDIT: picpak's me way would actually fix the problem :D


As a temporary fix, 
i would reboot to recovery mode (select it from the grub menu whilst booting)
And then restore your original hostname.
```
hostname myhostname 
```

Did you change it originally with a command or through the GUI menu thing?

---

### Post by zxcvbnm on 2006-08-06
> Boot into recovery mode (hit Escape on boot-up, and go to the kernel that says "recovery mode"). Once you're logged in, type

Code:

nano /etc/hosts


At the top of the file, put

Code:

127.0.0.1 localhost ubuntu

(Replace ubuntu with the host name that you want.) Reboot.

Hope that helps!


But I alreeady have that in my /etc/hosts file

---

### Post by zxcvbnm on 2006-08-06
Sorry to bump this..As I have to have superuser privleges for a program I need to use.

---

### Post by MiserySignals on 2006-08-06
do you save in grub? cause i had put in 127.0.0.1 localhost ubuntu  and then just restarted my computer and that didn't do anything i still get gethostbyname when i sudo :confused:

---

