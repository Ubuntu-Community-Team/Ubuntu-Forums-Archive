---
title: "I blanked /etc/hosts ... can I fix it without a CD?"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by OfficeLinebacker on 2006-04-01
So I can't sudo because 
 
sudo:  uable to look up machinename via gethostbyname()
 
Since I can't sudo, I can't edit the /etc/hosts, which is what I believe I need to do in order to fix this problem.
 
Running Dapper Flight 5 BTW.

---

### Post by 5-HT on 2006-04-01
What about trying to boot into recovery mode and editing the file from there?
Not sure if that would work.
If you do have a livce CD hanging around, it would be a quick fix.

---

### Post by OfficeLinebacker on 2006-04-01
OK looks like I needed to do some more searching.
 
recovery console allowed me to edit it and at least put in an entry for 127.0.0.1, but I've also lost a bunch of crap which I don't know if it's necessary.
 
So I can do apt-get and all that now but am worried about what else I lost (can't remember what else I deleted).

---

### Post by 5-HT on 2006-04-01
For the hosts file, should be something like this:
```
127.0.0.1 localhost.localdomain localhost <hostname> 
```

HTH

---

### Post by OfficeLinebacker on 2006-04-01
yeah bro that's what I have.  I think I should be good, but feel free to weigh in.
 
Also, nice user name.  I used to use 5-HTP.

---

