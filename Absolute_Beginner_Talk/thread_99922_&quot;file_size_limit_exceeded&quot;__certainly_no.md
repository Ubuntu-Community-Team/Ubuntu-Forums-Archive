---
title: "&quot;file size limit exceeded&quot; ?? certainly no one knows the real solution ..."
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-12-06
I change a bit my properties on my gnome-panel (under fvwm)
then 
"file size limit exceeded" 
  
yep,
iimpossible to start any apps and x programs (mozilla ...) ...

I looked on the web
the advices are all not workign and just suggesting reinstalling all !!
  
the best one could have been to change:
/etc/security/limits.conf
to put higher values 
  
that workded, but I am sure there is a expert solution 'cos the probl is not coming from there 
  
thank you very much,

this problem is very difficult question, maybe not for this beginner section
(but I am still beginning or trying to )

Greetings,

patrick

---

### Post by patrick295767 on 2005-12-07
No solutions... 
  
So, I made it : 
you'd have to boot with knoppix cd
then :
e2fsck and put option : 
automatic repair & force the checking even if clean 
  
Result : great
no needs of touching the limits.conf (that was not nice advice from the google search results)


kidn regards, 

pat'

---

