---
title: "[SOLVED] Saving Scripts ?"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by thelugnut on 2008-03-26
I am trying to learn scripts.

All of the tutorials I have read, always say to write the script, which I do, and then save it.

Save it where? Where am I suppose to put the things? I have tried many places but have not been able to get the thing to execute. I always get the message, "Command not found".

So I am assuming I am putting the darn thing in the wrong place. 

Again, where am I suppose to save the scripts ?

:mad::mad::mad::mad:

---

### Post by saj0577 on 2008-03-26
Just save it in yoru home directory, right click it and give it permission to be excutable then double click it.

Saj

Hope it helps

---

### Post by ByteJuggler on 2008-03-26
You can put them anywhere you like. But then, to run them, you need to specify the proper path to the script.  And do note: The "current" folder is NOT on the search path, so even if the script you're trying to run is in the current folder, it will not run if you don't specify "./" at the front.  Also, needless to say, you need to make sure the script is actually marked as executable, otherwise it won't run either ("chmod u+x script")

Aside:  If you create a "bin" folder in your home folder, then when you log in, the system will put that folder on the search path, so any script you put in that folder will be runnable from anywhere without any further fiddling (and without requiring "./" in front if your in the folder.

---

### Post by thelugnut on 2008-03-26
Thank you. I was slowly going nuts. 

I appreciate the instant reply very much.

---

### Post by saj0577 on 2008-03-26
No problem. If that is your problem solved(try it first) then please mark the thread as solved, just so people know when they see your thread in the forums.

Cheers
Saj

To mark as solved. 
At the top of the thread
Click Thread Tools
Click Mark as [Solved]

---

