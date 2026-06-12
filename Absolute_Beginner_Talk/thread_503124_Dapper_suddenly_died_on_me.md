---
title: "Dapper suddenly died on me"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by shivling on 2007-07-17
dear all, 

My ubuntu dapper has gone dead! while trying to log on i get the following message: 

loading drivers ok 
mounting root file systems ok 

and then nothing. 

while try to boot using 
ubuntu kernel 2.6.15-27-386 (recovery mode) 
I get a lot of numbers. 
the last set of numbers are like this: 

run -init: /sbin/init :error 20 
[17179578.49 2000] kernel panic - not synching: attempting to kill init! 

and the system just stands still! 

shortly before i downloaded and installed skype. could that be a reason? 

please help 
sk

---

### Post by Rocket2DMn on 2007-07-17
Can you try booting into another kernel?  perhaps a generic one?  Check your boot menu and see what other options there are.

Kernel panic means the kernel hit an error and could not continue.  The not synching part is good - it means your hard drive is not being written to.  if it was writing, it could be corrupting stuff.

---

### Post by ajgreeny on 2007-07-17
One good reason to make sure you always keep one older kernel on your system, I think.  At least, that will be so if it's still possible to boot from it!

---

