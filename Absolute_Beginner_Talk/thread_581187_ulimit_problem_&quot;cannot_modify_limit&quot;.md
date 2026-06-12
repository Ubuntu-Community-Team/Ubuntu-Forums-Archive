---
title: "ulimit problem &quot;cannot modify limit&quot;"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by sdahlin on 2007-10-19
I am getting a problem when I try to open a session as another user (oracle in this instance). I have gone into the /etc/security/limits.conf file and modified it with:

oracle soft nproc 2047
oracle hard nproc 16384
oracle soft nofile 1023
oracle hard nofile 65535

I have also modified the /etc/pam.d/login file with:

session required /lib/security/pam_limits.so
session required pam_limits.so

but when my .profile is run upon logging in or I enter "ulimit -u 16384" I am given the following message:

-su: ulimit: max user processes: cannot modify limit: Operation not permitted

I then tried tweaking the /etc/ssh/ssh_config file as one post indicated with:

"UsePrivilegeSeperation no"=20

This did not fix the problem. Any suggestions?

Thanks,
Steve

---

