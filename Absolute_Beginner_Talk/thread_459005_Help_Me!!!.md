---
title: "Help Me!!!"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by frd on 2007-05-30
I need ubuntu and i boot my ubuntu in recovery mode and i wouldn´t! After i write in recovery mode "reboot"! Now i can't login in ubuntu! I write username and pass...but ubuntu display every time username and pass!!

Example:

(grub)
1- ubuntu
2- ubuntu (recovery mode)
3- other OS...

and I select (1)

...and then I write:

username: *****
password: *****

...after:

ubuntu ask me yet

username: *****
password: *****

and never end this!!!!

---

### Post by hashimoto on 2007-05-30
So it seems that your password (or username) is wrong. 

To set the password, reboot to recovery mode and do:
```
passwd username
``` (replace username with your real username, of course). You are then prompted for a new password for that user. Then reboot and log in.

---

### Post by bapoumba on 2007-05-30
@ frd: moved your thread to "Absolute Beginner Talk".
Do you mean you cannot boot in recovery mode _at all_ ?

---

### Post by frd on 2007-05-30
don't work!!! :-(

password and username are correct!
ubuntu not said pass or username incorrect, he accept pass and username, but display everytime this:

username: ****
...then...
password: ****

accept and...

username: ****
...then...
password: ****

accept and...    
    
    "
    "
    "

---

### Post by Cypher on 2007-05-30
The fact that you're getting the Username prompt again after entering your password means that it's not right. Instead of choosing option [1] from the GRUB menu, choose option [2] and do the "passwd <username>" that was suggested earlier..

---

### Post by bapoumba on 2007-05-30
Then you'll have to use a Live CD to fix that. I cannot guide you through from the top of my head, I'll have to dig around.
Anyone else, please ?

---

### Post by bapoumba on 2007-05-30
Okay,here is a procedure from the Live CD:
[http://ubuntuforums.org/showpost.php?p=2683122&postcount=8]("http://ubuntuforums.org/showpost.php?p=2683122&postcount=8")

---

### Post by frd on 2007-05-30
I already make this!!!

recovery mode:

passwd <username>
...and new pass!!

doesn't work!!

...and if I insert a wrong username or pass in option (1) ubuntu tell me that is incorrect...but this not happen when I insert correct data!!

---

