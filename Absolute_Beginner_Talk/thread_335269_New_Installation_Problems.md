---
title: "New Installation Problems"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by subject117 on 2007-01-10
I installed Ubuntu today using the Alternative installation CD because I wanted to have a raid 1 disk configuration.  I got it to work and finished the installation without any problems until I tried to update the software.  I am unable to do anything to administrate this machine!  

In the menu when I select System - Administration - Update Manager, I get a list of software updates.  I tell it to install and it prompts me for my password.  Then I get an error message that this failed.  It says "The underlying authorization mechanism (sudo) does not allow you to run this program.  Contact the system administrator."  I can not use the "Users and Groups" function.  In a terminal, when try to use sudo, I get ignored:

jim@Dell:~$ sudo passwd
Password:
jim@Dell:~$ 
jim@Dell:~$ sudo adduser john
jim@Dell:~$ sudo sh
jim@Dell:~$ 

It seems that this user does not have any administation privleges on this machine.  This is the user I created in the installation process.  When I first logged in as oem and then restarted, I was prompted for a few things but it crashed on the last step.  Is that related to this problem?  And how do I fix it?  Do I have to reinstall everything again?  Or is there an easier way?  This is so frustrating.

---

### Post by ajm2005 on 2007-01-10
bump for responses :)

---

### Post by jvc26 on 2007-01-10
When it asks for your password, have you put your password in (i.e. the one you use for your account) and then pressed enter?
Ah 1 sec have re-read your post, it sounds like the last step of the install may well have something to do with this if it crashed before it completed, then you may have an incomplete install and hence the sudo command may well be nonfunctional - would it be a lot of trouble to try a reinstall?
Il

---

### Post by eeaarrgh on 2007-01-10
Same thing here, except I didn't experience any crash.  Hey, I even got my ATI X300 card working (which is why I went with the OEM install on the alternative CD).  Now I have this lovely system that I'm unable to administer.  D'ohh!

Just joined the forum (first post!) so I'm still looking for answers beyond reinstallation (which really was relatively painless, even the part where I learned a little about vim).;) 

e

---

### Post by nonpareilpearl on 2007-01-10
I had similar problems when I first installed Ubuntu until I realized you have to *create* the sudo user profile. I am unsure what, if any, default password there is but you must first create a password (probably a good idea to make it match your admin/user password).  Then when you attempt to execute sudo commands everything should work fine :)

---

### Post by subject117 on 2007-01-12
I got it to work for me!

What I did is I booted the machine in single user mode, giving me root access.  I did this by hitting the escape key on startup, then editing the boot script thing to add a ", single" to the end of the kernel line, then started it up.  I then had root access, so I changed the password to something I know, and edited the /etc/group file to add myself to the sudo group.  Then I restarted, and everything worked.

---

