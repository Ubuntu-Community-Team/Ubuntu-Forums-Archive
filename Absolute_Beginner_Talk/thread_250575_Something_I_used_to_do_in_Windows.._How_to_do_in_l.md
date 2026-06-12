---
title: "Something I used to do in Windows.. How to do in linux?"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by tsrajesh on 2006-09-04
Hi all,

I am just starting up with linux, and have started with ubuntu Dapper Drake. Here is my issue..

My ISP provides unlimited access from 2AM to 8AM, so normally, I put my system to hibernation, and use a scheduler program to wake up and start up my p2p or download programs (I'd rather have my computer wake up at 2AM instead of my waking up and turning it on :D ). Is there any such facility available in Linux? I see ubuntu 6 has Hibernate facility too.. This is one major thing i have to use a dual-boot linux & windows..

Thanks
Rajesh

---

### Post by whizbaby on 2006-09-04
What you are looking for is cron. At 

[http://doc.gwos.org/index.php/Crontab](http://doc.gwos.org/index.php/Crontab)

you are likely to find howto do it.
For hibernation look at this:
[http://packages.ubuntu.com/hoary/utils/hibernate](http://packages.ubuntu.com/hoary/utils/hibernate)
(in dapper it's similar, simply don't know a dapper page for this)
good luck!

---

### Post by skymt on 2006-09-04
[http://packages.ubuntu.com/dapper/utils/hibernate](http://packages.ubuntu.com/dapper/utils/hibernate) ;)

---

### Post by whizbaby on 2006-09-04
](*,) This proves that my brain's suspend mode is working properly.

---

### Post by tsrajesh on 2006-09-04
Thanks all,

I spent some time on cron (The tricky part was to get my GUI programs to work in cron). The only thing i am not able to do (yet) is to wake up from hibernation from cron...

Thanks & Regards
Rajesh

---

### Post by skymt on 2006-09-04
That would have to be done in hardware. Cron is in software, so if it's suspended, it can't run to un-suspend. It's like digging up a shovel.

---

### Post by tsrajesh on 2006-09-04
Here is the catch.. In windows, that was exactly i was able to do.. with "shut down expert"
[http://www.zylsoft.com/shutdown.htm](http://www.zylsoft.com/shutdown.htm)

---

### Post by skymt on 2006-09-04
Okay, I've done a little Googling on the topic. This all has to do with [ACPI](http://en.wikipedia.org/wiki/Acpi). It looks like the ACPI software in Ubuntu (acpi, acpid) doesn't support scheduled waking. So, it's just a matter of someone to do the coding. ACPI hacking is complex, beyond my small ability. Any volunteers?

---

