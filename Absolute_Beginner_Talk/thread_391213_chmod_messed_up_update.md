---
title: "chmod messed up update"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by bennettmeredith on 2007-03-22
Because I couldn't do something a week ago, I used chmod in the terminal to reset the permissions of all the files in the directory /etc to 0777. Now update fails, and when I try update in the terminal I get the message:

 /etc/sudoers is mode 0777, should be 0440. 

Unfortunately, when I try:

sudo chmod 0440 sudoers

I get the same error message. How can I fix the permissions on sudoers so I can use sudo again?

---

### Post by Muzik83 on 2007-03-23
EEyikes!  777 is a very bad idea!  If someone obtains your /etc/shadow, they can calculate your password for all accounts on your system (and there are other various attacks using files in /etc/)

Now, after that rant, how to fix your problem

Boot into the 'recovery mode', which means you dont need to sudo anything. Then type the following commands
cd /etc/
chmod 0440 sudoers
chown root:root sudoers
chmod 640 shadow
chmod o-w *

Reboot back into your normal environment, and your sudoers problem should be fixed.  the "chmod o-w *" above will remove the global write permission from /etc (generally a bad idea... then anyone who can access the system is able to add users to /etc/passwd.

-sean

---

### Post by bennettmeredith on 2007-03-23
Sean:

Great answer. Thank you. It solved the problem.

I guess I'll have to find another way to permit moving and copying files.

---

### Post by taurus on 2007-03-23
What files do you want to move and where do you want to move it.  You can always use either "sudo cp "or 

```
gksudo nautilus
```

---

