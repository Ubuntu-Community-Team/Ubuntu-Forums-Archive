---
title: "Dual boot winxp/ubuntu with Dell inspiron 1501"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by exsencon on 2008-02-04
I am thinking of installing Ubuntu on my Dell laptop Inspiron 1501.
For starters I got Gparted live CD and went to repartition the HD. Being a Dell PC the HD already has 3 primary partitions

sda 1 109MB (dell utilities I think)
sda 3 3GB (dell recovery)
sda 2 109GB NTFS with winxp on it

I resized the windows partition in half so I have some 56GB for my Linux.
Then I went on creating the first partition (root) of 8GB but after that you are not allowed more primary partitions since 4 is the maximum.
So I was thinking of just making my 56GB unallocated space into one extended partition  and put the ubuntu partitions(root,swap,home and maybe shared) in there as logical partitions.
Now, before I do that I just want to know if that would be correct. I know linux installs in primary or logical partitions but I am not sure in the case of dual boot. 
After I resized the winxp partition I rebooted and windows did its check and everything was OK so I would like to move on now but just asking before I do something stupid!:confused:
Thanks

---

### Post by Rocket2DMn on 2008-02-04
I don't think you will have problems, it should just make logical partitions, I've seen drives with many more partitions than that without doing anything special.  Did the installer SAY there were too many partitions?
Also, you can have everything under / but you still need a separate swap partition.  A separate /home partition is not necessary, just convenient for some people.

---

### Post by pdub on 2008-02-04
That is exactly what I did with my Dell D820. Ubuntu 7.10 dual boot with XP Pro.

---

### Post by exsencon on 2008-02-04
Thanks pdub and Rocket2DMn, you put my mind at rest! I will proceed tomorrow (it's 3AM here) and let you know how it went

---

### Post by exsencon on 2008-02-05
Here I am again and it all went beautifully! I did it in the extended partitions (3: root-swap-home) then just followed the installer. It recognized my logical partitions without any problems. Reboot after install and I had my dualboot between Kubuntu 7.10 gutsy (I preferred the KDE desktop) and WinXP. Great!
Going to install wireless with ndiswrapper now. Thanks for your advice.

---

### Post by pdub on 2008-02-05
Glad to here that it went well.

---

