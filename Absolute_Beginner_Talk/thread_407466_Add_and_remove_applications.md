---
title: "Add and remove applications"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by Istonian on 2007-04-12
Whenever I try to use add and remove applications it loads the third party list and doesnt start. Anyone know what it is?

---

### Post by mrmonday on 2007-04-12
What do you mean by 'the third party lisy'?

---

### Post by mohjlir on 2007-04-12
I don't know what your exact problem is but if you want to install or remove programs, you could try aptitude:

sudo aptitude


Or if you know the name of the program you want to install, use apt-get:

sudo apt-get install gedit


Hope that helps ;)

---

### Post by ajgreeny on 2007-04-12
What is the /etc/apt/sources.list file you're using?  It sounds as if it may not be the complete one for your version.  Copy it and post it here so we can see what repos are active and we may be able to see what's going on.

---

### Post by Istonian on 2007-04-12
I will post when I get home.

---

