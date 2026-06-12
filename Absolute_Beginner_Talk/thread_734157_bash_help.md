---
title: "bash help"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by love2learn on 2008-03-24
Okay, i am so new I dont know where to get help files.

I figured that the terminal program is called bash ( i will be a terminal guy once I get going ) 

I need a few basics answered, I would have searched and read help files instead but I dont know the basic language.

How do I get help files? like on old dos it used to be /? or help /? or a list of bash command files. In other words how do I RTFM with most programs?

Man I sound like a true noob....

Please, i need answers in command line interface, i dont like the point and click method. Thanks!

---

### Post by handydan918 on 2008-03-24
The ```
man
``` command is your friend. 
Kinda...

For example, you can do ```
man cp
``` 
to read the man page on the cp (copy)command

You could also take a look [here]("http://en.wikipedia.org/wiki/Linux_commands"), to get a list of commands

---

### Post by love2learn on 2008-03-24
exactly what I needed Thanks! 

Favorited already

and you are saying 'man' is basically help files on '*'  such as 'man bash'

ahhh man =manuals im an idiot. I will go far with this.. thanks

---

### Post by brownknight on 2008-03-24
man man - manual about how to use manual
man cp - is manual about the copy command
man ls - manual about the list command
etc..

below is a blog about common bash commands
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

good luck

---

### Post by Dr Small on 2008-03-24
You can also read the man pages in Yelp (The graphical help application) by using:
```
yelp man:bash
```

Dr Small

---

### Post by drs305 on 2008-03-24
Here's another man tip. If something refers you to section or page X of a man entry, such as "see also crontab (5) " you view it with:
```
man 5 crontab
```

It took me a while to figure that out, but I'm more dense than most ](*,)]

---

