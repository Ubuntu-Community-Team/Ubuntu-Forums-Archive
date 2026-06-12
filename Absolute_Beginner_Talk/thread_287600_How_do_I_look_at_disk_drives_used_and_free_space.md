---
title: "How do I look at disk drives used and free space"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-10-29
I use to look at disk space by going to Systems>Admin> Disks.

I dont see that in Edgy where did it go ?

---

### Post by taurus on 2006-10-29
Open a terminal, Applications -> Accessories -> Terminal, and type

```
df -h
```

---

### Post by kent41 on 2006-10-29
> **taurus said:**
> Open a terminal, Applications -> Accessories -> Terminal, and type

```
df -h
```

Thanks that works but did they remove that function ?

---

### Post by taurus on 2006-10-29
I am not in front of my Edgy right now (it's in the office and I am at home with Dapper) so can't tell you until I come in on Monday to have a look at it.  In the meantime, use the "df -h" from the terminal tnen.

---

### Post by kent41 on 2006-10-29
> **taurus said:**
> I am not in front of my Edgy right now (it's in the office and I am at home with Dapper) so can't tell you until I come in on Monday to have a look at it.  In the meantime, use the "df -h" from the terminal tnen.

Thanks - I thought I look at the disks when I first installed Edgy and it was there but maybe I am mistaken. It will be the first time this year but there is a first time for everything.

Thanks again I can wait until monday/

PS. Other strange things happen with edgy like firefox just goes away then later it ask me if I want to restore it. wow

---

### Post by H.E. Pennypacker on 2006-10-29
I noticed the same thing with Edgy.  Disks seems to be gone, but a good thing is that Boabab is now installed by default.  You'll find it under Accessories as Disk Usage Analyzer.

As for the Firefox problem, I am sure developers are already aware of it.  Do a search on the issue, and you'll likely find lots of threads.  Don't create a thread of your own on the Firefox issue.

---

### Post by MoebusNet on 2006-10-29
I don't see that option in Kubuntu Edgy. No "Accessories" listed in KMenu.

---

### Post by SoloSalsa on 2006-10-29
Will someone explain that line to me?  I can tell that df is the program, but what does it stand for?  And what is the choice, -h?
Thanks!

---

### Post by po0f on 2006-10-29
SoloSalsa,

df stands for **d**isk **f**reespace (I'm guessing), and the -h argument tells it to print its output in "human-readable" form.  It defaults to outputting sizes in bytes, IIRC.  Try running `df -h` and then just `df` and compare the output.

---

### Post by Zahrber on 2006-10-29
Do a man df and it will give you info on the df command and also lsit the arguments or parameters for the command and how to use them and what they do. That way in the future you can learn commands on your own

---

### Post by Coelocanth on 2006-10-29
Yes, it stands for 'disk free'.

-h is human readable format, using powers of 1024 for the space sizes. If you use the -H command, it gives the sizes in powers of 1000.

Another useful option is -T, which tells you the filesystem type.

---

### Post by jd65pl on 2006-10-29
If you prefer a graphical user interface then why not try

SYSTEM > ADMIN > SYSTEM MONITOR 

then select the file systems tab

---

### Post by H.E. Pennypacker on 2006-10-29
> **MoebusNet said:**
> I don't see that option in Kubuntu Edgy. No "Accessories" listed in KMenu.

You probably won't find it under KDE, but you will with Gnome. :)  Gnome rocks.

Check out Boabab.  Download and install it.  Should work on KDE.

---

