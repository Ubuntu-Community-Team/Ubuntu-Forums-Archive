---
title: "Question about the services loaded when Ubuntu Starts.Please help~~`"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by Wong3 on 2006-03-28
Serious Users,I got so sad to see that my ubuntu can start properly.when it begins to load the various services,it comes to a halt when the "Enterprise Volume Management System" service starts,and it makes me waiting for even 10 minuters,but still not work.

I have re-installed the ubuntu system for 3 times,but the question still disturbes me.

Everytime when the install is finished,i can come to the GUI,but when I restart the system,the bad case abovt occours.

Please help me~~`

---

### Post by nanotube on 2006-03-28
try hitting control-c to skip that, and see if that works.

---

### Post by Wong3 on 2006-03-28
Thanks,
       I've tried that,but that still doesn't works.

---

### Post by codejunkie on 2006-03-28
open a terminal and enter ```
sudo update-rc.d -f evms remove
```this will disable the "Enterprise Volume Management System" service.

---

### Post by Wong3 on 2006-03-30
Thanks,
    I,myself,absolutly a beginner,do not know how to open a terminal and enter,My boot menus only have the following options besides Windows XP: ubuntu kernel,and its recovery mode.So Please explain further more on how to open a terminal...
    Waiting for your help,kind man!!!

---

### Post by _teo_ on 2006-04-30
[QUOTE=Wong3]...I,myself,absolutly a beginner,do not know how to open a terminal...[/QUOTE]
It's simple: you will find it in Applications menu (on the top of your screen). It's located in Accessories submenu.

---

### Post by Rinzwind on 2006-04-30
[QUOTE=_teo_]It's simple: you will find it in Applications menu (on the top of your screen). It's located in Accessories submenu.[/QUOTE]

codejunkie and _teo_: And how does he get there when Ubuntu doesn't boot?

Hmm?

---

### Post by Rinzwind on 2006-04-30
Wong:

I am a newbie too but I think this will work ->

Inside Grub select the 'recovery' mode. Not the normal Ubuntu you'd choose to start with.

This will get you to a #-prompt. In there type the command posted by the user named codejunkie :)

---

### Post by hito1 on 2006-05-01
[QUOTE=codejunkie]open a terminal and enter ```
sudo update-rc.d -f evms remove
```this will disable the "Enterprise Volume Management System" service.[/QUOTE]


What does this Enterprise Volume Management System do?

---

### Post by codejunkie on 2006-05-02
[quote=hito1]What does this Enterprise Volume Management System do?[/quote]
i don't know for sure but i disabled it, and i haven't noticed any ill affects, but what it's for i have no idea.

---

