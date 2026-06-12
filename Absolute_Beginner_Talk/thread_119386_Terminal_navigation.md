---
title: "Terminal navigation"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by _Lawless on 2006-01-19
I seem to remember a thread a while back that explained, very nicely I might add, how to navigate using terminal. Am I just missing it?
If there is not a sticky about it there really should be. It was VERY informative.

In the mean time I'm trying to figure out how to navigate to the /sbin folder to run a command.

I finally figured out smb and printers on my home network so I have the basics working YEAH!!!!

Now I'm going thru and installing programs such as teamspeak(got it working!) and now Hamachi. 

Getting very excited about Linux now after 6 frustrating months of teaching this old dog new tricks.
Not saying that everyone is going to have the problems I did. I have special circumstances that made Linux difficult to set up for my network.

Thanks in advance!

---

### Post by lha on 2006-01-19
[QUOTE=_Lawless]I seem to remember a thread a while back that explained, very nicely I might add, how to navigate using terminal. Am I just missing it?
If there is not a sticky about it there really should be. It was VERY informative.

In the mean time I'm trying to figure out how to navigate to the /sbin folder to run a command.

I finally figured out smb and printers on my home network so I have the basics working YEAH!!!!

Now I'm going thru and installing programs such as teamspeak(got it working!) and now Hamachi. 

Getting very excited about Linux now after 6 frustrating months of teaching this old dog new tricks.
Not saying that everyone is going to have the problems I did. I have special circumstances that made Linux difficult to set up for my network.

Thanks in advance![/QUOTE]

If you want to get into /sbin, do
```
cd /sbin
```

If you want to run a binary that lies in /sbin, you don't have to cd there. Just type the command in terminal. /sbin and half a dozen of other directories are in your PATH by default. You can use
```
env|grep PATH
```
to list all folders in your PATH. Any executable file in any of those folders can be executed by typing merely the name of that file.

---

### Post by _Lawless on 2006-01-19
Fantastic!
Thanks.

---

### Post by Sutekh on 2006-01-19
Just to make sure this very good thread stays in the sunlight

[Terminal for Beginners by Kyral]("http://www.ubuntuforums.org/showthread.php?t=73885")

---

### Post by dueY on 2006-01-19
[QUOTE=Sutekh]Just to make sure this very good thread stays in the sunlight

[Terminal for Beginners by Kyral]("http://www.ubuntuforums.org/showthread.php?t=73885")[/QUOTE]

Everyone should be required to read this thread atleast once! :D

---

### Post by ardchoille on 2006-01-19
[QUOTE=Sutekh]Just to make sure this very good thread stays in the sunlight

[Terminal for Beginners by Kyral]("http://www.ubuntuforums.org/showthread.php?t=73885")[/QUOTE]
Thank you very much for posting that link :)

---

