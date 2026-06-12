---
title: "Run time value error"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Tids on 2007-05-08
Hi there,

I need help. I dont know much about Linux servers. Our server here at work crashed because of a power 
failure. It required us to do a file system check and I used this command fsck. After doing I rebooted the server 
and typed in fsck /var. Then I rebooted the server again. The machine is still workin now but I can not log in.
Everytime I try to log in it gives me this error: Scheduled_timeout;runtime value fffffff 9CC01D30c0.
Please help, I dont where to go from here.:confused: 

Thank you
Tids

---

### Post by dstew on 2007-05-08
Are you trying to log in with ssh? If so, you might have a problem with the /etc/ssh/sshd_config file. Can you get this file out of your machine and post its contents?

---

### Post by Tids on 2007-05-09
Hi 

Thank you for replying. No I am not using ssh to login.  

Tids

---

