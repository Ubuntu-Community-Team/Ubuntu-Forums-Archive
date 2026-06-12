---
title: "&quot;File size exceeded&quot; message =&gt; Xsession stops. Please Help."
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-01-24
Hi, 
I got this error message when doing: 
```
startx
```
  
that happened sometimes, but that was solved with recovery console
with e2fsck -f -p /dev/hda2
(my hda2 is my linux main partition)
 
It is not helping anymore now... 
I dont know what to do / how to have my linux  box working again ... 
:-(
  
Thank you very much if you'd know what to do ...

Patrick

---

### Post by patrick295767 on 2006-01-24
(also not working via gdm )
 
my fvwm sessions starts but no rox , no xterm , nothg can be started
then the X session stops after few seconds ... 
 
 
I dont know what to do to solve it ...

---

### Post by patrick295767 on 2006-01-25
That fixed it : 
>   

:: Linux ::

File Size Limit Exceeded Error Solved
5. 'FILE SIZE LIMIT EXCEEDED' ERROR

This one was a doozy. I got this error message when I tried to su from a regular user account. This is what I would get 

[jkeane@laptop jkeane]$ su
Password:
Error: file size limit exceeded
[jkeane@laptop jkeane]

and I was stuck. It took me forever to figure this one out online. First I checked proc/sys/fs and the files in there. Issuing 'cat file-max' will show you the maximum files that a user can open. Issuing 'cat super-max' will show you the same information for the root user. I increased both of these, but unfortunately it didn't help. I finally found the answer in a very obscure corner of the net (and my file syste). You have to check etc/security/limits.conf. Don't ask me why this file is here, but it sets the max limit for user files to 100mb. This is completely inefficient so I pico'ed the file and changed the appropriate line (the last I think) to the following: 

# limit size of any one of users' files to 100mb
# originally set to 100000, reset to 500mb
* hard fsize 500000

This fixed the problem and I was good to go. 
  
Is it the right solution ? 
(in terms of security and so on ... ).?
  
Thank you, 

Pat'

---

### Post by patrick295767 on 2006-02-12
This solution from  [http://www.madirish.net/tech.php?section=5&article=27](http://www.madirish.net/tech.php?section=5&article=27)
  
is not working when I created a very big file of about 6-8 GB
  
In linux breezy, it's therefore not possible to have such big file. I dont know how can people download DVD from p2p without any problems ? :-k 
  
Thnak you if you have some further information, 

Kind regards, 

Patrick

---

