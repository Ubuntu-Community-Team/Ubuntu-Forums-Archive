---
title: "Aptitude"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by marx2k on 2006-10-27
When in Aptitude, I try to select a new package for download by hitting '+'

I have the program set to move to the next line when I select a package.

However, I hit '+' and it moves to the next line, but the status of the package (gvim) does not change.  It stays 'v' with no i or I next to it to show that its marked for download! Does anyone else have this problem?

---

### Post by marx2k on 2006-10-27
I read through the '?' help and hitting M or m doesnt work either :(

---

### Post by jd65pl on 2006-10-27
why dont you try:

```
sudo aptitude install gvim
```

---

### Post by marx2k on 2006-10-27
Solved my own problem yet again :) What I was looking at was the parent node of the program.  I SHOULD have hit 'v' to look at individual install packages of the base program and THEN selected one of those!

---

### Post by jd65pl on 2006-10-27
If you knew the name of the package you could have just used the command. The gui for aptitude is a little clunky IMO.

---

### Post by marx2k on 2006-10-30
Gettin around aptitude without using the mouse in a gterm window is clunky.  Itd be nice if menus were accessible via ALT+letter

I agree that 'sudo aptitude install 'packagename'' is easy as heck

Now, whats the difference between doing it in Aptitude and doing it in Synaptic?

---

### Post by Anonii on 2006-10-30
> **marx2k said:**
> Gettin around aptitude without using the mouse in a gterm window is clunky.  Itd be nice if menus were accessible via ALT+letter

I agree that 'sudo aptitude install 'packagename'' is easy as heck

Now, whats the difference between doing it in Aptitude and doing it in Synaptic?
Synaptic is like doing an apt-get. Also Synaptic is in GUI. aptitude and apt-get is in the CLI, which is trully superior.

So basicaly.

aptitude, is better than apt-get for dependency reasons. Synaptic uses a GUI, which is easier to use, but its slow, resource-depending and boring, also it uses apt-get which is worse than aptitude.

I'd suggest you use aptitude. :]

---

### Post by ReaderRat on 2006-10-30
[**aptitude vs. apt-get**](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by Najand on 2006-10-30
Well, I think you cannot just say apt-get is worse than aptitude. apt-get is just simple and let you choose the packages you don't need yourself. 

Sometimes the so-called "superior" aptitute is too smart and install unnecessary packages or remove some necessary packages (for example, last time when I was trying to remove scim, it starts  to install mozilla-thunderbird. Still I cannot understand what is  the relationship between scim which is a package manager and mozilla-thunderbird which is a mail cilent). 

It is just a matter of taste and your need at the time of dealing with packages to use apt-get or aptitude. So, suggestion of using one then the other is somehow unnecessary.

---

### Post by marx2k on 2006-10-30
A-ha! See, I thought Synaptic used Aptitude.  I was unaware that it uses apt-get!  Now that I know, I will use Aptitude.

Sorry to be lame, but is there a front-end gui for Aptitude by any chance?

---

### Post by gperk on 2007-10-29
In aptitude you can access the menus with Ctrl+t. 
Seems so often that many things in Linux are just different and cryptic to make it difficult and often impossible for a beginner to use. 

I have an install CD (Edubuntu 7.10) which is mostly OK but one part is corrupted. I would like to be able to download software from the Internet servers but it always asks for the CD. Anyone know how I can download directly?
Thanks,
Greg

---

### Post by Maestro23 on 2007-10-29
> **gperk said:**
> In aptitude you can access the menus with Ctrl+t. 
Seems so often that many things in Linux are just different and cryptic to make it difficult and often impossible for a beginner to use. 

I have an install CD (Edubuntu 7.10) which is mostly OK but one part is corrupted. I would like to be able to download software from the Internet servers but it always asks for the CD. Anyone know how I can download directly?
Thanks,
Greg

See your thread.

---

