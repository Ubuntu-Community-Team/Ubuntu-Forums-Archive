---
title: "configure script problems"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by RM_Thomas on 2007-05-31
Hi,
Im trying to compile a program and the configure script gives an error about the c compiler cannont make executables, im fairly certain its a base install of ubuntu 6.06 my dad did the install or i would know for sure, i installed gcc because it was missing. Anyone know what i can do to fix this?

Thanks
Nathan

ps sorry if i dont give enough details just ask if you need more

---

### Post by aidanr on 2007-05-31
well you need to install build-essential (sudo aptitude install build-essential) and also any other dependencies the program needs to run/build

if you can post the exact error and also the name of the program you're trying to compile

---

### Post by RM_Thomas on 2007-05-31
oh yeah its prboom. Now it wont run the configure becaues of open gl support but i think thats a hardware issue but i just realized its in synaptic anyway so ill try that.

thanks,
nathan

---

