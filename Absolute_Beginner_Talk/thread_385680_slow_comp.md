---
title: "slow comp"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-03-16
my system is slow.. i dontknow why.. it was fast but its slow now.. is there anything i can do to make it faster like -- restore, scan or soemthing like that.. please

---

### Post by seshomaru samma on 2007-03-16
what is the output of this command :
```
top
```

---

### Post by HunkieChan on 2007-03-16
> **seshomaru samma said:**
> what is the output of this command :
```
top
```

what do you mean

---

### Post by maxamillion on 2007-03-16
Open a terminal and type the command "top" into it .... or install htop and run it by:

Open a terminal and enter the command:
```
sudo aptitude install htop
```
it will ask for your password, enter it

then it will ask [y/n/?] and enter 'y'

now once that is done and you are presented with a command prompt again do:\
```
htop
```

that will show you the system resource usage in a very nice curses layout.

---

### Post by HunkieChan on 2007-03-16
> **maxamillion said:**
> Open a terminal and type the command "top" into it .... or install htop and run it by:

Open a terminal and enter the command:
```
sudo aptitude install htop
```
it will ask for your password, enter it

then it will ask [y/n/?] and enter 'y'

now once that is done and you are presented with a command prompt again do:\
```
htop
```

that will show you the system resource usage in a very nice curses layout.

but how do i make my comp faster.. like on windows if you did defragement or wahtever you call it.. and it make youurcomp  fast.. you know whati mean.. how can i do that ?

---

### Post by mahiyar on 2007-03-16
Just enter this command in the terminal and post the output or if you can see for yourself what process is consuming  the  maximum  processor power.

---

### Post by HunkieChan on 2007-03-16
> **mahiyar said:**
> Just enter this command in the terminal and post the output or if you can see for yourself what process is consuming  the  maximum  processor power.

oh thanks

---

### Post by HunkieChan on 2007-03-16
one more thing.. when i startup my system so many folder automatically opens up.. how do i disable them.. i tried session but its only temporary..

---

### Post by mahiyar on 2007-03-16
In the system>preferrences>session there is a session option tab. In the tab you might have inadvertently clicked <Automatically save changes> options, remove it, next time while exiting close every window and you should be done.

---

### Post by seshomaru samma on 2007-03-16
the command top will show you which processes are running on your computer
if you disable some of them you will end up with a faster computer

---

### Post by HunkieChan on 2007-03-16
> **mahiyar said:**
> In the system>preferrences>session there is a session option tab. In the tab you might have inadvertently clicked <Automatically save changes> options, remove it, next time while exiting close every window and you should be done.

that worked.. thanks a lot.. the other guy thank you too..

---

