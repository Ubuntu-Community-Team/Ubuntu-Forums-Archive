---
title: "Why does Epiphany Web Browser randomly crash sometimes?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-01
Okay if it helps the system I'm working with right now is:

MPC ClientPro 345 
376 of registerying RAM
25GB Xubuntu partition
5GB swap

Occationally, Epiphany Web Browser just flatout will crash for no apparent reason. What will happen is the window part will stay up and if I click any of the buttons, say the 'x' or the 'minimize' button, they will indent, but not do anything. The only thing I can do to get rid of it is to go to the System Monitor and end or kill the process. After doing so, when I run epiphany it boots right up no problems and completely recovers everything I was just doing. Now when it comes to what I'm doing while browsing the web? Allow me to elaborate. I've been on for the past 5 hours and it hasn't crashed once even with having close to ten tabs open at times and 2-3 windows of it open. I've ran it using one single tab and one window and had it crash like 3-5 times in one hour. I can't blaim it on the memory usage nor can I blame it on the content of my browsing as it has no issue recovering for me. 

Does anyone else have a similar issue like this? 

What can I do to fix this issue?

Does anyone know the terminal command to end the process? That would save me a lot of time.

---

### Post by PeterJS on 2008-03-01
Keeping us busy tonight :)

Can't offer much in the way of a solution, firefox does this to me sometimes too, seems like it happens when I close tabs with lots of java script.

As for killing Epiphany from a terminal you could use:
```

killall epiphany

```
I'm assuming that's the name of the process.

---

### Post by whoscheesemine on 2008-03-01
I havn't tried the command yet as there is some online work I'm in the middle of, but I do know that when I first installed Xubuntu on his computer I typed

```
sudo apt-get install epiphany
```

and it installed this dumb little game lol

System Monitor refers to it as "epiphany-browser" would that be the appropriate term to use? I suppose trial and error could answer this one and I could answer myself LOL. When I'm done with my work I'll experiment with that one. Thanks you so much for putting up with all my annoying questions.

:popcorn:

---

### Post by PeterJS on 2008-03-01
Yeah, the process name that shows up in the system monitor is what you want to use.

---

### Post by whoscheesemine on 2008-03-01
Alright, thanks a million!

---

### Post by Myglaren on 2008-03-01
Doesn't answer the OP but I find Epiphany to be completely stable.  There has never been a single fault that I can recall.  Unlike Opera.

---

### Post by bapoumba on 2008-03-01
You could launch it from a terminal and see if you get any error message:
```
epiphany
```

---

### Post by CarpKing on 2008-04-07
I've been having this problem off and on again too, with no discernible pattern.  I've tried disabling some extensions, but it still crashes (I still have smart bookmarks and tab groups turned on, but I wouldn't think those would cause trouble).  I'm also pretty sure it isn't flash, as it has happened on websites without it.  I'd be interested to hear any solution.

---

