---
title: "Sudo not functioning"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by wwitthoff1 on 2006-04-20
hello,

my sudo command is not functioning.  when i try to use it in terminal, all i get as output is: sudo: must be setuid root

I have looked at other threads and have entered my username expressly in the /etc/sudoers file using visudo but to no avail.  any help would be appreciated.

Thanks,

Will

---

### Post by unbuntu on 2006-04-20
try this:
from:  [http://www.sudo.ws/pipermail/sudo-users/2005-April/002470.html](http://www.sudo.ws/pipermail/sudo-users/2005-April/002470.html)
> 
> If sudo is installed as /usr/bin/sudo, then run
> 
> chmod 4111 /usr/bin/sudo
> 
> as root.


---

### Post by wwitthoff1 on 2006-04-20
Thanks it worked.  Note to self,  self dont tweak with permissions.

---

### Post by BLTicklemonster on 2006-09-05
In case any noobs come in wondering how to fix this here's what I did:

I went into the recovery console (reboot, and chose recovery console in case you didn't catch on to how to do that), and typed 

ls -l usr/bin/sudo 

and the readout looked fine, like this 

```
-rwsr-xr-x 1 root root 93844 2006-09-05 08:41 /usr/bin/sudo
```

but I knew better...


so I put 

chwon root:root /usr/bin/sudo
then
chmod 4755 /usr/bin/sudo

then I typed 

reboot


and I now have sudo again.

---

