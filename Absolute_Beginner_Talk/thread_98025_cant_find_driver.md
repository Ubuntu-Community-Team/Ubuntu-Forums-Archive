---
title: "cant find driver"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by xstation on 2005-12-02
I have a driver in the folder dffd but for some reason cannot be found
brezzy badger 5.10



andy108@heis:~$ cd /etc/dffd
andy108@heis:/etc/dffd$ sudo alien --to-deb driver-ipn2220-2.10.03.2004-lark.i586.rpm
Password:
Sorry, try again.
Password:
File "driver-ipn2220-2.10.03.2004-lark.i586.rpm" not found.
andy108@heis:/etc/dffd$



any sugesstions

andy:smile:

---

### Post by 23meg on 2005-12-02
You need to specify the --to-deb argument after the filename. Actually you probably don't even need to specify it, since it will default to making a deb in Ubuntu.

---

### Post by xstation on 2005-12-02
What would the agrument be for example, if its needed as you say?
I think I do not fully understand your reply.  my fault.


andy:smile:

---

### Post by 23meg on 2005-12-02
Try it like this```
sudo alien driver-ipn2220-2.10.03.2004-lark.i586.rpm

```

---

### Post by xstation on 2005-12-02
hi

same result as before.

yesterday there wasno command for alien as the package was not installed now that it is still no progress


andy:???:

---

### Post by 23meg on 2005-12-02
Do you get the exact same error?

And why do you put this file in /etc/dfdd in the first place? Put it somewhere under your home folder, change to that folder in terminal by using "cd" and enter the command again.

---

### Post by xstation on 2005-12-02
ok here's what happened


andy108@heis:~$ cd home
bash: cd: home: No such file or directory
andy108@heis:~$ cd /home
andy108@heis:/home$ dir
andy108  driver-ipn2220-2.10.03.2004-1ark.i586.rpm
andy108@heis:/home$ sudo alien driver-ipn2220-2.10.03.2004-lark.i586.rpm
Password:
File "driver-ipn2220-2.10.03.2004-lark.i586.rpm" not found.
andy108@heis:/home$



andy:???:

---

### Post by mo_x on 2005-12-02
Little typo :) 
driver-ipn2220-2.10.03.2004-1ark.i586.rpm
driver-ipn2220-2.10.03.2004-lark.i586.rpm

l instead of 1 (use tab completion)

---

### Post by xstation on 2005-12-02
many thanks for pointing out my typo

andy:;)

---

### Post by 23meg on 2005-12-02
So you sorted it out now?

---

