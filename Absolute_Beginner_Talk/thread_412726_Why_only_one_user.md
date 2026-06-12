---
title: "Why only one user?"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Bob Pendleton on 2007-04-18
Just installed 6.06 LTS.  The installer asked very few questions and gave very little info.  In particular, I have my own user name, and my own password, but I was not asked to set any other passwords which I might need for sys ad tasks.  Since this is a brand new OS on a brand new machine, there are lots of sys ad tasks I need to do -- getting the OS to recognize the ethernet port on my motherboard, the PATA IDE port on my motherboard, setting up my video board, my RAID board, etc.  How do I do sys ad if all this OS wants to let me do is use Gnome as username bob?

The documentation I have seen seems more focused on using the OS as a user rather than doing sys ad tasks.  Is there a document I'm missing? Are there manuals on the distro DVDs?

Thanks, all:) 

Bob Pendleton

---

### Post by earobinson on 2007-04-18
you can use the sudo command to do sys admin tasks

---

### Post by charming_eyes on 2007-04-18
As I understand, Ubuntu policy (like most of the Linux Distros) is not to use root everytime. When you will try to perform any system administration tasks in gnome, you will be asked for your password and it will be enough for you. Also, if you want to do something as root in terminal, just type: sudo <command> (e.g. sudo su) and enter your password after this. I hope that I've answered your question.

---

### Post by Cypher on 2007-04-18
The first user created during installation is also the Sys Admin account. You're automatically added to the "sudoers" file and can perform all your sys admin tasks with sudo.

You can also create other users later on and, I believe, those new users will be regular users without sudo privs.

Regards

---

### Post by Patrick K on 2007-04-18
Just use the password you entered when installing.

---

### Post by kingy89 on 2007-04-18
Hi

One of the key reasons Windows 98/XP had security issues, is that programs running on an admin login can get admin access to systems as if they were the user. 

The way that admin accounts work in Ubuntu means this cannot happen. Everybody is a low level user, until they NEED to perform admin tasks. Only then will they be asked for the root password.

I know Charmind_Eyes said the same thing really, but I wanted you to understand some of the reasoning behind it.

Adam

---

### Post by brennydoogles on 2007-04-18
> **Bob Pendleton said:**
> Just installed 6.06 LTS.  The installer asked very few questions and gave very little info.  In particular, I have my own user name, and my own password, but I was not asked to set any other passwords which I might need for sys ad tasks.  Since this is a brand new OS on a brand new machine, there are lots of sys ad tasks I need to do -- getting the OS to recognize the ethernet port on my motherboard, the PATA IDE port on my motherboard, setting up my video board, my RAID board, etc.  How do I do sys ad if all this OS wants to let me do is use Gnome as username bob?

The documentation I have seen seems more focused on using the OS as a user rather than doing sys ad tasks.  Is there a document I'm missing? Are there manuals on the distro DVDs?

Thanks, all:) 

Bob Pendleton

If I understand your question correctly, you are wondering if you need to set a new password for system administration tasks... am I correct? If so, the answer is no. Anytime you do any type of Stsem administration, you will be asked for a password. The password you need to type is your user password, which you created when you installed ubuntu. This password prompt keeps unwanted software from being installed on your system (nothing can install unless you directly give it permission). If you are on a multi-user system (such as a family computer), you can give differing levels of administrative privileges to each user, or none (for children or people who don't look before they install :O) ). If you have multiple users with Administrative privileges, each will use their OWN password... that way there is no root password to have to keep up with. Did I answer your question?? If not, feel free to post back!!

---

### Post by Bob Pendleton on 2007-04-18
Thanks all,   I'll use sudo

Bob Pendleton:)

---

### Post by earobinson on 2007-04-18
> **charming_eyes said:**
> As I understand, Ubuntu policy (like most of the Linux Distros) is not to use root everytime. When you will try to perform any system administration tasks in gnome, you will be asked for your password and it will be enough for you. Also, if you want to do something as root in terminal, just type: sudo <command> (e.g. sudo su) and enter your password after this. I hope that I've answered your question.
you can use sudo -s instead of sudo su

---

### Post by edgecoug71 on 2007-04-18
I am using the beta for feisty fawn and I am new to Ubuntu, but I found some links to some sites you can check out if you haven't already....

[https://help.ubuntu.com/6.06/](https://help.ubuntu.com/6.06/)
[https://blueprints.launchpad.net/dapper-backports/+documentation](https://blueprints.launchpad.net/dapper-backports/+documentation)
[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

You can also look at some of the Ubuntu books out in bookstores too, I have one, hacking Ubuntu and it is based on 6.06.....Hope you find what you are looking for....

---

