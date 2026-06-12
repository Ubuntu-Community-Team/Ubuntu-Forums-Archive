---
title: "KILLing a process in the baclground"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Dodelijk on 2008-01-16
Hello, 

this is a general Linux question: 

i want to kill/end a process that i have called from a terminal. 

Here's my typical situation: 

I'm using a terminal and I open up gedit: 
I then put gedit in the background, by pressing "Ctrl + Z".
Now I can (re)use the terminal. 
Now say I want to close gedit, without closing the terminal, how do I do it? 

I tried typing "jobs" and finding the number associated with gedit and then 
typing "kill 1" (1 being gedit's job number). 
But this doesn't work. 

Thanks...

---

### Post by bodhi.zazen on 2008-01-16
kill -9 `pidof command`

note those are bac tics ` by the number 1 not single quotes

You can also 

killall command

---

### Post by Dodelijk on 2008-01-16
sorry you've lost me. 

what is "pidof"

i tried killall and that didn't work

---

### Post by geirha on 2008-01-16
to kill job 1, run "kill %1"

---

### Post by bodhi.zazen on 2008-01-16
pidof is a command that will give you the process id of a running command

enclosing it in back tics ` executes the command

which is then used by kill -9 to terminate the program

The alternate is to manually look up the job or pid with say 

ps aux | grep command

then use that info in kill

---

### Post by Dodelijk on 2008-01-16
ok, 

Thanks for the replies. I'm stuck in windows for the moment i'll have a go when  i next reboot. 


Thanks

---

