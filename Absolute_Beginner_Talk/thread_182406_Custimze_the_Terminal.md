---
title: "Custimze the Terminal"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by nalgene on 2006-05-26
Stupid question, is there a way to make my terminal more like the one lost

instead of having name@ubuntu$: to
something like

>:

is it possible, i know its stupid but i think it would be cool

thx..

---

### Post by uzi09 on 2006-05-26
the question is, "what ISN'T possible with linux??" ;)

yea it is, you'll have to learn a bit of it though. most of it can be done with messing around with your .bashrc file in your home folder.

you should be looking for the PS1 line, i know there are multiple ones, but lemme get you some links that'll explain that mess:

here's an example:
```

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;

```


EDIT: This seems like a good how-to, although i must admit -- i have't read throught it much :D
[http://linux-blog.org/index.php?/archives/84-BASH-Prompt-Fun.html](http://linux-blog.org/index.php?/archives/84-BASH-Prompt-Fun.html)

---

### Post by Sef on 2006-05-26
> Stupid question,

Not a stupid question.  Just one that you want answered.

> i know its stupid but i think it would be cool

No, it is not.  You want to learn how to do something.  That is never stupid.

---

### Post by cowley on 2006-05-26
[QUOTE=Sef]Not a stupid question.  Just one that you want answered.



No, it is not.  You want to learn how to do something.  That is never stupid.[/QUOTE]



this is what i think is really cool about the linux/ubuntu way of life - in microsoft forums i am sure there is not this type of confidence building or help available for newbees such as myself where u r not afraid to ask any questions to acheive and learn what u want. great!!

simon

---

### Post by kart3r on 2006-05-26
You don't have to be afraid, nobody knows everything, everyone helps everyone, because tomorrow it could be you helping another newbie.I recognize i'm newbie too but I keep learning and helping another people and most important asking for help too.TEAM SPIRIT heheheh lol

---

### Post by nalgene on 2006-05-26
Thanks it was really easy to change it.

---

