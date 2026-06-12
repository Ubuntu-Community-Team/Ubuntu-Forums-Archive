---
title: "how do i run a job on another computer useing ssh"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by paxmanchris on 2007-03-08
i have a computer at my house. i am able to connect to it via ssh. 
i want to log into that computer and run a job on it, so that by the time i get home it will be done.

i have tried to do background processing. with the & symbol and the bg  fg commands. but when i close the terminal window the process stop.

my situation is that, im as school. i find a torrent, like a new ubuntu ISO. but i don't want to wait till i get home to download it. so i want to run the command line torrent tool off my computer at my house so that i will always be downloading, as long as that computer is on.

hopefully i made my situation very clear.

please let me know what sloutions there are, and how to use them.

---

### Post by Bachstelze on 2007-03-08
```
screen
```

is your best friend :)

In a nutshell, when you run *screen*,, it wil open a new shell/ You can then run a command in it and while it's running, do Ctrl+A-Ctrl+D to detach it and go back to the previous shell. Now you can safely exit it and close the ssh session, the process you started in *screen* will continue to run. Then, when you log in again, do *screen -R* and voilà.

As I always say, *screen* is the greatest invention of mankind since canned beer :D

---

### Post by paxmanchris on 2007-03-08
Sweet! this is what im looking for. thank you very much

---

