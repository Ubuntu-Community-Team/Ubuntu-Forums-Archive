---
title: "MySQL won't start don't know password"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by locoHost on 2006-09-13
I've tried entering every variation of "mysql -u root -p" and "mysql -u ????? -p" that I can think of. I've been trying to start MySQL for well over a 30 minutes with absolutely no success. You could say I'm a little frustrated. I had MySQL started before but I have no idea now what any password might be as I type this. How can I clear the password and start over with it blank.

Obviously I don't know what I'm doing.

I will -greatly- appreciate your help.

---

### Post by jordanmthomas on 2006-09-13
I believe there is no root password at the start...just blank

this site tells you how to reset it, as you asked
[http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html)

---

### Post by locoHost on 2006-09-13
This is what I get...

mark@d6games:/etc/mysql$ mysql
ERROR 1045 (28000): Access denied for user 'mark'@'localhost' (using password: NO)

or...

mark@d6games:/etc/mysql$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)


I have no clue what the password is. I've tried every variation my standard passwords and none work. I tried creating the text file with the reset password commands and doing all the steps in the instructions but I get various "Access denied" errors when anything tries to run. What's the next idea?

---

### Post by blunt1 on 2006-09-20
> **locoHost said:**
> This is what I get...

mark@d6games:/etc/mysql$ mysql
ERROR 1045 (28000): Access denied for user 'mark'@'localhost' (using password: NO)

or...

mark@d6games:/etc/mysql$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)


I have no clue what the password is. I've tried every variation my standard passwords and none work. I tried creating the text file with the reset password commands and doing all the steps in the instructions but I get various "Access denied" errors when anything tries to run. What's the next idea?

I have exactly the same problem! :confused: 
Can anyone help!?

Thanks

---

### Post by dbott67 on 2006-09-20
Similar thing happened to me.

I was following the guide for a "Perfect LTS Server Setup" here:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

And on page 4, step 10, I got to the MySQL password section (the last step on the page):

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4)

And it choked on the 2nd line:

```
mysqladmin -u root password yourrootsqlpassword

mysqladmin -h server1.example.com -u root password yourrootsqlpassword
```

-Dave

---

