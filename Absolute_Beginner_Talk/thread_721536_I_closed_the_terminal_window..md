---
title: "I closed the terminal window."
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by balakumar on 2008-03-11
The problem is simple.
I closed the terminal window when some actions were taking place.
Not it does not allow me to run anything 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

this is the reply i get.

dpkg --configure -a

How do i activate power user and how can the root user be used.
IPlease tell me what i should do now because i dont know much about the terminal scripts and how to use it.It was my windows habit. I just did it without realising. Sorry for the trouble guys.

---

### Post by MRiGnS on 2008-03-11
```
sudo dpkg --configure -a
```

---

### Post by Arkenzor on 2008-03-11
Anytime you need to run a command with super-user (administrator) privileges, simply prefix it with "sudo". For example
```
sudo dpkg --reconfigure -a
```
should work. It allows you to complete a software installation that was interrupted by accident.

---

