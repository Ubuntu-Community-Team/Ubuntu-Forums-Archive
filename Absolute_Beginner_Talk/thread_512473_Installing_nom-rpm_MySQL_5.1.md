---
title: "Installing nom-rpm MySQL 5.1"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by algone on 2007-07-29
Hello,
I need help, am new to Ubuntu, and am trying to install the MYSQL 5.1 non-rpm version using the instructions on [http://dev.mysql.com/doc/refman/5.1/en/installing-binary.html](http://dev.mysql.com/doc/refman/5.1/en/installing-binary.html). I unpacked and created a symbolic link to the unpacked folder, however when trying to change to the mysql folder, I get file not found error, even though I see it there. Can someone explain to me whats happening and how i can proceed.

Thank you

---

### Post by Nevis on 2007-07-29
From the instructions it seems that the folder belongs to the group 'mysql'. I could very well be wrong but I suspect if you added yourself to the mysql group you'd have better luck.

However, I don't use mysql and I don't know if it's intended for users to have access to these folders.

---

