---
title: "how do i undo this command"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by raymond1234 on 2007-06-01
I wanted to play chess in 3d so I type this into my terminal

 sudo dpkg -i python-gtkglext1_1.1.0-2feisty_i386.deb

and Installed the python-gtkglex but now I cant watch .flv or even .mpeg files

all I get is a black screen when I swith to full screen


so I do I undo or uni stall python

---

### Post by wieman01 on 2007-06-01
> sudo dpkg [COLOR="Red"]-r[/COLOR] python-gtkglext1_1.1.0-2feisty_i386.deb
...or...
> sudo dpkg [COLOR="Red"]-r[/COLOR] python-gtkglext1_1.1.0-2feisty_i386
...I believe.

_**EDIT:**_
Useful help function:
> sudo dpkg --help

---

### Post by FredSambo on 2007-06-01
Do:

```
sudo dpkg --purge python-gtkglext1_1.1.0-2feisty_i386.deb
```

or if you want to remove it while keeping the configuration files incase you need them later:

```
sudo dpkg -r python-gtkglext1_1.1.0-2feisty_i386.deb
```

Good luck!

---

### Post by Rui Pais on 2007-06-01
or, since you installed a deb packages, you can simply use apt-get remove

---

### Post by FredSambo on 2007-06-01
Like Wieman, I'm not sure if you have to put the .deb on the end or not.

---

### Post by Rui Pais on 2007-06-01
> **FredSambo said:**
> Like Wieman, I'm not sure if you have to put the .deb on the end or not.

no, it's just the app name, no .deb or version number. 
Best is type only a few initial letters and use tab completion to get the rest correctly. Or, as i said, use apt-get/aptitude like usual.

---

### Post by RomeReactor on 2007-06-01
Hi. If I'm not mistaken, .deb files installed with dpkg appear in Synaptic, so you can use it to uninstall it.

---

### Post by FredSambo on 2007-06-01
> Best is type only a few initial letters and use tab completion to get the rest correctly.

w00t!

---

### Post by Rui Pais on 2007-06-01
> **FredSambo said:**
> w00t!

[biblic voice]
never understimate the powers of tab completion
[/biblic voice]

---

### Post by wieman01 on 2007-06-01
Guess it would be best if someone test it... But I don't want to remove anything so... ;-) Volunteers!

---

### Post by Rui Pais on 2007-06-01
> **wieman01 said:**
> Guess it would be best if someone test it... But I don't want to remove anything so... ;-) Volunteers!

sorry? 
don't get it, test what?

---

### Post by wieman01 on 2007-06-01
> **Rui Pais said:**
> sorry? 
don't get it, test what?
Removing software from an running system... Silly joke, was trying to be funny. ;-) I know you have already pointed out the solution.

---

### Post by Rui Pais on 2007-06-01
> **wieman01 said:**
> Removing software from an running system... Silly joke, was trying to be funny. ;-) 

:oops: sorry, i miss it :oops: 
(me dumb :lol:)

---

### Post by wieman01 on 2007-06-01
> **Rui Pais said:**
> :oops: sorry, i miss it :oops: 
(me dumb :lol:)
No worries, was a bad joke anyway... :D

---

### Post by raymond1234 on 2007-06-01
**this was the command I used**

You will all be pleased to know that now I can watch my .flv and .mpg files again after I uninstalled that last program I wonder it screwed up the play back of those video files in the first place

ray@ray-laptop:~$ sudo dpkg -r python-gtkglext1
(Reading database ... 127493 files and directories currently installed.)
Removing python-gtkglext1 ...



J used auto complete to find the right name of the package installed. thats hitting the tab key

---

