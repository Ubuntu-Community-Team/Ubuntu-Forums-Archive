---
title: "Bad at researching/searching need sudo help"
date: 2009-08-02
forum: Beginner Team
---

### Post by silvervein on 2009-08-02
Greetings,
 
I generally have a terrible time of researching info in forums. With that I have 2 questions I'm hoping to get answered here.
 
1. Tips and tricks of using forums to find what you need. (I wish only to create new threads if I have to, not duplicate someone elses threads.)
 
 
2. I just installed Ubuntu-9.04-server-powerpc on a Mac Mini. Server packages installed: Print and file server packages.
 
Install went just fine. I reboot and log in no problems to the command line environment. (as much as I would like to learn more about command line, I need to work on a desktop environment for help).
 
so I typed:
 
sudo apt-get install ubuntu-desktop
 
[sudo] password for (user):
 
Now I type in my pwd for (user) and get the following error:
 
(user) is not in the sudoers file. This incident will be reported.
 
Well I've only made 1 user and that was in the install. What do I do now? What file do I need to edit, should I re-install? 
 
Thank you all for any assisntace.
 
-Impatient n00b

---

### Post by jerrrys on 2009-08-02
heres one idea

[http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

---

### Post by silvervein on 2009-08-03
Interesting, thank you.

---

### Post by Logan1985 on 2009-11-24
In Ubuntu desktop, the first User is added to the Admin group by default and so can use Sudo. I am not familiar with Ubuntu server, so perhaps it is a little different. 

Were you prompted to set a password for root/administrator when you installed?

If not, reboot the server and select "recovery mode" from the grub menu. This lets you have root access without authentication

Then when you have a shell prompt, take a look at the sudoers file with "visudo"

For your reference, heres an example from a desktop version of ubuntu - note the last line - members of the Admin group can sudo:

 # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

