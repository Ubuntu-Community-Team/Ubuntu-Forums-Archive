---
title: "K3B copy DVD problem"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-08-27
I use 1 RW-DVD driver
when I "copy DVD"
it makes a full image
but then it says "unable eject media"
and it stops with an error.
what can I do ?

---

### Post by maximilian35 on 2006-12-31
I have the same problem also. When i want to copy a cd, I get the same error : 'Unable to eject media'

---

### Post by maximilian35 on 2006-12-31
You are right. I solved the problem by running from console.
When I write 'sudo k3b' on the console, problem is solved.

---

### Post by gralbe on 2007-01-09
I too had this problem. My solution was to run the k3b setup program and let it do it's magic. After that it worked as expected.

This is on a fresh install of Edgy and the k3b setup program had not been run before.

Also, fwiw, my normal user was able to use the eject command without issue so I'm not sure why k3b appears to need suid for certain helpers (though it's possibly because other parts of k3b uses suid programs). 

-g

---

