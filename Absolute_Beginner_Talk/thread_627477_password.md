---
title: "password"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by irshan on 2007-11-30
im new to linux and now i installed ubunto 7.0, waht my problem is i try to log onto admin part but i coudnt, dont know why, when i try to go SU it is ask username and password then when i type password it says authontication failure so i can know my password and how to go SU

---

### Post by ZipoTe on 2007-11-30
Ubuntu comes with "su" disabled. What you can do is

sudo su

it should work :popcorn:

---

### Post by hyper_ch on 2007-11-30
Uubntu uses sudo, see here for more details:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by quandary on 2007-11-30
> **irshan said:**
> im new to linux and now i installed ubunto 7.0, waht my problem is i try to log onto admin part but i coudnt, dont know why, when i try to go SU it is ask username and password then when i type password it says authontication failure so i can know my password and how to go SU

Login as administrator is disabled by default. You have to enable it. 
Go to:
System->Administration->Login Windows-> Security tab
Click on "allow local system administrator login", click close afterwards.

Then type: sudo passwd
You're then prompted to enter a password for root.
Enter your password, remember it.

Log out.
In the login window login as user "root"
type your password

You're now logged in as root. 

PS: Careful, you can damage your system if you're logged in as root...

---

### Post by hyper_ch on 2007-11-30
No need to tell how to enable root. Once people have the skills to permanently login as root they will know how to do it anyway. Before that's it's just risky.

---

