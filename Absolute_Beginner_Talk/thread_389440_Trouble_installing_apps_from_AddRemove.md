---
title: "Trouble installing apps from Add/Remove"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by xjesse on 2007-03-20
Hello, I am new to these forums and I would first of just like to welcome myself. I see A LOT of activity in these forums. A lot more than in Freespire's....  

Anyways, after selecting the application that I would like installed & and after clicking "apply",  I get the error box saying, "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. ":confused: 

I guess I'm use to CNR. :lolflag: 

I have my Konsole open..
tell me where to go from there. 

I did a light search for this problem but really did not find anything useful. Any response at all will be greatly appreciated! :)

---

### Post by JustinAlf on 2007-03-20
I would try installing from Synaptic Package Manager.  You could be having a problem with privileges for your user name.

---

### Post by zvacet on 2007-03-20
When you open terminal type command
```
dpkg --configure -a
```


or just copy/paste from here

---

### Post by PurplePenguin on 2007-03-20
Don't be afraid of messages like that... as zvacet mentioned, all you have to do is what the message says: open a terminal and type 'dpkg --configure -a' and your problems should be solved. :)

---

### Post by xjesse on 2007-03-21
Well wow. You sure did point out the obvious! Haha, thank you for the replies. Off I go with my head between my legs. :P

Problem solved, of course.

---

