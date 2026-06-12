---
title: "Buffer I/O error on device hda1"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by twshadow101 on 2006-12-27
Hey everyone, im in serious need of help to get my Ubuntu system working correctly again. I had to unplug the computer and move it, and when I hooked it up it reset the time some how and when I tried to change the time back it kept giving me a error window with no message. So I restarted the system and set the time in the bios menu. And, Ubuntu booted fine. But, once it got to the "Checking root file system..." is where my problems began. It had an error so it forced a check. The result from the check gave me,
> 
Buffer I/0 error on device hda1, logical block 1825198325.8%
Buffer I/0 error on device hda1, logical block 18251984
Buffer I/0 error on device hda1, logical block 18251985
Buffer I/0 error on device hda1, logical block 18251986
Buffer I/0 error on device hda1, logical block 18251987
Buffer I/0 error on device hda1, logical block 18251988...


It continues to climb with the last number changing each time I get the answer. Now, please bare in mind im totally new to Ubuntu and the entire Linux system. So im far from knowing what the heck this means. I have a lot of important files on my system, so I dont want to have to reinstall Ubuntu, if there is anyway of fixing this issue. Please someone help me out with detail steps. Thank you.

](*,) :confused: :-| :-k :(

PS: Im using, Ubuntu 6.06

---

### Post by taurus on 2006-12-27
Any chance you could accidentally knock the cable to the harddrive loose!  Can you boot with the LiveCD and see if it can see your harddrive at all with

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by nobloodshed on 2007-04-02
i installed the updates of last night, there were about 15 of them, updating some kind of libraries, and i get this error too.  i hibernated it, then it wouldnt wake up, so i shut it off and restarted it, it went to the thirty mounting check, and then it started dooing the same error that twshadow got

---

