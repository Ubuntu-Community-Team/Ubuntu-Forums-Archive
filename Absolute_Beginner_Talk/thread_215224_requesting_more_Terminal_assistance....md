---
title: "requesting more Terminal assistance..."
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by olivesmarch4th on 2006-07-13
I'd like to know how to launch programs and terminate them through the BASH, but I can't find this information anywhere.  I had OpenOffice freeze on me and the only way I could close the program was crtl alt backspace... but deep down I know I could have probably done it much less intrusively using the Terminal.  What are some good tips for someone who wants to learn to do as much as humanly possible through the Terminal... say web browsing, opening and writing Office documents, etc? Are there any links on this? 

I also have another question.  Is there a way I can shorten my username so I don't have to type so much every time I want to specify my user directory?  Right now it's "olivesmarch4th."  I'm thinking "om4" would make things a lot easier.  Let me know.

Thanks!

Olives,
Christy

---

### Post by shanepardue on 2006-07-13
xkill is the command to "kill" tasks..it turns your mouse cursor into a skull and bones and anything you click is dead. right-clicking will end xkill's powers.

---

### Post by Brunellus on 2006-07-13
your user directory is easy.  if you want to go home, type

```
~/
```

that's short for /home/username/

easiest way to figure out what's taking up all the processor time is to execute 

```
top
```

which will give you a list of programs and how much time/resources they are using.  make a note of the name of the program you want to kill, hit CTRL-C (to quit top)  and then kill that sucker:

```
kill processname
```

if the name is wrong, but you know the process ID, just substitute the process ID number for the name.

if there are multiple instances, use

```
killall
```

---

### Post by digby on 2006-07-13
You can find a good intro [here]("http://linux.org.mt/article/terminal").  

To answer one specific question, if you have an unresponsive program, you can run xkill in a terminal and then click the offending window.

---

### Post by Sonofmoog on 2006-07-13
> **olivesmarch4th said:**
> 

I also have another question.  Is there a way I can shorten my username so I don't have to type so much every time I want to specify my user directory?  Right now it's "olivesmarch4th."  I'm thinking "om4" would make things a lot easier. 

Typing cd without arguments and pressing enter will take you $HOME

The earlier suggestion about using xkill to kill unresponsive programs is a good one.  It's quick, efficient, and easy ..

---

### Post by Skia_42 on 2006-07-13
Or you can just kill the process by going to "System Monitor"
(System >> Administration >> System Monitor)
I know it's not in the terminal but it works. 
(You need to kiil the process though, not just stop it.)

---

### Post by olivesmarch4th on 2006-07-13
Thanks guys!

Is it possible to start an application through the Terminal?

---

### Post by digby on 2006-07-13
You can start any application through the terminal - If the application is in your path (a list of directories the shell looks through for executable files), all you have to do is type the name of the executable file (e.g. fortune).  If it's not in your path, you'll have to give that as well (e.g. /usr/games/fortune).

---

