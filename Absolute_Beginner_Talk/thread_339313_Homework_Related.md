---
title: "Homework Related"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by The Tronyx on 2007-01-15
Hello all!

I have a question about a homework assignment for my intro to linux class and yes, I am using Ubuntu.  The question is as follows:

Make certain you are in your home directory.  Change your command prompt so that it shows your current working directory with an exclamation point, such as *mydirectory!*  Change to the spreadsheets and then to the documents directory and see how the prompt changes.

I understand pretty much everything in these exercises but I cannot, for the life of me, figure out how to change that part of the command prompt, I have re-read the chapters numerous times as well! ](*,) 

I'm not asking for answers, just a push in the right direction I suppose.  I can't even find anything with google, the search criteria is just so....vague.

Thanks for all your help and patience!

---

### Post by meng on 2007-01-15
The bash prompt representation is a shell variable:
[http://www.linuxjournal.com/article/3215](http://www.linuxjournal.com/article/3215)

---

### Post by The Tronyx on 2007-01-15
That was a little over my head...I'm only in my first week.:oops:

I can understand what echo $PS1 displays, but not how to use the command modifiers to have the ! appear.

---

### Post by Lord Illidan on 2007-01-15
Try this : PS1="\w ! "

---

### Post by The Tronyx on 2007-01-15
Thank you so much!

I wasn't seeing before that PS1=" " was the format for modifying.

Thank you again.

---

### Post by Lord Illidan on 2007-01-15
> **2point0 said:**
> Thank you so much!

I wasn't seeing before that PS1=" " was the format for modifying.

Thank you again.

No problem. I got it from the site above. Experimenting is the best way of learning, don't forget it!

---

