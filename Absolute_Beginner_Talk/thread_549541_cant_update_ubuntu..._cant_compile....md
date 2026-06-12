---
title: "cant update ubuntu... cant compile..."
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by Lewismorris on 2007-09-12
hi,i recently installed ubuntu and have had some problems :) if anyone could help would be great!!

right i tryed updating but i need the password... but i sware it didnt ask me for one ! i tryed every password i use and nothing ... any ideas?

and also when i try to 'make' and it dosent work when i try to compile stuff... i could be doing it rong tho lol :P im new 

oh and one more thing ... why dosent the spell ceck know how to spell ubuntu?

---

### Post by swoll1980 on 2007-09-12
to compile you have to install build-essential from synapics but you need to know you password to do that Try going to users under the system menu, create a new password under old password leave it blank if you didn't create one you shouldn't need one

---

### Post by Lewismorris on 2007-09-12
ok i still cant update i think i got mypassword right but it says [[img=http://img513.imageshack.us/img513/4121/screenshottu1.th.png]](http://img513.imageshack.us/my.php?image=screenshottu1.png)

---

### Post by splintercellguy on 2007-09-12
You do anything to /etc/sudoers? The password it's looking for is the one you set when you installed Ubuntu. If you have forgotten your password, you can reset it by doing:

passwd <your username>

in the Recovery Console.

---

### Post by Lewismorris on 2007-09-12
ive done nothing to no folders.... any help? lol i know the pass

---

### Post by Hospadar on 2007-09-12
Do you use a password to login when your machine starts up?  If you do, then I suspect the problem is one of two things: Somehow the "admin" group got removed from /etc/sudoers somehow, or, you somehow got removed from the admin group.  If you at some point changed your root password and you know what it is, you could go to a terminal and type "su" give your root password and use the "visudo" command to check the /etc/sudoers file, make sure admin is on the list. (if you go this route read up on manually editing this file, it's not exactly straigtforeward) or try using the recovery console to re-add your user to the admin group.

---

