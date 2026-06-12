---
title: "How to kill a &quot;man &lt;command&gt;&quot; process"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by MoonDoggie on 2008-01-21
If I ```
man fdisk
```

And then I quit out of it by just doing ^Z, how can I kill the process?  (I just found out the correct way to exit a man page is by hitting Q, but how do I kill the process when it says 

```
man fdisk - stopped
```

-Colin

---

### Post by Kulgan on 2008-01-21
I don't know why you would want to end it any other way than by hitting q, but the general command for killing any process is killall. You can see the available processes by issuing "ps ax", and narrow it down by searching with grep:
```
ps ax | grep "man"
```

You can end the processes with killall - I recommend using the -i switch to confirm each kill. Saftey first :P
```
killall -i man
```

Or replace man with any other process name from the last column in ps ax. 

Hope that's what you're looking for 
-K

---

### Post by brennydoogles on 2008-01-21
How are you seeing the process? If you are in the system monitor, you can kill the process from the right click menu. Hope that helps!!

---

### Post by Cypher on 2008-01-21
The "right" way of closing an application that you essentially put in the background by hitting CTRL-Z is to type "fg" to bring that application back into the foreground. Now you can hit the Q  or anything else to close the application.

This also works if you wanted to put some application in the background and forgot the "&" at the end. Once the application has been started, hit CTRL-Z to get to the prompt and type "bg" to allow the program to run in the background while you continue using the shell..

---

### Post by MoonDoggie on 2008-01-21
Thanks Cypher, brennydoogles, Kulgan for being ultra helpful!

---

### Post by frup on 2008-01-21
Hey great I knew about & and q but not about ^Z,fg and bg. I think I may have done ^Z a few times and just not realised what I was doing. This is something I have wanted in conjunction with the top command more than once

---

### Post by Kulgan on 2008-01-21
Now that we're on the topic of basic process management, I think nohup is worth mentioning. It basically ensures that a command keeps running after you have logged out of the session. Useful for torrents over SSH :D

[http://www.is.ed.ac.uk/itus/sce/linuxunix/unix_nohup.html](http://www.is.ed.ac.uk/itus/sce/linuxunix/unix_nohup.html)

---

### Post by arkara on 2008-01-21
ok it is very simple

give 
 
ps

and then 

kill -9 PID(this is the number in front of your running applications.)

---

