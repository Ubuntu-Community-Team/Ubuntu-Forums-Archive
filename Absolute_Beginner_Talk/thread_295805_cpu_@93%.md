---
title: "cpu @93%"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2006-11-08
top - 06:45:18 up 29 min,  2 users,  load average: 0.01, 0.07, 0.06
Tasks: 111 total,   1 running, 110 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.3% us,  0.7% sy,  0.0% ni, 89.4% id,  0.0% wa,  0.3% hi,  0.3% si
Mem:   1035844k total,   444520k used,   591324k free,     6184k buffers
Swap:  3028212k total,        0k used,  3028212k free,   248684k cached

my cpu is running at 93% all the time ,i have tried top in terminal and got this readout ,the only problem i can see is with id ,but how do i find out what is maxing out my cpu,and how do i stop it:-k

---

### Post by civetta on 2006-11-08
Try System --> Administration --> System Monitor. Scroll down in the Processes tab and find the offending process.

---

### Post by lloyd_b on 2006-11-08
> top - 06:45:18 up 29 min, 2 users, load average: 0.01, 0.07, 0.06
Tasks: 111 total, 1 running, 110 sleeping, 0 stopped, 0 zombie
Cpu(s): 9.3% us, 0.7% sy, 0.0% ni, 89.4% id, 0.0% wa, 0.3% hi, 0.3% si
Mem: 1035844k total, 444520k used, 591324k free, 6184k buffers
Swap: 3028212k total, 0k used, 3028212k free, 248684k cached

my cpu is running at 93% all the time ,i have tried top in terminal and got this readout ,the only problem i can see is with id ,but how do i find out what is maxing out my cpu,and how do i stop it

According to the above:
9.3% us (User)
0.7% sy (System)
0.0% ni (Nice)
89.4% id (Idle)

"id" = "Idle" = "Not doing anything"

I don't see the problem.....

Lloyd B.

---

### Post by STREETURCHINE on 2006-11-08
i have done some fiddling and a rebbot so the ones i turned of must have solved the problem,should have checked after the reboot before posting so sorry all

---

### Post by glotz on 2006-11-08
I always have 100% processor usage and I love it. So should you all! Why? See my signature!

---

