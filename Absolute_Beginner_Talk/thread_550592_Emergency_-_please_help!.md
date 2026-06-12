---
title: "Emergency - please help!"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-09-14
I am now from WinXP. My Ubuntu feisty 7.04 has shown a dangerous problem.
I was working with my printer, and some problems (minor) with printer was noticed. However, I was trying to make the printer work. Suddenly I found that the evince was not working correctly. I restarted and it said that disc space was low; I logged in and tried to kill some processes. But the main problem sustained. I again restarted - but I can't log in now. It says on log in screen that I am OUT of disc space so that it can't write in my home folder .....and so I can't log in.

Please help me out!

---

### Post by simonn on 2007-09-14
Boot from a boot cd and delete some stuff from your home folder?

---

### Post by curuxz on 2007-09-14
Restart the system, then select the failsafe boot entry for ubuntu

should get you to a text based login, login there.

type "ls"

that will get you a listing of files

then "rm FILENAME" will remove the file you have typed in, be careful but that should allow you to clean some space up :)

---

### Post by sauravbhaumik on 2007-09-14
I booted from CD.
Then found that the partition was full, with no free space.
Then I sought for the folder that was of huge size.
```
/var/log
``` was more than 5GB. I emptied it and then emptied root-trash.
I booted my Feisty then.
I am now from Feisty. :)

---

### Post by splintercellguy on 2007-09-14
A possible way to avoid such a catastrophe might be to make a separate ext3 partition for /home, and leave the OS with the free space to grow.

---

