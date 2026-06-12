---
title: "What are the adverse side effects of using gksudo"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-06-18
I was reading about some of the adverse side effects of using sudo all of the time.  What are some of the adverse side effects of using gksudo all of the time.  I suffer from severe short term memory and I forget to distinguish between the 2 and use sudo when I shouldn't.  A simple message telling me to use sudo would not for me be an adverse side effect of gksudo.

---

### Post by dannyboy79 on 2007-06-18
this has been asked a million times. Here you go, bookmark for the next time you would like to read about it due to your short term memory loss:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by dreadlord_chris on 2007-06-18
> **ICUR2Ys said:**
> I was reading about some of the adverse side effects of using sudo all of the time.  What are some of the adverse side effects of using gksudo all of the time.  I suffer from severe short term memory and I forget to distinguish between the 2 and use sudo when I shouldn't.  A simple message telling me to use sudo would not for me be an adverse side effect of gksudo.

uhh... let's see...

sudo: for use when a command requires administrative privileges.
i.e.
```

chris@HAL421:~$ mount -a
mount: only root can do that
chris@HAL421:~$

```
whereas, with sudo:
```

chris@HAL421:~$ sudo mount -a
Password:
chris@HAL421:~$ 

```
the command completed sucessfully.

Now, if you're wanting to launch a *graphical* program (one with a GUI) then you would use gksudo.

The only difference between the 2 is gksudo is designed to handle GUI apps.

The same warnings that apply to sudo apply to gksudo - if you don't need admin privilages to run something, don't use (gk)sudo

---

### Post by ICUR2Ys on 2007-06-18
Nope.  I read that it tells me about a bug that looks like an error, and about the adverse side effects of using sudo all of the time.  Some of those side effects can be nasty.  I am not asking about the difference between them.  I am asking about any adverse side effects to gksudo.

---

### Post by jputman01 on 2007-06-18
adverse side effect = moving, deleting, altering something you shouldnt by accident

---

### Post by ICUR2Ys on 2007-06-18
jputman01, are you saying that if I use gksudo for the command line it would sometimes move, delete, or alter something that the sudo command would not?

---

### Post by dannyboy79 on 2007-06-18
> **ICUR2Ys said:**
> Nope.  I read that it tells me about a bug that looks like an error, and about the adverse side effects of using sudo all of the time.  Some of those side effects can be nasty.  I am not asking about the difference between them.  I am asking about any adverse side effects to gksudo.

read the link and you'll get your adverse effects. It deals with sudo launching with root privalages but using the user's config file.If that's not what you're talking about then obviously you know more about it and you should be telling us.

---

### Post by dannyboy79 on 2007-06-18
> **ICUR2Ys said:**
> jputman01, are you saying that if I use gksudo for the command line it would sometimes move, delete, or alter something that the sudo command would not?

I think I smell a TROLL????

Don't feed the trolls.

---

### Post by lazyart on 2007-06-18
>   I suffer from severe short term memory and I forget to distinguish between the 2 and use sudo when I shouldn't. 

Use sudo for command line programs.  Use gksudo for graphical programs (ones that open a window). 

> What are some of the adverse side effects of using gksudo all of the time.
The side effects are the same as using sudo all the time.  Just one is used for command like and one for graphical programs (see above).

---

### Post by ICUR2Ys on 2007-06-18
dannyboy79 you are unreal calling names for a simple question.  I will just experiment if anything bad happens on my own.  This thread is dead for me.

---

### Post by wormser on 2007-06-18
> **dannyboy79 said:**
> [COLOR="Red"]this has been asked a million times.[/COLOR] Here you go, bookmark for the next time you would like to [COLOR="Red"]read about it due to your short term memory loss:[/COLOR]
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> **dannyboy79 said:**
> read the link and you'll get your adverse effects. It deals with sudo launching with root privalages but using the user's config file.If that's not what you're talking about [COLOR="Red"]then obviously you know more about it and you should be telling us[/COLOR].

> **dannyboy79 said:**
> I think I smell a TROLL????

Don't feed the trolls.

Dannyboy79, to use your word, obviously you did not read the [Code of Conduct]("http://www.ubuntu.com/community/conduct").

---

### Post by jputman01 on 2007-06-18
> **ICUR2Ys said:**
> dannyboy79 you are unreal calling names for a simple question.  I will just experiment if anything bad happens on my own.  This thread is dead for me.

im not sure what the troll thing is supposed to mean, but its pretty much like someone said after me. sudo is for command line and gksudo is graphical the draw back are pretty much the same. what i meant by accidentally moving, deleting, altering is like this

if i type in a terminal "gksudo nautilus" it will launch nautilus with root permissions, i can then browse my whole system graphically with root permission. say i wanted to delete a file and i clicked on it pushed delete and then realized oops wrong file, well now its gone (provided its not in the recycle bin)

all i am saying is running with root permissions at all times, whether in terminal or gui, is asking for trouble in my opinion, you may accidentally do something that messes up your entire system

this is all just my opinion however

---

### Post by Atomic Dog on 2007-06-18
> **jputman01 said:**
> im not sure what the troll thing is supposed to mean, but its pretty much like someone said after me. sudo is for command line and gksudo is graphical the draw back are pretty much the same. what i meant by accidentally moving, deleting, altering is like this

if i type in a terminal "gksudo nautilus" it will launch nautilus with root permissions, i can then browse my whole system graphically with root permission. say i wanted to delete a file and i clicked on it pushed delete and then realized oops wrong file, well now its gone (provided its not in the recycle bin)

all i am saying is running with root permissions at all times, whether in terminal or gui, is asking for trouble in my opinion, you may accidentally do something that messes up your entire system

this is all just my opinion however

Yep.  That makes sense.  I used to run nautilus as root (gksudo Nautilus)often.  After making a few bone headded mistakes I stopped unless it is absolutely necessary.  

So yea:  SUDO for command line/terminal stuff (sudo fdisk -?)
GKSUDO for GUI apps being launched from a command line.  (ie. gksudo nautilus)

---

### Post by Rui Pais on 2007-06-18
I think most people here don't note the deep irony of saying that for security one should run gksudo nautilus.

The dangerous is to run nautilus with sudo powers. Using gksudo or sudo is quite irrelevant, as soon as, by distraction or accident, you delete all your /usr or something sweet like that...

---

### Post by Enverex on 2007-06-20
Using Sudo for basic things is bad because any apps run with it basically have full control to do anything to the system. You can also end up screwing up your users permissions meaning they are unable to do things anymore (due to root owning their files and thus not being able to access them as a user). i.e. if you run Wine with sudo for the first time, you can't ever run Wine as that user because it's created your virtual C: drive as root and every file in there is now roots, not yours.

---

