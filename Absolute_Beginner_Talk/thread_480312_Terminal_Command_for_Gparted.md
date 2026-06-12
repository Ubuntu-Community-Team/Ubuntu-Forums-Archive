---
title: "Terminal Command for Gparted"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by JerryAtrik on 2007-06-21
I have installed Gparted on my dapper Ubuntu but it will not run without my instructions .have looked through the archives ,but non of the commands I have tried work .Can some kind person give me the terminal command to make it work for me .
The reason :
I have a spare partition on which to install Feisty Fawn .I already have windows and Dapper installed .However the installation CD reads the Drive as completely blank .
Windows Administration can read all the partitions .Ubuntu Dapper System -Admin-Disk manager can read all the partitions .But non of my Ubuntu CD`s can read it .I have also tried The "Rescue Live cD test disk but got nowhere with that .Dapper CD did read it all properly at one stage but not now.
Can anyone advise please?
Cheers Jerry

---

### Post by dreadlord_chris on 2007-06-21
> **JerryAtrik said:**
> I have installed Gparted on my dapper Ubuntu but it will not run without my instructions .have looked through the archives ,but non of the commands I have tried work .Can some kind person give me the terminal command to make it work for me .
The reason :
I have a spare partition on which to install Feisty Fawn .I already have windows and Dapper installed .However the installation CD reads the Drive as completely blank .
Windows Administration can read all the partitions .Ubuntu Dapper System -Admin-Disk manager can read all the partitions .But non of my Ubuntu CD`s can read it .I have also tried The "Rescue Live cD test disk but got nowhere with that .Dapper CD did read it all properly at one stage but not now.
Can anyone advise please?
Cheers Jerry

not sure what you mean that it won't start without your instruction, but....
```

gksudo gparted

```
should open a window asing for your password - then open gparted

---

### Post by JerryAtrik on 2007-06-21
dread_lord chris .Already tried that before but cut and pasted again and I get command not found        myffie@myffie-desktop:~$ gksudo gparted
                sudo: gparted: command not found

any other ideas please ?

---

### Post by aeiah on 2007-06-21
are you sure its installed?

```
sudo apt-get install gparted
```

the command given by dreadlord should launch gparted.

ive found that with troublesome drives and partition editing in general, using the gparted livecd is better, since its a newer version and you dont have to mess with mounting and unmounting partitions or drives. its a small livecd and loads pretty quick. you could try that

---

### Post by JerryAtrik on 2007-06-21
I definitely have Gparted installed from Applications - System tools I click on it and it comes up qparted v0.4.5-cvs with no drives selected but all greyed out so cannot insert any info. 
have downloaded and burnt Gparted CD but cannot find the command to open it.

---

### Post by JerryAtrik on 2007-06-21
Oh dear ! what a Pratt I had installed Qparted NOT parted sorry gents 
Now downloaded and working .
Thank you for sowing the seeds of doubt about it being installed
A rather red faced Jerry

---

