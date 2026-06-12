---
title: "What on earth does this mean?"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-05-04
Hi all! :) 

Every time I boot and I put in my password for Firestarter, I then get this error message:

"[B]Failed to run /usr/sbin/firestarter               as user root:
Child terminated with 1 status[/B]"

I reinstalled firestarter but it still happens.

Is this normal?  What does this "Child terminated" mean? :confused: 

Russty.

---

### Post by jason.b.c on 2006-05-04
[QUOTE=Russty of Oz]Hi all! :) 

Every time I boot and I put in my password for Firestarter, I then get this error message:

"[B]Failed to run /usr/sbin/firestarter               as user root:
Child terminated with 1 status[/B]"

I reinstalled firestarter but it still happens.

Is this normal?  What does this "Child terminated" mean? :confused: 

Russty.[/QUOTE]


It means your dealing with a machine from the future, Sent back through time, A metal endo-skeleton covered with living tissue..;) 

*Terminator 1 & 2 *

---

### Post by Russty of Oz on 2006-05-04
Oh, really?  So how are things in Wonderland Alice?  (only joking)

---

### Post by jason.b.c on 2006-05-04
[QUOTE=Russty of Oz]Oh, really?  So how are things in Wonderland Alice?  (only joking)[/QUOTE]


I thought it was preaty funny..;)   No but seriously just stick with it and keep bumping up your thread, you'll get your answer..

Somebody knows...;)

---

### Post by Russty of Oz on 2006-05-04
Yes, I thought it was funny too.

---

### Post by r4ik on 2006-05-04
You could do a keyword search for sudoers + visudo and you will find information.

Good luck !

---

### Post by Russty of Oz on 2006-05-04
I don't understand what that means, but I will give it a try.

Thanks.

---

### Post by Mustard on 2006-05-04
Are you putting in your user password?  

Do you have sudo privileges on your system?

Type in this command in the Terminal and tell me what it outputs..

```
sudo whoami
```

---

### Post by Russty of Oz on 2006-05-04
After putting in my password it just said      

root

Was it being rude to me? ;)

---

### Post by Mustard on 2006-05-04
[QUOTE=Russty of Oz]After putting in my password it just said      

root

Was it being rude to me? ;)[/QUOTE]
That's a good sign.  You've definitely got superuser priviliges.  If you are putting in your user password to start up firestarter, then I'm not quite sure what the problem is atm.

---

### Post by Russty of Oz on 2006-05-04
Oh well, I think firestarter still works though, as I can open it form Applications > System tools, and it says it is active, it is just that when I start up that error message always appears.

---

