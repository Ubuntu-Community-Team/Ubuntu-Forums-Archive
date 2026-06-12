---
title: "How to start a script at a specific time of the day ?"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-12-08
a job that is entered once (entered once via xterm) and will work even if pc is rebooted ... 
 
'cos at doesnt work 'cos at has to be reentered once the script has been started ... 
 
someone knows ,??

thank you !!

---

### Post by fourchannel on 2005-12-08
two things come to mind. 

cron

at

both of those will execute scripts at a given time, however 'at' is for one time only, 'cron' is repetitious. they will both work through reboots, as long as the downtime doesn't occur when the script is supposed to execute

---

### Post by patrick295767 on 2005-12-08
Thank you very much !!!!
I got some troubles with at last time
I had to do atrm on about 15000 jobs !!
I did run a loop script in order to remove all them... 
  Noob mistakes :-) :-) 
  
  
cron is the best for sure !!

Greetings'

---

### Post by fourchannel on 2005-12-08
haha, you gotta love those. I replicated one of my webservers using wget and every directory had 8 INDEX.HTMLs. there were like 500 of them of them to remove. was no fun.

---

