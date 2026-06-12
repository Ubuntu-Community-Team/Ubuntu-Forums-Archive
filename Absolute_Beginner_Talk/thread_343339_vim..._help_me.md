---
title: "vim... help me"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by programmer in linux on 2007-01-21
hello everybody,,,

            [CENTER][/CENTER]can any one learn me [SIZE="4"][COLOR="Red"]how to use vim[/COLOR][/SIZE], please

---

### Post by taurus on 2007-01-21
[http://freeengineer.org/learnUNIXin10minutes.html#Vi](http://freeengineer.org/learnUNIXin10minutes.html#Vi)

---

### Post by CroEragon on 2007-01-21
[img]http://www.justfuckinggoogleit.com/bart.gif[/img]
Couldnt resist!LOL
Anyway check [this]("http://www.apmaths.uwo.ca/~xli/vim/vim_tutorial.html") link. Also conssider using nano.

---

### Post by weresheep on 2007-01-21
Hello,

The first thing I would say is that you should be prepared for a long journey. VIM is an excellent editor and I find it hard to use other "normal" editors after getting used to it, but it does take a long time to get comfortable with it. Don't expect to read a couple of help pages and be am expert, cos you wont be :D 

I found the best way to really learn VIM was by forcing myself to use all the time and that forced me to search out and learn the specifics of what I needed (e.g. how to search text, how to find and replace, how to edit multiple files etc.). However, in order to be able to use VIM you need to have the basics mastered. You have to know about the various modes of VIM, how to move the cursor about, how to insert, append and replace text and that is where vimtutor comes in very handy.

'vimtutor' (just run 'vimtutor' at the command line) is the built in VIM tutorial and is well worth spending the 30 minutes or so it takes to go through it. I went through the tutorial a few times when I first started out with VIM.

There are other excellent editors out there so if you really can't get your mind around VIMs interface I wouldn't worry about it, but if you edit text for a living (e.g. are a programmer) then it is a worth while investment in your time.

-weresheep

---

### Post by programmer in linux on 2007-01-21
Looooool, nice pic CroEragon thx i forget google 

thx taurus

---

### Post by pistcivet on 2007-01-21
```
vimtutor
```

---

### Post by programmer in linux on 2007-01-21
sudo: vimtutor: command not found

---

### Post by taurus on 2007-01-21
Maybe you have to install the vim-full first.

```
sudo aptitude update
sudo aptitude install vim-full
vimtutor
```

---

### Post by peresko on 2007-01-21
yes vimtutor is nice,
but i find this [cheatsheet]("http://www.tuxfiles.org/linuxhelp/vimcheat.html") also very helpfull

---

### Post by Pobega on 2007-01-21
> **taurus said:**
> Maybe you have to install the vim-full first.

```
sudo aptitude update
sudo aptitude install vim-full
vimtutor
```

Actually vimtutor isn't dependant on the full package, but some vim features are. Don't run vimtutor as root, which I think is your problem.

---

### Post by programmer in linux on 2007-01-21
thx 4 all

---

