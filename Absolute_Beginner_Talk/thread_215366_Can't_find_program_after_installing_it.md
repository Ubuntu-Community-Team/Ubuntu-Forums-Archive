---
title: "Can't find program after installing it"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by octathlon on 2006-07-13
I just installed links2 using the package manager, but where is it?  I did a "Search for Files" for links2 and links, but it didn't return a match.  

I imagine that question has been asked before, but I can't find a way to search for a phrase or ALL words ... If I enter "find installed program" or find AND installed AND program, the search acts like I did a find OR installed OR program and returns way too many irrelevant results, making it impossible to find the threads I need.  

I have **lots** of questions, so if anyone knows a more practical way to search, please advise. :confused: 

Thanks

---

### Post by croak77 on 2006-07-13
Links is a console app. If you are using Xorg, just open a terminal and type links2 [www.google.com](www.google.com) or whatever site you want to visit.

---

### Post by meng on 2006-07-13
If I've just installed something, I always "sudo updatedb" before searching for it.

---

### Post by octathlon on 2006-07-13
Croak77: Thanks! I had tried to start it with Alt-F2 and it gave me an error.  But I typed it into a terminal window and it started! :)

meng: What does "sudo updateb" do?  Some additional step that the package manager doesn't do?  Thx

---

### Post by mcduck on 2006-07-14
> **octathlon said:**
> Croak77: Thanks! I had tried to start it with Alt-F2 and it gave me an error.  But I typed it into a terminal window and it started! :)

meng: What does "sudo updateb" do?  Some additional step that the package manager doesn't do?  Thx

Ubuntu has a database-based console search tool called 'locate', that is very quick in finding things from your system. But as it uses database, it won't find new things until the database is updated. This happens usually once a day, but if you have just installed something you might want to update that database manually, and 'sudo updatedb' does that for you.

---

### Post by octathlon on 2006-07-14
Thanks, McDuck! I tried "locate links2" and it displayed all the relevant locations.:) I'll remember that command.

---

