---
title: "Can't Add Remove Any Programs"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by mikeric on 2008-03-16
I had been having issues trying to installing thunderbird, and now i realized it is with whatever program i try to install. It does it using add remove programs, the package manager, or the terminal.

With Add/Remove programs i get this:
The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection. 
Then it goes through like two different loading things and back to how the Add/Remove  is when you open it.

---

### Post by Oldsoldier2003 on 2008-03-16
> **mikeric said:**
> I had been having issues trying to installing thunderbird, and now i realized it is with whatever program i try to install. It does it using add remove programs, the package manager, or the terminal.

With Add/Remove programs i get this:
The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection. 
Then it goes through like two different loading things and back to how the Add/Remove  is when you open it.

System >Administration >Software Sources. Enable the first 4 repositories, or all 5 if you plan on compiling sources..

then in a terminal (its faster)
```
sudo apt-get update
```

From there you should be able to use synaptic, add/remove programs or apt-get to install proggies with no problems.

if you get any error messages please reply with them here and we can help you sort it out.

---

### Post by mikeric on 2008-03-16
Thanks so much for the help, I wish i had known it was that simple, everything is working now.

---

