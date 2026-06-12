---
title: "libc.so.6"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by SMS on 2007-03-16
hey can an any one tell me thier out put for
gedit /usr/lib/libc.so.6
thanks

---

### Post by xyz on 2007-03-17
> bash: cd: libc.so.6: No such file or directory

What do you mean?

---

### Post by eljalill on 2007-03-17
for /lib/libc.so.6 :
Could not open the file, 
gedit has not been able to detect character coding .

Why? What is it for?

---

### Post by SMS on 2007-03-17
hey guys thanks for your replies
what it is, is that when i try run certain programs they fail to start up, so i did it in terminal and it say invalid elf header in libc.so.6 so when i opened that libary i cold see a section that said elf header so i wanted to check wht it should say incase mine was wrong. it is really annoying cause i cant even run openoffice

---

### Post by Bachstelze on 2007-03-17
libc6 is definitely not something you should fiddle with. What happened to yours ?

---

### Post by SMS on 2007-03-17
well i tried to install mercury but inorder to install that you have to install java, but now that has messed everything else up lol if you seach "sms" in the seach bar, you can see all the trouble i have had, in that file different from pc to pc if not could send me yours and see if that would work
thanks for you help guys

---

### Post by AtrejuT on 2007-03-17
can't you just reinstall it using synaptic?

(the package is libc6)

---

### Post by SMS on 2007-03-17
tried that but still i get this in the terminal

> 
sms@sms-laptop:~$ ooffice
/usr/lib/openoffice/program/javaldx: error while loading shared libraries: /usr/lib/libc.so.6: invalid ELF header
find: error while loading shared libraries: /usr/lib/libc.so.6: invalid ELF header
head: error while loading shared libraries: /usr/lib/libc.so.6: invalid ELF header
/usr/lib/openoffice/program/pagein: error while loading shared libraries: /usr/lib/libc.so.6: invalid ELF header
/usr/lib/openoffice/program/soffice.bin: error while loading shared libraries: /usr/lib/libc.so.6: invalid ELF header

** (process:5070): WARNING **: Unknown error forking main binary / abnormal early exit ...
sms@sms-laptop:~$ 


---

### Post by SMS on 2007-03-18
hey i have sorted it out i am sooooooooooooooo happy lol
what i did was deleted libc.so.6 -not unistall, Deleted manualy.
then uninstalled open office and rebooted. then reinstalled libc.so.6 and openoffice
yay:guitar: yay back in business
thanks for your help guys u guys are the best

---

