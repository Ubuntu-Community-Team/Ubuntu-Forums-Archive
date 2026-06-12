---
title: "Why can't I save to &quot;Read Only&quot; files?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by chaofan on 2007-01-31
I know the title kinda sounds funny, but what I mean is that I can't change attributes.

Some of my configuration files (text files mainly) have read only attributes, and although I am the system owner/admin/whatever you wanna call me(super user) I can't change permissions on the file so I can save to it. Is there any way of changing this without a gigantic amount of terminal command stuff? (like disable the whole required to be admin to do ANYTHING crap?) or even making it so that I never have to use sudo stuff again?

---

### Post by taurus on 2007-01-31
What files do you want to change permissions.  Again, don't change permissions because they would make life easier for you.  The reason they have that type of permissions is for a good reason.  Have you read through this guide at all?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bodhi.zazen on 2007-01-31
Yes, there are ways of doing this, but I do not advise such a drastic action.

IMO the best way to configure these files is with sudo.

sudo vim <file>

OR

sudo nano <file>

OR

gksudo gedit <file>

It takes some adjustment, but it is your interest.

---

### Post by ewankho on 2007-01-31
Technically you are not logged in as admin/root if you are using Ubuntu correctly. This is to protect the user from damaging the system should they make mistakes.

---

### Post by Stochastic on 2007-01-31
Basically, it is a major security risk to operate regularly as root in X.  The use of the sudo command (sudo gedit, etc..) is highly recommended whenever you need to edit underlying configurations.  Should anyone somehow attack your system and gain access to your user account this prevents them from doing any terrible damage.

That being said, you can run 'sudo passwd' to change the root password (THIS IS ALSO NOT GOOD FOR SECURITY!!! the generated root password is very secure and should not be changed, sudo works fine for editing files).  Then you can use the su command to change the user to root but DO NOT CHANGE PERMISSIONS OF THE CONFIG FILES.  Those permissions keep your system secure.

---

### Post by the_darkside_986 on 2007-01-31
I do not understand how making a diff. password for root is dangerous. It seems that after doing a sudo, programs that need root privelege only prompt me for password half the time. This seems to be insecure but I am new to Ubuntu. I hope no one gets my one and only password.

---

### Post by aysiu on 2007-01-31
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

and this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by chaofan on 2007-02-02
Well I'm sure you guys are thinking some of the security risks are hackers, but I'm behind a router and a pseudo-router (quest DSL modem has most features of a router), as well as firewall protection. I am not new to computers, so I know how to stay safe, it's just I don't quite understand which commands get me to where I wanna go. I'm normally a windows guy, and there isn't much of this "Enter your password so you can move your mouse" mentality. Thanks for your concerns and help though, I really appreciate it.

---

### Post by aysiu on 2007-02-02
Read the links I posted. Thanks.

---

### Post by macogw on 2007-02-02
> **the_darkside_986 said:**
> I do not understand how making a diff. password for root is dangerous. It seems that after doing a sudo, programs that need root privelege only prompt me for password half the time. This seems to be insecure but I am new to Ubuntu. I hope no one gets my one and only password.

That thing with sometimes prompt sometimes not is probably because it acts like a cookie and expires after like 15 minutes

---

### Post by aysiu on 2007-02-02
You can change the timeout to be 0 minutes instead of 15 minutes if you want.

---

### Post by Archmage on 2007-02-02
> **chaofan said:**
> I'm normally a windows guy, and there isn't much of this "Enter your password so you can move your mouse" mentality.

I think you didn't tried Vista yet. :lolflag: 

The UAC from Vista is more a burden than they way Ubuntu is doing it. Vista will ask the user ANYTIME it is doing something that might have to do with a task for an administrator. Ubuntu on the other hand will only ask you once a while.

This is ment to help you to have a working system, because you can screw up very easy things as a beginner to Linux.

I hope the *sudo-way is working for you. I think there is also a way that you can edit such files with a right-click on "edit as root".

---

### Post by bodhi.zazen on 2007-02-02
> **chaofan said:**
> Well I'm sure you guys are thinking some of the security risks are hackers, but I'm behind a router and a pseudo-router (quest DSL modem has most features of a router), as well as firewall protection. I am not new to computers, so I know how to stay safe, it's just I don't quite understand which commands get me to where I wanna go. I'm normally a windows guy, and there isn't much of this "Enter your password so you can move your mouse" mentality. Thanks for your concerns and help though, I really appreciate it.

LOL, I understand the feeling. But this is part of what makes Linux more secure and the restrictions are not that harsh.

I do not run windows, but my understanding is windows is in fact going this way as well.

See Archmage's post and my understanding is windows server editions are similar to Linux.

Linux is a whole new OS and very different from windows. Not much of what you may know about windows will apply to linux, although obviously some will. Give it time and it will start to make sense.

Again, this is one reason it is more difficult to compromise a Linux box with viruses and maleware.

---

### Post by xpod on 2007-02-02
> Well I'm sure you guys are thinking some of the security risks are hackers, but I'm behind a router and a pseudo-router (quest DSL modem has most features of a router), as well as firewall protection. I am not new to computers, so I know how to stay safe, it's just I don't quite understand which commands get me to where I wanna go. I'm normally a windows guy, and there isn't much of this "Enter your password so you can move your mouse" mentality. Thanks for your concerns and help though, I really appreciate it.

Also to protect us from ourselves i believe:D

---

