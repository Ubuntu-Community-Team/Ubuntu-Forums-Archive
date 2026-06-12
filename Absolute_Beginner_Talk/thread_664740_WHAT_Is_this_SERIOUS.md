---
title: "WHAT? Is this SERIOUS?"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by gnappi on 2008-01-11
OK, let me start by saying that I've used Linux a long time in a development lab, not as a desktop user. I setup UBUNTU 7.10 on a dual boot system wit XP to see how Winblows users will fare. 

Initially I gotta say, this ubuntu is not bad. Sure customizing the desktop and finding applets takes a bit but in general it's pretty easy to use if you have just a  little experience with Linux. 

Other than occassionally hanging (Dell 210L) I noticed that had to change the root user password in advance because I did not find any notes on what the default password was which was NOT what I setup for the default user.

Anyway,  here's the problem.

I set the default users' home directory as /  and the system allowed me to do it. But rebooting I could NOT get in as my defaust user and the ROOT user isn't allowed in on the login screen.

What's the purpose does it serve to not allow the root user to log in  
after from the login screen at the default runlevel? If the user had a problem and cannot log in how do you fix it? 

Can this be easily fixed or do I simply re-install. 


   Gary

---

### Post by Pevichaey5 on 2008-01-11
if you don't really have anything, i would reinstall

but you can login as normal at the moment? if so you can use root priviledges to change the permissions on / for your user

---

### Post by gnappi on 2008-01-11
I cannot log in at all.


  Gary

---

### Post by kestrel1 on 2008-01-11
Do a re-install then.

---

### Post by p_quarles on 2008-01-11
You can still log into recovery mode (single user mode) from the GRUB boot menu.

The root account is locked by default in Ubuntu. You can, of course, easily set a password for it, but the normal way of doing things is to use "sudo" before commands that require root privileges. Your initially-created user has full sudoer privileges. This can also be changed or tweaked.

---

### Post by stroyan on 2008-01-11
You can reboot and select a "recovery mode" grub boot menu option to start the system in single user mode.  That will have you logged in as root.  The intention of the ubuntu configuration is to use sudo instead of ever logging in as root.  The rationale for that is discussed at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

