---
title: "Sudu Help and permissions help!  ( newb)"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Natedawg3086 on 2007-07-22
This all started out trying to do a simple task for a game.. and ended up ruining every thing..  

I'll start off where I began.   

I was trying to change the permissions to a setup.txt file under my /etc/somegame directory and it would not let me do it, So searching on the forums I find out about the sudo nautilus command in the terminal and I proceed to do as told.  I Think I know where I messed up now, but trying to revert what I did is a pain in the neck.  I changed the permissions in the /ect so that my user name is the owner and I did some other tweaks under permissions.  Now when I try to revert it back using sudu I get a error 

> "sudo: /etc/sudoers is mode 0460, should be 0440". 

I also checked In other threads similar before posting and every thing I have done just doesn't work, Or I'm not doing it right. I also tried changing the mode back by typing 

> sudo chmod 0440 /ect/sudoers  

and still the same error. I Kinda know what the mode means which is the permissions but I'm just having sever trouble doing so... All I want to do is revert it back to normal.  

1) I tried also to use the live cd to change any thing back but no luck, or I didn't know what to do.
2) I also tried to reboot press esc and add init=/bin/bash in the kernal part after what was already there and it did not boot up ( so it seems it wont let me log in as root)...  I don't know if i did it right or not *shrugs*.



Under permissions for the /etc folder I can change every thing still but nothing works and it just goes back to how it was, oh and every folder and file in the /etc folder has a lock on it now which didn't before. Oh another thing is that I pressed under permissions when I first did it ("apply permissions to enclosed files")..

So all I want to do is just revert it back so I can use sudo and im good.. but thats the whole problem...   I can't even access sudo and I don't know how to fix any thing..  I'm sorry for being a complete newbzorz.. but Help is needed!  Thx again for whoever posts! :(

edit: I Also just tried to reboot into recovery mode and do a 

> " chmod 440 /etc/sudoers"

but that ended up saying 

> "chmod: changing permissions of `/etc/sudoers': Operation not permitted"

So im guessing all I need to do now is just some how get it so i can have permissions to edit it then do the chmod command but thats where im having trouble as well..

---

### Post by Natedawg3086 on 2007-07-22
bump of some sort?

---

### Post by aysiu on 2007-07-22
Boot into recovery mode and type ```
chown -R root:root /etc
chmod 0440 /etc/sudoers
reboot
``` **Then stop changing ownership of system files**. That's a quick way, as you now know, to break your system.

If you need to edit system files, do it the right way:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

