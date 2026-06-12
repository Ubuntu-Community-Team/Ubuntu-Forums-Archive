---
title: "Help On Dosbox"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by pearlgdatingaling on 2006-03-06
hi!

i need help in dosbox. i have successfully installed dosbox in my ubuntu linux environment and has  mounted c to /home/lala/cai as the default drive. the problem is, each time i run dosbox.exe, i get a z prompt and everytime i try to type in something, the title bar displays a pause message and i can no longer access the cursor so i end up closing the window instead and not be able to use dosbox at all.

please help. i need to run my dos programs in ubuntu. i already have wine installed.

many thanks!

pearl

---

### Post by gord on 2006-03-06
i don't know about the pause thing. but to make it automatically mount C: you need to create a file called ".dosboxrc" in "/home/<username>/.dosbox/"

this stores configuration information for dosbox and is automatically loaded at startup. 

add this to the file 
```

[autoexec]
# Lines in this section will be run at startup.
@echo off
mount C /home/lala/cai 
C:
@echo on

```

then you will be put in C: when you start up.

---

### Post by pearlgdatingaling on 2006-03-06
[QUOTE=gord]i don't know about the pause thing. but to make it automatically mount C: you need to create a file called ".dosboxrc" in "/home/<username>/.dosbox/"

this stores configuration information for dosbox and is automatically loaded at startup. 

add this to the file 
```

[autoexec]
# Lines in this section will be run at startup.
@echo off
mount C /home/lala/cai 
C:
@echo on

```

then you will be put in C: when you start up.[/QUOTE]
thanks gord, i'll try it now and update you of the status

---

