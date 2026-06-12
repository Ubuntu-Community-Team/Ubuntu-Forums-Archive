---
title: "new install !"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by nivesh on 2007-12-30
hey guys,

I just completed installing gutsy gibbon on my old hp ze5375US laptop. Well everything worked great the partition manager in the install was great for me to resize my ntfs parition and create linux native n swap. The boot loader just took take care of the dual boot on its own. SWEET !

to someone who last installed linux when redhat came out with 5.something, this was just great.

It got all my hardware working just fine, even the wireless without having any ndiswrapper haddles n stuff.

I have two issues as of now

1) hibernation : It doesn't hibernate very well, gets stuck and then I need to power off.

2) I need to do away with my ntfs partition, either merge it with the linux native ( if possible without loss of data) or just copy the data from it to the linux native and resize it to 0.


any help on the above two will be highly appreciated.


thanks


Nivesh

---

### Post by the_nomad on 2007-12-30
1) how much space have you allocated for the swap?

2) if you have another partition with enough free space to hold data from partition A (that ntfs you want to merge with ubuntu native partition) then move the data from partion A to that free space, and then delete partition A (with gparted ... but i think it works with ubuntu installer too) and resize the ubuntu partition


hope it helps somehow!

---

### Post by PmDematagoda on 2007-12-30
Concerning your second question, a rather good program you can use achieve it is Gparted, it can be installed using:-
```

sudo apt-get install gparted
```
Gparted can then be found in System>Administration>Partition Editor.

About your first question, I cannot be very certain, but if you are using Ubuntu Gutsy then the problem can be the kernel since kernel 2.6.22 is rather buggy when compared to 2.6.20 and 2.6.23.

---

