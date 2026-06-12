---
title: "trouble with permissions [Resolved]"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by niallcd on 2007-04-10
Hello. 

Long time listener first time caller.

I have two hard disks I'm trying to add to Edgy. A 34 gig and a 250 gig when I try to add them in the console with $ chmod 777 /media/robot

I get this in response. 

chmod: changing permissions of `/media/robot': Operation not permitted

I have no idea why other then it might be a permissions problem.

If anyone can lend a hand it would be great. Thanks.

P.S. is there a way I can auto mount the two hard drives?

And If I need to repair my permissions how do I navigate to a place where I can repair them?

---

### Post by lamalex on 2007-04-10
you need to do sudo chmod

---

### Post by aysiu on 2007-04-10
If the second hard drive is NTFS or FAT32, you can't *chown* or *chmod* it.

One of these links should help you:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by niallcd on 2007-04-10
LAMALEX : What does {you need to do sudo chmod} mean? Could you elaborate? 

Just to be clear I'm a new user. I am totally new to the Linux community and its commands.

Thanks again.

---

### Post by niallcd on 2007-04-10
Hey I just recently reformated the two drive to EXT 3.

---

### Post by lamalex on 2007-04-10
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) is a good document for understanding sudo.

the way linux works, and part of the reason its so secure is how it handles administrator rights in the form of a root account. sudo allows you to run commands as the root user for that command without having a full time root user (pros and cons to this, that page has them). Things like changing permissions shouldn't be done by all users, so people callled "sudoers" (there is a permissions group by this name) are able to do things with the sudo command that administrators can do. :) hope that clears some things up

---

### Post by aysiu on 2007-04-10
> **niallcd said:**
> Hey I just recently reformated the two drive to EXT 3.
In that case, you want this tutorial:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by niallcd on 2007-04-11
okay so now all I am trying to due is install the drives I have followed the guides you guys suggested and this is how far I got 

niall@kronos:~$ sudo mkdir /media/robot
mkdir: cannot create directory `/media/robot': File exists
niall@kronos:~$ chmod 777 /media/robot
chmod: changing permissions of `/media/robot': Operation not permitted
niall@kronos:~$ 

any clues as to how I might be able to get permission?

---

### Post by aysiu on 2007-04-11
Paste these commands in the terminal: ```
sudo chown -R niall:niall /media/robot
sudo chmod -R 755 /media/robot
```

---

### Post by niallcd on 2007-04-12
Hi guys I resolved the issue with your help. Thanks alot!

---

