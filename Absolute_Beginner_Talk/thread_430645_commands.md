---
title: "commands"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by shadowfreak on 2007-05-02
ive tried searching and i couldnt come up with anything, so i was wondering if some one could provide me with just some basic custimization commands or something that i could enter into the terminal. 

sorry if my request is a little vague im still a noob to all of this...:mad: :roll: :frown:

---

### Post by taurus on 2007-05-02
What do you have in mind?

---

### Post by Dcox on 2007-05-02
ps -> see the processes ... mostly used with option -aux, so ps -aux
ls -> list the files ... mostly used with option -al, so ls -al
reboot -> obvious :)
vi -> the vi editor!
nano -> the nano editor!
touch -> create an empty file : eg touch test.txt
top -> show active processes 

and so on :) Enough to get you interested !

---

### Post by shadowfreak on 2007-05-02
uh... file organization, search commands, installation commands, stuff like that, and pretty much anything that would make ubuntu look cool or how to setup some quick execution commands like setting up a short cut to open songbird, and firefox at the same time, stuff like that basically

and thanks DCox

---

### Post by Yazaaab on 2007-05-02
I would like to know networking commands, I am curious on how to find what DNS servers I am using and what my default route is.  Sorry if I am taking the thread in the wrong direction.

Thanks

---

### Post by overdrank on 2007-05-02
> **shadowfreak said:**
> uh... file organization, search commands, installation commands, stuff like that, and pretty much anything that would make ubuntu look cool or how to setup some quick execution commands like setting up a short cut to open songbird, and firefox at the same time, stuff like that basically

and thanks DCox

Hi and hope this link will help. Good Luck !
[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

---

### Post by shadowfreak on 2007-05-03
> **Yazaaab said:**
> I would like to know networking commands, I am curious on how to find what DNS servers I am using and what my default route is.  Sorry if I am taking the thread in the wrong direction.

Thanks

nope its still in the spirit of learning commands for linux and if this thread helps someone else also im down with that

---

### Post by Bachstelze on 2007-05-03
The DNS servers used by the system are stored in /etc/resolv.conf, so :

```
cat /etc/resolv.conf
```

The cat command basically reads from something (here, the /etc/resolv.conf file) and writes to standard output (your terminal).

---

