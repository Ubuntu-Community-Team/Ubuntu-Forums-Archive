---
title: "samba dependencies problems"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by kane77 on 2007-02-10
there were few new upgrades available so I decided to upgrade, but among them was one for samba that has had unmet dependencies...

now every time I try to run "apt-get install -f" i get this:
```
(Reading database ... 136107 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.2_amd64.deb) ...invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

I cannot remove the package (i get an error..) I cannot upgrade.. and it always gives me this message... what can I do??

---

### Post by Jussi01 on 2007-02-10
You could try going into synaptic - > edit -> fix broken packages...

---

### Post by kane77 on 2007-02-10
> **Jussi01 said:**
> You could try going into synaptic - > edit -> fix broken packages...

I get this: ```
E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_amd64.deb: subprocess new pre-removal script returned error exit status 102
```

and on the terminal screen the same error as before...

---

### Post by Jussi01 on 2007-02-10
Im sorry, I dont have any more answers for you, hang in there though, Im sure there is someone out there who can help. If you need help in a hurry you can try going on irc to #ubuntu.

Cheers


Jussi

---

### Post by sonmez on 2007-02-10
I am having the same problem here. I am running Dapper.

---

### Post by sonmez on 2007-02-10
This seems to solve the problem
[https://answers.launchpad.net/ubuntu/+ticket/1556](https://answers.launchpad.net/ubuntu/+ticket/1556)

---

### Post by kane77 on 2007-02-10
> **sonmez said:**
> I am having the same problem here. I am running Dapper.

yeah, I'm running dapper too...
i'll try your solution and let know if it's working...

---

### Post by kane77 on 2007-02-10
YAY!! it works!! 

thanx man!

heh I wouldn't have thought about doing that!!

---

### Post by Mike_Longbow on 2007-02-17
:D Thank you, that link worked for me.
I tought it would take me a long time to fix it...

---

### Post by ivodalves on 2007-04-04
Hi,

Please check this:

ls -l /etc/rcs.d/k09samba

if the output is: lrwxrwxrwx 1 root root 6 2007-04-03 16:16 /etc/rc2.d/K09samba -> /samba

remove K09samba because this link can not "point" to samba (crazy sh#"$%t) :

rm /etc/rc2.d/k09samba

and it's done, now you can upgrade, remove samba ... etc etc!

---

