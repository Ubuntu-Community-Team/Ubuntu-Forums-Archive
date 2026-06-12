---
title: "followed direction but get error message"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by broekskw on 2008-01-02
still new to all this again,trying to install new themes, so i followed this guide
[http://www.arsgeek.com/?p=2754](http://www.arsgeek.com/?p=2754)
after everything was done as per guide tried to update with non gpl'd theme but keep getting this error message
so what am i missing if any??
also after this is working do i just select the theme that i want and it will install????

thanks

---

### Post by ~LoKe on 2008-01-02
Did you run the command at the bottom that it told you to?

```
svn ls https://svn.generation.no/emerald-themes
```

---

### Post by broekskw on 2008-01-02
sure thing but just to be sure i ran them again but got the same error message:confused:

---

### Post by ~LoKe on 2008-01-02
A solution [here](http://www.mepislovers.org/forums/showthread.php?t=7419)?

Seems like a [common](http://www.google.ca/search?hl=en&q=emerald%2C+error+calling+tar&btnG=Google+Search&meta=) problem.

---

### Post by broekskw on 2008-01-02
great LoKe but how do you make a new folder as per instructions 

Hi, I had the same problem. So my workaround was to create a folder(s) here; /home/your name/.emerald/themes/
name it the theme, and open the tar's and drop the contents in this folder. Do this for every theme. Then opening emerald theme manager, you will see the new theme & can select it. You may need to tell konqueror to show hidden files in view. good luck
Alan

still very new to this ubuntu but trying to understand as fast as possible:popcorn:

thanks

---

### Post by ~LoKe on 2008-01-02
In the terminal, type this:
```
mkdir ~/.emerald && mkdir ~/.emerald/themes/
```

---

### Post by broekskw on 2008-01-02
thanks again, this command said that it already exists

broekskw@broekskw-desktop:~$ mkdir ~/.emerald && mkdir ~/.emerald/themes/
mkdir: cannot create directory `/home/broekskw/.emerald': File exists

so all i do know is download themes to this folder?? correct

:):popcorn:

---

### Post by ~LoKe on 2008-01-02
> **broekskw said:**
> so all i do know is download themes to this folder?? correct

:):popcorn:
Yes!  You need to download the packages for the themes (usually archives with that .tar or .tar.gz) then extract them into the ~/.emerald/themes folder!

---

### Post by broekskw on 2008-01-02
thanks ~LoKe got it going, was expecting the themes to change everything on my desktop,but i found out that you have control over everything separately:popcorn:
so going to check it out 

again thanks for all your help:lolflag:

---

### Post by ~LoKe on 2008-01-02
You're welcome. :)

Emerald changes the title bars and window borders only.  The rest is controlled by your GTK theme.

---

