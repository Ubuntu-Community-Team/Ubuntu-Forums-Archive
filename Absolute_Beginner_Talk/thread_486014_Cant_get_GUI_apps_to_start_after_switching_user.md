---
title: "Cant get GUI apps to start after switching user"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by s_raghu20 on 2007-06-27
Hi Friends,

Here's a small view from my terminal

```
oracle@raghav-ubuntu:~$ echo $DISPLAY
:0.0
oracle@raghav-ubuntu:~$ su - owb
Password: 
owb@raghav-ubuntu:~$ export DISPLAY=192.168.0.143:0.0
owb@raghav-ubuntu:~$ xcalc
Error: Can't open display: 192.168.0.143:0.0
owb@raghav-ubuntu:~$ export DISPLAY=127.0.0.1:0.0
owb@raghav-ubuntu:~$ xcalc
Error: Can't open display: 127.0.0.1:0.0
owb@raghav-ubuntu:~$ 
```

A few questions : 

[LIST=1]
[*]What could be the reason that my display variable is not set properly.. i mean using the dynamic ip address ?
[*]If thats not the problem, what else is wrong with my system.. I mean what needs to be fixed to get it working fine.. ?? :(
[/LIST]

Would appreciate any  help ..

regards
raghav..

---

### Post by jrib on 2007-06-27
```

+(jrib@castelo:~)
% echo $DISPLAY                                               (22:41/10107)
:0.0
+(jrib@castelo:~)
% xhost +local:                                               (22:41/10108)
non-network local connections being added to access control list
+(jrib@castelo:~)
% su - tester                                                 (22:41/10109)
Password: 
tester@castelo:~$ export DISPLAY=:0.0
tester@castelo:~$ gedit

```

I set my display a little differently.  Also, be sure you use xhost or xauth appropriately before you switch users.

---

### Post by s_raghu20 on 2007-06-28
Thanks.

You suggestion about ```
xhost +local:
``` worked perfectly for me.

Thanks a ton.

regards
raghav..

---

