---
title: "how do I run a comand as root?"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-11-08
I am installing Cinelerra and I have to run a command to finalize it but the HOW TO says "You will need to be root to issue the command. Sudo will not work."


So if sudo is not running as root, how do I do it? :-?

---

### Post by pay on 2006-11-08
try "sudo su"

---

### Post by argie on 2006-11-08
"sudo su"

should put you at a root prompt.

EDIT: UGH! Shouldn't open all the links in tabs to answer later. :D

---

### Post by Russty of Oz on 2006-11-08
Thanks guys!:)

---

### Post by Russty of Oz on 2006-11-08
Hmmm, that didn't work.  I have to run this command as root 

 **echo "0x7fffffff" >/proc/sys/kernel/shmmax**

I put the sudo su in front of it but it said Permission Denied

So, how do I do it? :-?

---

### Post by Russty of Oz on 2006-11-08
Its OK, I read argie's post again and realized I just had to put sudo su first then enter.

---

