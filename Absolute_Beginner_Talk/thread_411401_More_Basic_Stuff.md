---
title: "More Basic Stuff"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by wmichaelb on 2007-04-16
Today, when I moved to the "bookmarks" tab in Streamtuner, the cursor turned into a closed fist and would not activate any buttons. I could not select another tab nor shut off the program. It continued to play; but I had no control of the program, nor of any function in Ubuntu. How does one shut down an errant program in Ubuntu, given that we have no access to root? Is there a command similar to cntrl-alt-delete in Windows?

Thanks in advance!](*,) ]

---

### Post by finer recliner on 2007-04-16
you may need super user priveledges to do this or be the user that executed the application:

```

$ xkill

```
your mouse will turn into a skull and cross bones. now click on the app you want to force quit, and it will kill that application for you :)
fun and effective.

---

### Post by tchoklat on 2007-04-16
yes you can install a ctr-alt-del utility through synaptic that operates the same as in Windoze.

---

### Post by wmichaelb on 2007-04-16
That's way cool, but when I faced this problem today, I couldn't get the cursor to open terminal. I could get to the command line via ctrl-alt-F2, but xkill won't work from that command line. Is there a command line command that will close open windows?

Thanks!

---

### Post by Ptero-4 on 2007-04-16
killall -9 appname. IIRC

---

### Post by ubromtoo on 2007-04-16
WMICHAELB :

      for 6.06 Dapper , right-click on an empty part of the panel, and a drop-down menu

 will appear. click on "add to panel...."  then in the "desktop & windows" area, click on 

 "force quit" and add it to the panel.  works for me, :)

---

### Post by finer recliner on 2007-04-17
if things are that bad, you can try restarting X  by pressing ctrl + alt +backspace. (this will log you out).

the typical way is what ptero4 was saying. if you can get to an empty terminal (ctrl + alt + f2 for example) type:

```

$ps aux 
//all applications from all users will be displayed
//find your application that froze and note the PID (second column) of it.
$ kill -9 <PID>
//the -9 will force quit the application.

```


since you will be on tty2, your screen res is probably very low and cant see a lot of text at once, so i suggest piping the ps aux command with more or less
```

$ ps aux | more
//press enter to print the next line

$ ps aux | less
//word wrapping and scroll up and down

//press q to exit for either

```

---

### Post by wmichaelb on 2007-04-17
P-tero 4, ubromtoo, and finer recliner: thanks to all of you. That tells me what I need to know. I'm plowing my way through a book on basic Linux system admin, but hadn't found that particular command yet. I'll file that one, just in case. 

I've had a couple of Windows-like freeze ups with Ubuntu that have required me to force the system off with the computer's power switch. It's rare enough that I haven't been able to troubleshoot it; it could certainly be hardware. I fixed most (not all!) of the problems I've had with Windows by building a machine with 2 GB of RAM, and this machine has 1 GB; so that issue is covered (although Ubuntu seemed to run quite well in the beginning with just 256M of RAM). I've got lots to learn!

Thanks to all for your time and expertise.

---

### Post by Ptero-4 on 2007-04-17
It`s good to know your working it out well.

---

