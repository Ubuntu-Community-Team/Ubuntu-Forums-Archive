---
title: "855GM, laptop and LCD"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by marusz on 2006-06-28
At start, i'm must sorry for my poor english, but this forum is my last hope. I'm old Slackware user, and i seek distro for my laptop. I choose Ubuntu, becouse it's very simple in instalation and configure all thinks without me. But, i have big problem.

I use noname laptop, with unkown LCD ventor name and strage mainboard. Orginally was made by Uniwill, in poland you can buy it from local owner. Whatever. Ubuntu installer was correct found LCD and refresh rate. Everythinks look nice. BUT! My LCD screen works on 100% brightness/contrast set! I can't look into, becouse it burne my eyes! I try search for something to adjust that settings, but no chance :/

I try tools like:
**ltpconf**
> X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


**ddccontrol**
> 
DDC/CI not found


So my question is: how adjust brightness and contrast on my LCD? I use ubuntu 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686 GNU/Linux.

Thanks for help.

---

### Post by Jagot on 2006-06-28
You should be able to use xgamma.  The default is 1.0, so:

```
xgamma -gamma 1.0
```

To increase brightness, increase the number, for example:

```
xgamma -gamma 1.2
```

And thus to decrease, for example:

```
xgamma -gamma 0.8
```

---

### Post by marusz on 2006-06-29
[QUOTE=Jagot]You should be able to use xgamma.  The default is 1.0[/QUOTE]

Yes, i manipulate xgamma befor i write post :) but, it's not resolve my problem. Summary: xgamma is not brightness or contrast.

Thanks for try to help.

---

### Post by SimzI on 2006-07-06
I have this EXACT problem. I've tryed everything and there's no way I can change the brightness levels. It's driving me mad! My laptop is a Packard Bell E2316 and I'm using Dapper. It's so annoying I wish somebody could come upw ith a solution for it..

Please reply back with ANY suggestions. 

SimzI.

---

