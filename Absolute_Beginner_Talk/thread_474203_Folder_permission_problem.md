---
title: "Folder permission problem"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Spensawr on 2007-06-14
Hey, I just installed Planeshift and the folder belongs to root. How do I go about changing it to maybe where either I am the owner or where it allows me to use it. I've tried the chown and chmod commands but I must be doing something wrong. 

Thanks :p

---

### Post by ryanVickers on 2007-06-14
For a beginner, I would not recommend using those, kinda complicated.  I don't really use them either.  I would say type in a terminal "gksudo nautilus", then in the proporties of the folder, change the owner and permissions!

---

### Post by Spensawr on 2007-06-14
> **ryanVickers said:**
> For a beginner, I would not recommend using those, kinda complicated.  I don't really use them either.  I would say type in a terminal "gksudo nautilus", then in the proporties of the folder, change the owner and permissions!

O crap thanks. Ive been looking for a way to get root permissions with a file browser. Thanks a ton. :p:p

---

### Post by ryanVickers on 2007-06-14
just a point of interest, normally, anything you run from the command line will then consume the terminal, and if closed, will close the app too.  The "gk" just backgrounds the task (I believe) so you can close it after!  
I don't know if it's a true background, or if just having the "ubuntu root dialoge thing" launch it allows for this, but either way... :)

---

### Post by Inxsible on 2007-06-14
Using gksudo nautilus is, IMHO, more dangerous than using chown and chmod. With the first you can mistakenly delete anything important from within nautilus. 

With the second option of using chown, you are acting only on that one particular folder ..so you are relatively safer.

What did you try ? Can you tell us why chown didn't work for you?

Syntax is 
```
sudo chown -R <your username>:<your group> <device mount path or folder name>
```

---

### Post by ryanVickers on 2007-06-14
AHA!  Glad someone knows how to use that thing! :p

Yeah, I suppose you would have to be careful, but some commands are a little dodgy as well! :p

---

### Post by Inxsible on 2007-06-14
> **ryanVickers said:**
> AHA!  Glad someone knows how to use that thing! :p

Yeah, I suppose you would have to be careful, but some commands are a little dodgy as well! :p

Yes commands can seem intimidating to new users especially ones who have always depended on Windows. But given time, one can really realize the potential of the command line. It is much more powerful than what a GUI can do.

an example can be the pipe command denoted by |
you can use this to concatenate- for lack of a better word -- multiple commands. I dont think any GUI will be able to do that or it will be extremely difficult even if a GUI does allow something to that effect.

---

### Post by ryanVickers on 2007-06-14
No question that they are more powerful and versatile, but it just the danger that while your away and forgot to lock your screen, your pet monkey will get loose and type random stuff untill he erases your hardrive :p

---

### Post by Inxsible on 2007-06-14
> **ryanVickers said:**
> No question that they are more powerful and versatile, but it just the danger that while your away and forgot to lock your screen,[COLOR="Red"] your pet monkey will get loose and type random stuff untill he erases your hardrive :p[/COLOR]

LMAO !!!! :D

The pet monkey must be real sharp with Linux commands ! 

HAHAHAH

---

### Post by ryanVickers on 2007-06-14
Don't laugh, I've seen penguins do it before in "Madacascar" :p

---

### Post by danceswithcats on 2007-06-16
Thanks to all here.  This is the first time I've searched for a solution in forums and I found my exact problem covered.  Remarkable.

---

