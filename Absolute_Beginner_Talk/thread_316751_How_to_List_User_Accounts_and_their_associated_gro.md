---
title: "How to List User Accounts and their associated groups"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by JohnnyAvocado on 2006-12-11
Can someone please tell me how (from a command line as I am running server) you list all the existing user accounts and what groups they are associated with? Thanks so much.

---

### Post by xyz on 2006-12-11
Go System > Aministration > Users and Groups

---

### Post by bluefrog on 2006-12-11
cat /etc/passwd piped with awk should do. you will have to look for the columns you want to isolate (not on linux right now)

James

---

