---
title: "Whats this"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-04-19
E: Type 'dapper' is not known on line 4 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

How do i fix this? I cant go to add and remove programs

---

### Post by x64Jimbo on 2007-04-19
Looks like you're having troubles related to wine. Did you install it? If so, can you show the tutorial that you used?

---

### Post by kpkeerthi on 2007-04-19
Did you add a wine repository lately? The file /etc/apt/sources.list.d/winehq.list is probably incorrect. 
```

cat /etc/apt/sources.list.d/winehq.list

```
.. and post the content...

---

### Post by mojo123 on 2007-04-19
I dont really remember, is there a way i can fix it, i installed wine a week ago, it was fine back then



edit
 ## WineHQ - Ubuntu 6.10 "edgy eft"
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
dapper main

---

### Post by eyelessfade on 2007-04-19
cat /etc/apt/sources.list.d/winehq.list please

---

### Post by eyelessfade on 2007-04-19
oops sorry.
Remove the last line in your file

---

### Post by kpkeerthi on 2007-04-19
gksudo gedit /etc/apt/sources.list.d/winehq.list

delete the last line that read dapper main. Save and Retry.

---

### Post by mojo123 on 2007-04-19
guys thank you so much, how are u guys so fast?

---

