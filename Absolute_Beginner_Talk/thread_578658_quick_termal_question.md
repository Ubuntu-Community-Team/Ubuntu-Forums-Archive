---
title: "quick termal question"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by spyder0080 on 2007-10-17
hello all, 

i have a question regarding running programs from the terminal:

if you run a program with the following form

program &

(e.g rhythmbox &)

and you close the terminal, is the program that you ran supposed to close too? because that is what is happening to me.

i just upgraded from 7.04 to the 7.10 candidate release yesterday. i'm not sure if the same thing happened in the previous version but this is what is happening now

thanks!

---

### Post by ahaslam on 2007-10-17
No, it should not close. If you just issued 'rythembox' then it would.

---

### Post by spyder0080 on 2007-10-17
hmmm, that is strange

any way I could fix this error?

---

### Post by Dr Small on 2007-10-17
If you want to run a program through the terminal, and have the terminal close after you launch an applicatio, try this:
```
*application_name* && exit
```

Dr Small

---

### Post by mlind on 2007-10-17
yes it should close, unless you start the process using **nohup** (see *man nohup* for details).

for example
```

nohup rhythmbox

```

You can also start programs in gnome by doing ALT+F2 and then giving then program to 'run dialog'.
This way program will stay open until you log out of your xserver sesssion.


not sure if nautilus uses nohup, but it forks itself to background, so closing a terminal where you started it doesn't kill nautilus.

---

### Post by Bothered on 2007-10-17
Thanks mlind, I never knew that :-)

Should that also be used for ssh logins? i.e. if you login to a machine via ssh and run a program "[command] &" and then logout, with the program be stopeed?

---

### Post by notwen on 2007-10-17
Try it w/o the ' ' space.

```
rhythmbox&
```

---

### Post by Dr Small on 2007-10-17
That works too :p

---

### Post by mlind on 2007-10-17
> **Bothered said:**
> Thanks mlind, I never knew that :-)

Should that also be used for ssh logins? i.e. if you login to a machine via ssh and run a program "[command] &" and then logout, with the program be stopeed?


If the program you're executing is not a daemon and it's running inside a shell and you exit the shell, so I guess it should terminate.

I suggest you get familiar with **screen** which is very good for remote ssh sessions. You can detach the screen, then maybe switch a computer, then re-attach the screen back and you're back in same ssh session with all the same applications running.

---

### Post by spyder0080 on 2007-10-17
> **mlind said:**
> yes it should close, unless you start the process using **nohup** (see *man nohup* for details).

for example
```

nohup rhythmbox

```

You can also start programs in gnome by doing ALT+F2 and then giving then program to 'run dialog'.
This way program will stay open until you log out of your xserver sesssion.


not sure if nautilus uses nohup, but it forks itself to background, so closing a terminal where you started it doesn't kill nautilus.
thanks, nohup works (for rhythmbox at least)

unfortunately, taking out the space (rhythmbox&) doesn't work :(

---

### Post by 5-HT on 2007-10-17
> **spyder0080 said:**
> 
is the program that you ran supposed to close too?
nope. What's probably going on is that you're forcefully closing the terminal by clicking on the little x in the window boarder. Try  gracefully closing the terminal by issuing 'exit'.
cheers,

---

