---
title: "how do i figure out what version of ubuntu I am running?"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by gatorbrit on 2006-01-04
I installed automatix and it tells me that 
"This is the breezy version of automatix, it won't work on hoary"
But I thought I had installed ubuntu 5.10 breezy.

How can I check my installation?

Thanks
Rich

---

### Post by meborc on 2006-01-04
that's a good question... i would do 
**sudo gedit /etc/apt/sources.list**
and see what is there... if you have hoary repositories (a lot of hoaries) then you probably have all the packages of hoary... if you have breezies... welll you know :p 

but it is the lazy way to to it

EDIT: also be sure to do
[B]sudo apt-get update
sudo apt-get upgrade[/B]
if you have a lot of breezies... that way you can be sure that you have all the packages needed... for uptodate **sources.list** for hoary and breezy check _[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)_ (*from aysiu's sig*)

---

### Post by carlosqueso on 2006-01-04
This command may help you: ```
uname -a
```.  Try posting the output of that (you can delete your computer name, that's fine) here.

---

### Post by gatorbrit on 2006-01-04
This is what I get - but actually I think I corrected the problem - at some point I had put in a hoary sources list - I updated it to breezy and automatix runs now.

Having said this - wouldn't it be nice if you could easily tell what you were running?

```


Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux
```

---

### Post by bluefrog on 2006-01-04
click on the question mark on your taskbar. you will see right away what you have.

james

---

### Post by nocturn on 2006-01-04
Or use lsb_release -a

This should work on most distros

---

### Post by carlosqueso on 2006-01-04
I knew there was an easier way...DOH!

---

### Post by steve.horsley on 2006-01-04
Or Alt-Ctl-F1.

---

### Post by meborc on 2006-01-05
> Or Alt-Ctl-F1
just in case you are wondering how to get back:
> Or Alt-Ctl-F7
you know... you can cause a lot of trouble by sending a new person to linux to the cli without telling them how to get back :rolleyes:

---

### Post by Suzan on 2006-01-05
Or

```
less /etc/issue
```

or

```
cat /etc/lsb-release
```

---

### Post by estel on 2006-01-05
Any more? ;)

---

### Post by arnieboy on 2006-01-05
is there any CLI based prog which tells us whether we are running Gnome or KDE?

---

### Post by benplaut on 2006-01-05
[QUOTE=arnieboy]is there any CLI based prog which tells us whether we are running Gnome or KDE?[/QUOTE]

grep the output of ps aux, for kde-session manager, and whatever else is included at startup

then, the people who have gnome panel, openbox, xfce desktop, and xfce apps - there's the problem :rolleyes:

---

### Post by chimera on 2006-01-05
[QUOTE=arnieboy]is there any CLI based prog which tells us whether we are running Gnome or KDE?[/QUOTE]


Send me a screenshot and I'll tell you;)

---

### Post by arnieboy on 2006-01-05
[QUOTE=chimera]Send me a screenshot and I'll tell you;)[/QUOTE]
smart arent u? :) too bad a bash script cannot see a screenshot when it tries to decide the same :)
anyone?

---

### Post by estel on 2006-01-05
You mean, tell you the WM that X is running atm?

---

### Post by arnieboy on 2006-01-05
[QUOTE=estel]You mean, tell you the WM that X is running atm?[/QUOTE]
the desktop environment, not the WM.
yeah but what if it were simply the WM, is there a generic prog telling us which WM is running?

---

