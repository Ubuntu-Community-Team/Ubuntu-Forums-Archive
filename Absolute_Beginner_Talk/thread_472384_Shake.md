---
title: "Shake"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Darth_Maul on 2007-06-13
Is the available for Ubuntu  if so how do you download it.

---

### Post by tito13kfm on 2007-06-13
Found this on [http://www.apple.com/shake/](http://www.apple.com/shake/)
Shake for Linux is available through Apple Pro Resellers for $4999.

I'm not sure if there is a demo available for linux though.

---

### Post by deadgobby on 2007-06-13
[https://answers.launchpad.net/ubuntu/+question/7185](https://answers.launchpad.net/ubuntu/+question/7185)

---

### Post by Jerk1 on 2007-09-16
sorry to qualify so well for the newbie category, but I'm trying to get Shake up and running here and having no luck. The entire dir structure is copied to the /usr/local/ path but whenever I ./shake (even as sudo or su) I get /usr/local/shake/bin/shkx.exe: Command not found . The shkx.exe file is in the shake/bin dir. Even when I cd into the bin dir and try ./shake, same error. Little help here? Thx much in advance

---

### Post by Jerk1 on 2007-09-16
p.s. I have tried with csh as well. thx for any help

---

### Post by Bachstelze on 2007-09-17
You're on the 32bit version of Ubuntu, right ?

---

### Post by Jerk1 on 2007-09-17
64 bit

---

### Post by Jerk1 on 2007-09-17
bad?

---

### Post by Bachstelze on 2007-09-17
Then look no further. A 32-bit binary will not run on it.

---

### Post by Jerk1 on 2007-09-17
duh, thx a bunch, maybe I'll dual boot

---

### Post by AnRa on 2007-09-17
> **HymnToLife said:**
> Then look no further. A 32-bit binary will not run on it.That's not true! :???:

---

### Post by Bachstelze on 2007-09-17
> **AnRa said:**
> That's not true! :???:

All right, go ahead and explain to him how to make a chrooted 32-bits environment. Definitely not worth the hassle, to me.

---

### Post by Jerk1 on 2007-09-18
Hi again, well, after double checking with my IT guy at work, he assures me that, tho Shake will only run in 32 bit, it has no problem on a 64 bit OS, it's running on multiple machines at work this way. So that rules that out. Further, I have cp-r the untar'd dir to /usr/local, chmod'ed the permissions, installed csh, and a few yum libraries, really any suggestions I have been able to dig up in any of the forums I can find. I still just get /usr/local/shake/bin/shkx.exe: Command not found. when I ./shake. Argh. thx for any help

---

### Post by Jerk1 on 2007-09-18
p.s. just to be certain, I already installed a 32 bit stsyem, retraced all my steps, and recieved the same results. I'm back to 64 at this point

---

### Post by Jerk1 on 2007-09-20
nobody else out there has seen this?

---

### Post by Jerk1 on 2007-09-23
btw, I have also added /usr/shake_v4/bin/ to my path, still, to no avail. Same error, /usr/shake_v4/bin/shkx.exe: Command not found
sad clown

---

