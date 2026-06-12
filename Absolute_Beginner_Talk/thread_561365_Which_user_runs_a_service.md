---
title: "Which user runs a service"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by pdoukas on 2007-09-27
Hi,

Would someone mind posting the command to help me find out what user is running my apache? I think it is the default apache user but I do not know and I need to find out who it is and what groups it is in and what permissions it has.

I have an app that I need to chown permissions on and I want to make sure I'm setting it as the same as the apache userrunning my apache.

TIA,

Pete

---

### Post by hyper_ch on 2007-09-27
should be by default:   www-data

---

### Post by pdoukas on 2007-09-27
Thanks for telling me who it is. But in truth, it may not be that user which is why I asked for someone to please post the command so I CAN  see who it really is. 

If I do not know the command I cannot learn how to use linux?1

Pete

---

### Post by mysticmatrix on 2007-09-27
> **pdoukas said:**
> Thanks for telling me who it is. But in truth, it may not be that user which is why I asked for someone to please post the command so I CAN  see who it really is. 

If I do not know the command I cannot learn how to use linux?1

Pete

Open System Monitor(System --> Administration.)

Click on process tab, select show all processes. Find out the appropriate program and see which user is running it.

BTW, 90% of work can be done in slow GUI way, and most power user don't prefer it.

---

### Post by RamsesII on 2007-09-27
Hello pdoukas,

If your apache server is running, it means there's a processus running on. What you can do is to print in a console the list of all the processes running on your computer. Type :
ps aux| grep "apache"
You will have the line related to your apache server processus, and all the information you need about the user.

---

### Post by notwen on 2007-09-27
```
ps aux
```

Sould bring up running processes and the user that initiated them. =]

---

### Post by RamsesII on 2007-09-27
> **notwen said:**
> ```
ps aux
```

Sould bring up running processes and the user that initiated them. =]
Good,
So fundamentally notwen you agree with me. ;-)

---

### Post by pdoukas on 2007-09-27
Thanks so much, was exactly what I was looking for however now I am just as confused as I was earlier. I'm going to make another post here shortly maybe someone will be able to assist me further. I'm not a linux user, and I'm doing things commnad line on the LAMP version.

Thanks again!!

Pete

---

### Post by RamsesII on 2007-09-27
You're welcome.

---

