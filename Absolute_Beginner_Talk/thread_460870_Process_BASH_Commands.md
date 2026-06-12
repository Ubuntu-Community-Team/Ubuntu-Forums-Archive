---
title: "Process BASH Commands"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Drezard on 2007-06-01
My Ubuntu seems to have problems (most likely me) some programs continously freeze. Now, I know this is probably just my computer and I would like to learn the BASH Commands to view what process's are open and to close a process. So basically like in Windows (I know thats a banned word around here) when u hit ALT + CTRL + DEL then go into the process manager, u can close processes. How do I view and close processes like that in BASH Commands?

Thanks, Daniel

---

### Post by mendingo84 on 2007-06-01
All of this in a terminal:

to view all processes
```
ps aux
```

to kill a process 

```
kill -9 <process_number>
```

for better explanation, also in terminal, 
```
man <command_name>
```

And, unlike in the Windows community, no one will rip your head off if you pronounce Windows around here. Relax. ;)

---

### Post by Drezard on 2007-06-01
I love it how windows users are so scared of linux. I think Linux is a great OS, it was easy to install and rather easy to use. I also like the whole Terminal BASH thingo, it makes me feel like a proper computer geek :)

Also my next question would be:

I have tired to install Webmin (Yea, im having a play with all the cool linux technologies) and for some reason the installer has frozen.  How do i use ps aux to find this process?

Thanks, Daniel

---

### Post by mendingo84 on 2007-06-01
terminal,

```
ps aux | grep <process_name>
```

---

### Post by Drezard on 2007-06-01
but.... how do i know what the process name is? So how do i find out such as.... if Im running the package (i downloaded the package) from my desktop... (home/user/Desktop) then how do i find any processes running from that location?

Regards, Daniel

---

### Post by mendingo84 on 2007-06-01
you don't have to know the exact name of the process. for instance, if you type
```
ps aux | grep <your_user_name>
```
that will give you all the processes run by you.  so if you were the one launching that process, you should have it listed with that command.

---

