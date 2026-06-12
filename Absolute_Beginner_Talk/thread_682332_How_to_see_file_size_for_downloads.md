---
title: "How to see file size for downloads?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by coyotech on 2008-01-29
I'm extremely new to Linux of any kind, and am learning my way around and setting up my laptop. The problem is that my home ISP puts a strict download limit on me. When I try to install a program or update with apt-get, I have no idea what I'm biting off download-wise, and keep getting punished for over downloading! Is there a way to configure apt-get or some other download manager so that I can see the size of the files before downloading?
:(

---

### Post by JoshuaRL on 2008-01-29
Hmm.  I think that if you use apt from the terminal it will say how much disk space it will use.  That would be one indication.

---

### Post by Nythain on 2008-01-29
get familiar with apt-get and aptitude (wichever you prefer, both are on par with each other now)
sudo aptitude show <package name> will show tons of info about the chosen package.
Im pretty sure this info is also available in synaptic, but i dont use gui proggies much so i couldnt tell ya where to look or when it mentions it

---

### Post by mlissner on 2008-01-29
That's true, however, I think it may sometimes just go ahead and install things. The solution I found was to go to packages.ubuntu.com and look up the package there. 

The only trick will be to make sure you remember to add in dependencies. You might find the -s flag useful too if you want to "simulate" installation of files with apt. For example: ```
sudo apt-get -s install openoffice.org
```
That would do nothing to your system, and would just do a dry run. Actually, I think an alternative method to -s is --dry-run.

---

### Post by iansane on 2008-01-29
Your not worried about drive space right? Just bandwidth usage? in synaptic highlight the package by clicking on it and then at the top click the properties box. It tells the size

---

### Post by jaytek13 on 2008-01-29
Here is a page listing some various bandwidth monitoring tools:

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html)

From looking over it it seems only a couple offer a total usage while a lot of them are just for monitoring real time. But, it looks like ibmonitor might serve the purpose you are looking for.

---

### Post by coyotech on 2008-01-30
Thanks to everyone for your help! All the suggestions were helpful. Moving over from windows I naturally like the right click and see properties one the best :-)

I like the Linux. It's not too hard to get used to, especially the desktop version. Once I get comfortable with how things work in the beginner version, I'll move on more to the terminal. I have to. I started taking advanced computer science courses after years of doing nothing but administering small MS domains and doing web scripting. I can't even get my homework done without getting Linux working and figuring out how to write and run C and Prolog in Linux.

Anybody know why it Geany can't find the libraries for a c program? When the book's example didn't work I searched for the file and put in the full path, and it still can't find the library...I should probably put this as  separate post somewhere...

---

### Post by jaytek13 on 2008-01-30
> **coyotech said:**
> 

Anybody know why it Geany can't find the libraries for a c program? When the book's example didn't work I searched for the file and put in the full path, and it still can't find the library...I should probably put this as  separate post somewhere...

Well, first, type 

```

sudo apt-get install build-essential

```

into a terminal

After that, you should be able to compile c programs in a terminal using 

```

gcc filename.c - filename

```

and then to run you would just do ./filename

---

### Post by mlissner on 2008-01-30
Or, if you rather, do ```
sudo apt-get install gcc
```

That will get you the c compiler, and will save you some bandwidth over build -essential.

I should mention that you can do this the GUI way as well, if that is easier/more comfortable for you...

---

### Post by Pelham123 on 2008-01-30
You can configure synaptic to add 'download size' and 'installed size' in the main package list window - instead of right clicking on each individual package. Cant quite remember how, think it comes under one of the top menu choices 'view', 'edit' etc...

---

