---
title: "newbie cant get command line CD to work"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by mpooley on 2007-03-11
Please help i'm going nuts!
i have just installed ubuntu and i'm trying to get my printer to work.#I have downloaded the drivers to Home/mike/Drivers/Printer folder 
I need to run a command in that folder so i am trying to CD to it but nothing works!!
command line always seems to open in the desktop folder and if i DIR i see the Drivers folder in it -- (which as far as i' can work out it isnt?)  
anyway i tried 
mike@mike-desktop:~$ cd /Drivers  and got
bash: cd: /Drivers: No such file or directory  :confused: 
i did a PWD and got ------ /home/mike
so it seems i'm actually in the right directory and Drivers is Actually there but obviously i'm doing something wrong:confused: 

I've tried lots of other permutations but always get -- no such directory
can anyone help please

Mike

---

### Post by aidanr on 2007-03-11
cd Drivers/

/Drivers would be in the root directory

/
/Drivers
/home

;)

---

### Post by eljalill on 2007-03-11
if you want to get to a folder in the same directory you are currently in type
"cd driver"
Without the slash.

generally "man cd" gives you the sytax for that command.

---

### Post by Crooksey on 2007-03-11
```

$ cd ~/Drivers/

```

---

### Post by seshomaru samma on 2007-03-11
no need for  / inside your home directory
also notice that linux is case sensitive , so if the folder is called Drivers , then 'cd drivers' wont work.

---

### Post by mpooley on 2007-03-11
Thanks All :KS 

sometimes it the simpest thing thats the hardest!

Mike

---

