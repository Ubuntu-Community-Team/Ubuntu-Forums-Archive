---
title: "RockBox on 1st Gen Nano ipodpatcher problem"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by bryak on 2007-03-05
I am trying to RockBox my Nano so it can play ogg files.

I hate it when this happens, but i've hit a stumbling block very early in the process.  I've been following the instructions to a tee.  At the point when I typed

> chmod +x ipodpatcher

a fresh command line comes after, not showing any errors or anything.  then, when i type 

> ipodpatcher --scan

i get...

> bash: ipodpatcher: command not found

it might as well have said bash: yourheadintothekeyboard: idiot

I'm sure it's something simple, ideas?

---

### Post by Vivix729 on 2007-03-05
Your iPod is plugged in, right?  Not sure what to tell you, I did it quite easily on my sister's Windows machine.

---

### Post by bryak on 2007-03-05
Yup.  Plugged in and present on my desktop.

I'm thinking I'm doing something wrong with the chmod command or something, because it doesn't really look like it's doing anything.

here's the whole shmgiggy.

> bryce@bryce-laptop:~$ cd Desktop
bryce@bryce-laptop:~/Desktop$ chmod -x ipodpatcher
bryce@bryce-laptop:~/Desktop$ ipodpatcher --scan
bash: ipodpatcher: command not found
bryce@bryce-laptop:~/Desktop$

---

### Post by Vivix729 on 2007-03-05
I got it.  I downloaded the thing and tried it myself.  Got the same error.  But this worked:

```
./ipodpatcher --scan
```

My output:

> beast@beast:~$ chmod +x ipodpatcher 
beast@beast:~$ ipodpatcher --scan
bash: ipodpatcher: command not found
beast@beast:~$ ./ipodpatcher --scan
ipodpatcher v0.8 with r12194-070204 bootloaders - (C) Dave Chapman 2006-2007
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

[INFO] Scanning disk devices...
[ERR]  No ipods found.
beast@beast:~$ 


---

### Post by bryak on 2007-03-05
so close!

> bryce@bryce-laptop:~$ cd Desktop
bryce@bryce-laptop:~/Desktop$ chmod -x ipodpatcher
bryce@bryce-laptop:~/Desktop$ ./ipodpatcher --scan
bash: ./ipodpatcher: Permission denied
bryce@bryce-laptop:~/Desktop$

tried it under root, same answer.

as a side note; any chance to a link on a newbie tutorial on what things like ./ mean so I can save trouble of bothering folk in the future?

---

### Post by Vivix729 on 2007-03-05
You get permission denied under root?  What did you use, "sudo su"?

Just for the hell of it, put the file in your home folder and run it from there.

Also, just to make sure...you DID download the Linux version of ipodpatcher, right? :-P

---

### Post by bryak on 2007-03-05
I did it the sad, little beginner's Windows style Applications --> System Tools --> Root Terminal.

when i did it your way, the error was different than I'd thought...

> bryce@bryce-laptop:~$ cd Desktop
bryce@bryce-laptop:~/Desktop$ chmod -x ipodpatcher
bryce@bryce-laptop:~/Desktop$ sudo ./ipodpatcher --scan
Password:
sudo: ./ipodpatcher: command not found

and i got the ipod patcher from this RockBox repository

/bootloader/ipod/ipodpatcher/linux32x86

---

