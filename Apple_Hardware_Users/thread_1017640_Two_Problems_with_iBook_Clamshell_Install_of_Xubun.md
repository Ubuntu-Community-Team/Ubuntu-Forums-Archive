---
title: "Two Problems with iBook Clamshell Install of Xubuntu, Sleep, and Boot to Busy Box"
date: 2008-12-21
forum: Apple Hardware Users
---

### Post by Mars478 on 2008-12-21
Hello All.
I am relativley new to Xubuntu etc, so i have a few problems. First Off the more important problem that I would like to solve first is that when I sleep the clamshell by closing the lid, when i wake it up the screen is in gray, the top two corners of the screen are zoomed in on and are on top of eachother, all in all it is a mess, I cannot do anything and i have to hard reboot.
Number two, I know there is a fix to this by making a new kernel, but i am afraid i will kill my install, I have the problem where i get the Xubuntu boot screen but it just stays there. After a while it drops to the BusyBox Line. I enter the Code  ```
modprobe ide_core
```  and then ```
exit 
```and it boots normally. But I am giving this machine to a person who knows nothing about computers, she would die if she had to enter that code at the start! 
Now I really could get around the BusyBox Shell thing, but The sleep REALLY annoys me. Thanks in advance for your help.! ):P
Update 1: My Machine is a 300MHZ Indigo Clamshell, PowerPC with 160MB of Ram, 3 GB Hard Drive, I will upgrade all of these in the future. Thanks
Update 2: Attached is a picture of what it looks like when it wakes up from sleep :rolleyes:

---

### Post by Mars478 on 2008-12-21
Anyone? :/

---

### Post by stream303 on 2008-12-22
Ah, try this:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Gutsy%20CDs%20will%20not%20boot](https://wiki.ubuntu.com/PowerPCKnownIssues#Gutsy%20CDs%20will%20not%20boot)

Just underneath the "Gutsy Cd won't boot" are the instructions for busybox issues to make the modprobe ide-core permanent.

I notice you are using an underscore rather than a hyphen with ide_core.  I have also seen it as ide-core.  Might be something to doublecheck.

At any rate, adding modprobe ide-core (or ide_core) to /etc/initramfs-tools/modules , and then run

```
sudo update-initramfs -u
```

should keep you from having to type that at boot time.

---

### Post by Mars478 on 2008-12-22
Thanks, I have done what it said there. I edited all the files correctly put i forgot the last part where you do the initramfs -u thing. 
So now i have the last problem which SUCKS! Do you know how to fix it, becuz i have to get it by christmas!:lolflag:

---

### Post by Mars478 on 2008-12-23
Gonna Bump this, I have installed 8.04 HArdy and now suspend works perfectly, but not when i close the lid, when i close the lid, either the screen stays on, or it just goes off but i can still hear it doing things, so is my only solution to click sleep from the menu or is there something i can do to fix this. Sorry for my n00bish questions...

---

