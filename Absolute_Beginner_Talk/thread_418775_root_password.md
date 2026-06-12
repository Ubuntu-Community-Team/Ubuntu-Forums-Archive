---
title: "root password"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by mayday56 on 2007-04-22
Ive just installed ubuntu fiesty fawn.I opened a terminal ,did an su.put in the only password that was given during the install and it wont work,just says sorry....help

---

### Post by bobplano on 2007-04-22
use sudo su. just be careful as root, you can really mess up your system

---

### Post by mayday56 on 2007-04-22
thanx worked great...I guess alot has changed since my old solaris 2.6(unix) days....

---

### Post by RobsterUK on 2007-04-22
Its worth noting that in Ubuntu pretty much everything you might need to do as root can be done using

```
sudo command-name
```

This is a security feature of the distro which means you don't need to do su or login as root

EDIT: see [this page]("https://help.ubuntu.com/community/RootSudo") for more info

---

### Post by abcuser on 2007-04-22
Hi,
this sudo command instead of su command was the thing I was very surprised in Ubuntu. So at first I used "passwd root" command to assign password to root user. First thing, using sudo instead of su by default, I imagined was "Ubuntu stupidity" but when reading more info on this topic, I realized it is the main key to be secure system by default! For example Microsoft recommendation is use "User" privilege to access internet with web browser. But almost all users access internet with "Administrator" privilege. That is one single most important security problem on Windows, because all viruses and worms uses this admin weakness and changes/damages system settings. For example the latest worm in Windows [Win32/Stration](http://www.eset.eu/buxus/generate_page.php?page_id=15099) uses the admin privilege security weakness. Worm copies itself into system folders and changing system registry - the task only admin user can perform. So if users would not use superuser privileges to access internet this change couldn't happen.

So now days I am convinced Ubuntu security concept is way more secure then Windows one. There is one single problem on Windows: How to convince users to lower privileges from admin to user? According to my experience most of the people are strongly convinced that lowering privileges will make to many pain, but there are wrong. The pain begins if all privileges are allowed to web browser.

I have been working on Microsoft operating systems more then 15 years and at the bottom end there are the following security recommendations (Microsoft suggestions!) sorted from most important to less important:
1. lower your default user from Administration privileges to User privileges (Ubuntu does this by default and refuse log in into system by root user - only sudo is recommended)
2. stop using Internet Explorer 6 - use Internet Explorer 7, Firefox 2 or Opera 9 or any other browser (Ubuntu has this by default it uses Firefox 2.0 - IE6 is only available in Ubuntu with WINE)
3. upgrade your operating system regularly (Ubuntu does this by default - it suggest you to download new packages when available)
4. install firewall (this is the only recommended task on Ubuntu too - but not because of viruses or worms but because internet is not secure)
5. install anti-virus program (not needed on Ubuntu - it can be applied by not required)
6. install anti-spyware and anti-adware programs (not need on Ubuntu)

Bottom line. If there is some comparison between Windows and Linux (Ubuntu) which is better system. I can say: "If you look into security model, Ubuntu has better model not question about."

Hope this helps,
Abcuser

---

