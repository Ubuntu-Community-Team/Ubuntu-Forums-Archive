---
title: "Cannot login with a newly created ubuntu user"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by mihaic on 2005-11-19
Hi guys,

  I have done a little searching but haven't found anything related to the problems I'm encounering when I try to login in my ubuntu system with a freshly created user (not root, and not the default user that you are asked to create at installation).
  I have created a few users for my friends, but none of them work. When trying to login using one of them I get an "Incorrect username or password. Letters must be in the correct case." error. 
  Now I am absolutely sure that I typed in the correct username and password, but still I get this error. 
  Also in my auth.log I get the following line for the respective user:
  "authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=ana"
  Can any of you guys give me some advice on what to do here? I know I must have overlooked something when creating the user or there are some config files that need modifications, but I don't know where to look.

Thanks a lot,
Mihai

---

### Post by JurB on 2005-11-19
[QUOTE=mihaic]Hi guys,
 Now I am absolutely sure that I typed in the correct username and password, but still I get this error. 
 [/QUOTE]

Are you sure you haven't included numbers and the numlock is off?
Or was the numlock off while you created the user/password?
Caps-lock?

This seems dumb, but this tends to get overlooked quite easily ;)

---

### Post by patrick295767 on 2005-11-19
password probl certainly ... no ?
so:
maybe : 
sudo passwd user_beta
   
or:
(if no root)
[http://www.ubuntuforums.org/showthread.php?t=64557&page=6](http://www.ubuntuforums.org/showthread.php?t=64557&page=6)
  
greetz

---

### Post by mihaic on 2005-11-19
I finally managed to get the users to work.
I have logged in as root in recovery mode and changed their passwords. That seemed to do the trick.

Thanks for the sugestions guys.
Mihai

---

### Post by wulfhound on 2007-03-10
> **JurB said:**
> Are you sure you haven't included numbers and the numlock is off?
Or was the numlock off while you created the user/password?
Caps-lock?

This seems dumb, but this tends to get overlooked quite easily ;)

I am getting the same exact thing with Xubuntu Edgy.....

Sigh.

Sandaili

---

