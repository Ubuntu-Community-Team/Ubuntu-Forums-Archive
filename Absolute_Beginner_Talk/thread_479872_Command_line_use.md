---
title: "Command line use"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by davidma777 on 2007-06-20
How can you retrieve a previous command one character at a time? Under the DOS command line, you can press F1 multiple times to get to the point where you made a typo,  type the correct character, and then press F3 to fill in the rest of the line. I've found Ctrl-p  returns the whole command line (equivalent to F3 by itself) but haven't yet found a way to edit the line. What is the Linux way to do this?

---

### Post by MichaelLerch on 2007-06-20
Have you tried the arrow keys?

---

### Post by wormser on 2007-06-20
I am not sure Linux can do that.  (to my knowledge)   The up arrow key will scroll through your commands.  The tab key is a great feature.  Start typing you command and press tab.  It will auto complete or give you the options available.  It saves a lot of typing and typos.  You can also use the **history/B] command.  I recommend using it with [B]grep**.  

```
history | grep keyword
```

Then you can put an ! before the number of the wanted command and it will run.

---

### Post by MichaelLerch on 2007-06-20
What I've been able to do while in the terminal is that if I made an error in a command and I have yet to issue it [pressing enter], I use the left and right arrow keys to get to my typo and fix it.  Are we talking about the same thing or no?

---

### Post by davidma777 on 2007-06-20
> **wormser said:**
> ... The up arrow key will scroll through your commands.  The tab key is a great feature.  Start typing you command and press tab.  It will auto complete or give you the options available.  It saves a lot of typing and typos.  You can also use the **history/B] command.  I recommend using it with [B]grep**.  

```
history | grep keyword
```

Then you can put an ! before the number of the wanted command and it will run.

MichaelLerch  	What I've been able to do while in the terminal is that if I made an error in a command and I have yet to issue it [pressing enter], I use the left and right arrow keys to get to my typo and fix it. Are we talking about the same thing or no?


Yes we are talking about the same thing.  The combination of up arrow to retrieve the command and then left and right arrows to get to the character to correct allows command line retrieving and editing. MichaelLearch, it works after you issue the command as well as before. The history | grep idea is powerful but for immediate editing the arrow keys do it.
Dave A.

---

