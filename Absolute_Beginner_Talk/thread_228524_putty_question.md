---
title: "putty question"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-08-03
i have a windows machine at work and i use putty to connect to my linux box at home but I want to know where in putty I can invoke command
ssh -X abs.net 

there is just a window where i just type abc.net the post is set to 22 by default if i try -X abs.net it does not work

lex1

---

### Post by thingy on 2006-08-03
-X = enables X forwarding

Are you planning on using X clients in windows to connect to the linux box's X server?

If not then you don't need the -X option.

If you do need it, look at the screenshot for where in Putty you can enable X forwarding.

jin

---

### Post by carlosqueso on 2006-08-03
What version of putty do you have?  Mine has a lot fewer options and I spend all day on it.  Where did you get that?

---

### Post by lex1 on 2006-08-03
Thanks for post

I need need to use X in linux box when i connect from a windows machine with putty.#


lex1

---

### Post by thingy on 2006-08-04
Carlos,
 
Its just the standard Putty client I downloaded from the developer's website...maybe you have an older version of it.
 
Here's the URL:
 
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)
 
jin

---

