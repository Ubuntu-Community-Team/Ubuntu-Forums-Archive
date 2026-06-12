---
title: "Ouch :S my root account is gone"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by black_ice on 2007-03-13
hello all 

i have tried to make my account is the root and i enter the /etc/passwd file and i edit and make the number of user id to 0 to became a root and root  is gone :S 

I have no name!@adam-laptop:/etc$ su 
Sorry.



what i can do to make root come back i need it urgently

---

### Post by ardchoille42 on 2007-03-13
> **black_ice said:**
> hello all 

i have tried to make my account is the root and i enter the /etc/passwd file and i edit and make the number of user id to 0 to became a root and root  is gone :S 

I have no name!@adam-laptop:/etc$ su 
Sorry.



what i can do to make root come back i need it urgently

The root account in Ubuntu is locked. There is no need to ever log i as root. Use sudo to do admin tasks. Have a look at [this page]("https://help.ubuntu.com/community/RootSudo").

---

