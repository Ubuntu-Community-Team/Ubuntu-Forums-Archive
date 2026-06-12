---
title: "dmesg  boot option"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by silent1643 on 2007-08-30
am i missing something...

as man dmesg states i can use the follow command to view boot messages, but i get nothing? eh

dmesg > boot.messages

and i recieve nothing if i do this tweak
[http://ubuntuforums.org/showthread.php?t=49925&page=2](http://ubuntuforums.org/showthread.php?t=49925&page=2)

---

### Post by DBStevens on 2007-08-31
just enter: 

dmesg   

or better:

dmesg | more

when you did the dmesg > boot.messages you actually created a file named boot.messages in your current working directory.

you then could have done 

more boot.messages 

or

cat boot.messages

or

cat boot.message | more

I'm not going to bother with what is at that link.

---

