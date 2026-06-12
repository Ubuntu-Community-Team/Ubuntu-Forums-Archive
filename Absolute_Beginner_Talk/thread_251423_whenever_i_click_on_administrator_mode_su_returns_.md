---
title: "whenever i click on administrator mode su returns with an error"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by ashoka2004 on 2006-09-05
hi guys i am a total newbie and i really have no idea abt any commands etc plz... help me whenever i click on administrator mode it gives me a reply that su returned with an error 

i am not able to change my system time
i am not able to access the internet 

because whenever i click on administrator mode it gives me this error su returned with an errror 

also i think while i was installing kubuntu i changed the hostname to kaps i do not even know how to change the host name 

its not ubuntu i read in some forum that if the hostname is changed then this problem would be solved so i tried this command

su root sethostname ubuntu  -hostname was changed but i still have this problem of su returned with an error whenever i click on administrator mode

i changed the root password by going into recovery mode i cannot login to the root a/c from kdm

plz... help meeee


thanks

---

### Post by Iowan on 2006-09-05
Try **sudo** instead of **su root**. The root account is disabled (by default).> i changed the root password by going into recovery mode i cannot login to the root a/c from kdmOops... it may be enabled now.

---

