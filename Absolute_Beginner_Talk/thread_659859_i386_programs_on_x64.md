---
title: "i386 programs on x64?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by wwarsin on 2008-01-06
Hello all, i am fairly new to Ubuntu... 
My question is Should i install the i386 version or the x64 version i have a AMD Athlon 64 X2 4000+ i currently have the x64 version installed, i haven't really tried to install much, but can i run i386 programs on the x64 version?

---

### Post by PmDematagoda on 2008-01-06
The 64 bit version of Ubuntu performs better than i386 especially for memory intensive applications such as encoding since 64 bit uses and handles the memory more efficiently than i386 does, also you may get other performance increases on varying programs as well. 

You can also install and use i386 applications on 64 bit by forcing the application to work under 64 bit through 32 bit libraries. The software in the repositories is pretty much installed that way, you can do that manually using:-
```
sudo dpkg -i --force-architecture nameofpackage
```
But it is highly recommended that you use either the repositories or the 64 bit versions of the applications as much as possible since the above command could cause a few problems.

---

### Post by Perfect Storm on 2008-01-06
My experience, I only stumble upon very very few stuff that doesn't come 64-bit.
Other than that installing 32-bit layers solve the most if it doesn't support 64-bit.

---

### Post by Kimm on 2008-01-06
I run 64-bit and I dont have problems. I run Skype and Flash all the time. And x86 window apps work nicely in wine :)

---

### Post by wwarsin on 2008-01-06
ok thanks for the replys

---

