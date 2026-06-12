---
title: "Automatic Shutdown Software"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by DarkFlasher on 2007-04-15
I was wondering if there are any programs available that automatically shut down your Computer while running Ubuntu after a certain amount of time. Like how you would have Chrono Shutdown for Windows.
Please reply if you know of any software that can do so.:rolleyes:

---

### Post by Austin_KW on 2007-04-15
look at the help for cron and at
man cron
man at


also shutdown takes a time argument
to shutdown now "sudo shutdown -h now" or "shutdown -h 0"

to shutdown in 5 mins "sudo shutdown -h 5"

---

### Post by david_kt on 2007-04-15
You do not need any program to do that. For example you want to shutdown at 11:00pm, just open a terminal and type:

```
at 11:00pm <enter>
```

and after that type:
```
>sudo halt <enter>
>your password <enter>
<ctrl>d
```

To study more about how to use "at" command, tyoe in terminal:

```
man at <enter>
```

DK

---

### Post by dpar on 2007-04-15
Your questions seem to have been answered in your other post........[http://ubuntuforums.org/showthread.php?t=409792](http://ubuntuforums.org/showthread.php?t=409792)

---

### Post by alejaaandro on 2008-01-15
i have a similar question but didn't want to start a new thread..
how can i program ubuntu (7.10) to shutdown after a task has finished.. for exemple i usually leave DeVeDe converting a movie during the night cause it takes pretty long.. i could guess how long it would take and use gshutdown but if i program it too soon i'll have to start the encoding from the beginning (i think.. plz correct me if i'm wrong)..

i guess i should write a script to somehow check the processes and see if mencoder is still running. if it isn't, it should shutdown..then i would program the script to run every now and then (i guess that would be with cron, right?)
 The problem is i only know the basic commands, so i can't make it happent.. could anyone help me?

---

