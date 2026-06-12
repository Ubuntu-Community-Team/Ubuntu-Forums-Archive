---
title: "upgrading to 6.10 from DVD"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by dhawald3 on 2006-12-11
I have kubuntu 6.06 on my pc

and I have the kubuntu 6.10 DVD

so how do I upgrade to 6.10 using the DVD

---

### Post by ziggykg on 2006-12-11
I upgraded using the 6.10 DVD by using the 'cdromupgrade' script on the DVD.

[https://help.ubuntu.com/community/EdgyUpgrades]("https://help.ubuntu.com/community/EdgyUpgrades") states you can do so thus (command amended to reflect location of script on the DVD):

```
gksu "sh /cdromupgrade"
```

Boot the live DVD, open a terminal window and run the above command.

---

### Post by dhawald3 on 2006-12-11
> **ziggykg said:**
> I upgraded using the 6.10 DVD by using the 'cdromupgrade' script on the DVD.

[https://help.ubuntu.com/community/EdgyUpgrades]("https://help.ubuntu.com/community/EdgyUpgrades") states you can do so thus (command amended to reflect location of script on the DVD):

```
gksu "sh /cdromupgrade"
```

Boot the live DVD, open a terminal window and run the above command.


ok but what is the command for kde

---

### Post by bluefrog on 2006-12-11
command line is the same on kde
might want to use sudo instead of gksu though

james

---

### Post by dhawald3 on 2006-12-11
> **bluefrog said:**
> command line is the same on kde
might want to use sudo instead of gksu though

james

right now I am in the live DVD
it didn't work I tried

ubuntu@ubuntu:~$ kdesu "sh /cdromupgrade"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
sh:
Can't open /cdromupgrade

---

