---
title: "sudo gives an error..."
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by notquitehere188 on 2005-12-31
i was trying to change permissions for multiple files and i went to this post
[http://www.ubuntuforums.org/showthread.php?t=109201&highlight=set+multiple+permissions+terminal](http://www.ubuntuforums.org/showthread.php?t=109201&highlight=set+multiple+permissions+terminal)
and did the chmod thing, however i moved to the folder i wanted but put /*/* and according to a thing which i am just reading now that goes to root, now whenever i try to sudo it says something about sudoer, needing to be 0440 anb being 0777. 
and then i tried to fix it but now terminal wont open saying failed to change to directory '/ home/user permission denied

i think i did a bad thing

---

### Post by towsonu2003 on 2006-01-05
I think you should do a fresh install... you changed the permissions of too many files to deal with...

---

### Post by newuser111 on 2006-01-07
or you could log in as the root account if sudo doesnt work

set password by sudo passwd root

and do  sudo chown -R username:username /home/username

and set root permission with same method to the rest of the installation except your home directory, but im not sure if i missed any other areas that should be set to as your user permission

---

