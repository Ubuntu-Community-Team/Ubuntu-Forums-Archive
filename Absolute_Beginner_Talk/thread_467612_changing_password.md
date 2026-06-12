---
title: "changing password"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by doronb2 on 2007-06-07
hello,

i want to change my password.

i tried "sodu passwd" and "sudo passwd root" but it didn't worked...

any ideas???

---

### Post by Sethalos on 2007-06-07
to change yours: passwd
to change anothers:sudo passwd

---

### Post by pbw on 2007-06-07
no sudo, just passwd.

---

### Post by madmetal on 2007-06-07
system >> preferences >> about me 
up right click button " change password "

---

### Post by pbw on 2007-06-07
> **Sethalos said:**
> to change yours: passwd
to change anothers:sudo passwd

To change another user's would be sudo passwd username.

---

### Post by doronb2 on 2007-06-07
thanks guys.

whats the minimum length of the password?

---

### Post by pbw on 2007-06-07
No idea, dunno if there's a limit. Try something and you'll find out. Not sure why you'd want a borderline too short password though.

---

### Post by madmetal on 2007-06-07
> **doronb2 said:**
> thanks guys.

whats the minimum length of the password?

i got three characters.. not safe but its easy to use.. :KS
i think 4-5 is ok for home use..and if you use sudo and terminal a lot..

---

### Post by doronb2 on 2007-06-07
its very odd...
i have to give 4 characters for the password, but my friend with 7.04 like me have only 1 char'...

how can u explain this??

(i want also only 1 char password because its more fast to enter the password.. its my computer at home and i'm the only user, i don't like that i have to enter password so many times.**. is there is a way to cancel the whole password thing????**)

---

### Post by madmetal on 2007-06-07
> **doronb2 said:**
> its very odd...
i have to give 4 characters for the password, but my friend with 7.04 like me have only 1 char'...

how can u explain this??

(i want also only 1 char password because its more fast to enter the password.. its my computer at home and i'm the only user, i don't like that i have to enter password so many times.**. is there is a way to cancel the whole password thing????**)

are you sure its your account password and not root password?

---

### Post by doronb2 on 2007-06-07
> **madmetal said:**
> are you sure its your account password and not root password?

first of all please explain whats the difference.

and second, if i write "passwd root" it said that i cant modified the password... (WHY?? i'm the ONLY user in my machine!!) i think that tells me that i changed the acoount password...

---

### Post by dondad on 2007-06-07
> **doronb2 said:**
> its very odd...
i have to give 4 characters for the password, but my friend with 7.04 like me have only 1 char'...

how can u explain this??

(i want also only 1 char password because its more fast to enter the password.. its my computer at home and i'm the only user, i don't like that i have to enter password so many times.**. is there is a way to cancel the whole password thing????**)

You really don't want to do that. The only way to get away from the password would be to run as root, which is a bad idea. The password protects you from yourself. As a user, the password prompt is at least an indication that you are about to do something that could damage your system. As root, you could make an error and take out everything, no questions asked.

For me, I am good enough at messing stuff up on purpose without the additional problems of doing it by accident. ;-)

---

### Post by doronb2 on 2007-06-08
ok, thanks, but how can i have a 1 char password???

---

### Post by garydsims on 2007-11-07
> **doronb2 said:**
> ok, thanks, but how can i have a 1 char password???
All security questions aside, will someone please answer the question?

---

### Post by doronb2 on 2007-11-07
> **garydsims said:**
> All security questions aside, will someone please answer the question?

reinstall ubuntu

---

