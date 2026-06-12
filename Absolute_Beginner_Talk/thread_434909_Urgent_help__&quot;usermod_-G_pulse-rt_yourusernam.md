---
title: "Urgent help : &quot;usermod -G pulse-rt yourusername&quot; messed ujp my system"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by medya on 2007-05-06
hey I have an important meeting in 3 hours , and I have to make my computer work 

I had a problem with [Rhythmbox Curshing ]("http://ubuntuforums.org/showthread.php?t=434490")and a forum user suggested  **usermod -G pulse-rt usernamed**

and I did this 
> shewdiz@shewdiz-pc:~$ usermod -G pulse-rt shewdiz
usermod: unable to lock password file
shewdiz@shewdiz-pc:~$ sudo usermod -G pulse-rt shewdiz
Password:
shewdiz@shewdiz-pc:~$ 

after that I lost everything , I dont see the admin tools, I cant run the synaptic package manager (it says the root doeasnt have the righ, and I dont have sound )

that command killed my ubuntu ! how I can undo whatever the above comamnds did to my ubuntu ?

---

### Post by medya on 2007-05-06
bump !

---

### Post by junjan on 2007-05-06
Usermod manual:

> 
-G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
          A list of supplementary groups which the user is also a member of.
          Each group is separated from the next by a comma, with no
          intervening whitespace. The groups are subject to the same
          restrictions as the group given with the -g option. [B]If the user is
          currently a member of a group which is not listed, the user will be
          removed from the group.[/B] This behaviour can be changed via -a option,
          which appends user to the current supplementary group list.


Maybe you have removed yourself from any group that is not pulse-rt...

Type "groups" in the command line to know what groups are you member of.

---

### Post by junjan on 2007-05-06
For example. I am in the following groups:
```

junjan@Junjan:~$ groups
junjan adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin fuse
junjan@Junjan:~$ 

```

junjan is my login.

---

### Post by medya on 2007-05-06
i think you are right, here is what it says for me :
> shewdiz@shewdiz-pc:~$ groups
shewdiz pulse-rt


---

### Post by medya on 2007-05-06
so what to do ? how to fix ?

---

### Post by Skrynesaver on 2007-05-06
If you have a liveCD you can boot in this and mount your / partition. edit the file /media/<partiotion of / >/etc/group
add your username to the groups 
"adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin"

---

### Post by medya on 2007-05-06
thanks that worked ! thanks

---

### Post by junjan on 2007-05-06
Another collaborative community success!! :mrgreen:

---

### Post by Skrynesaver on 2007-05-06
Ola Junjan, you name the tune, I'll play the notes ;)
Collaborate again sometime soon

---

### Post by minuxx on 2008-07-03
> **Skrynesaver said:**
> If you have a liveCD you can boot in this and mount your / partition. edit the file /media/<partiotion of / >/etc/group
add your username to the groups 
"adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin"

I got the terminal of my livecd in front of me.
Whats the exact command to mount my / partition.
I need urgent help! Please!

---

