---
title: "Major Problems!!!"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by blithen on 2007-07-26
Everything is good up until it trys to create the ext3 file system in the partition it just freezes and that's it. I have to hard restart my computer. Right now I'm running of the live CD please help!! I've also checked the CD for defects twice.

---

### Post by blithen on 2007-07-26
Any help?

---

### Post by blithen on 2007-07-26
I did the top command in the terminal and this is what came up

[http://pastebin.com/m55ff80e3](http://pastebin.com/m55ff80e3)

---

### Post by Cypher on 2007-07-26
I've highlighted the appropriate pieces of your log which indicate that the mkfs.ext3 (the program that creats the EXT3) partition crashed. What you have there are remants of a stack trace. The entire crash wasn't caught, but enough of it to indicate that there's an issue.

So, what version of Ubuntu are you using? Did you create brand new partitions? How old is your computer and precisely the hard drive??

---

### Post by blithen on 2007-07-26
The computer itself is about 7 years old. The hard drive is really old...I can't remember how old. Older then the computer. my mom needed a new hard drive for one of her computer back in the day, but the computer didn't register it. So there it sat for like 10 years or so.
I'm trying to install 7.04 and Yeah I'm trying to install ubuntu on new partitions.

---

### Post by blithen on 2007-07-26
Well I it's the hard drive, it's just got to old, and finally is going.
Thanks for the help!

---

