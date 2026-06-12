---
title: "/bin and Terminal Questions"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by StRiFe10101 on 2007-07-12
My First Post ... Rock On!.  I installed Ubunut 2-3 weeks ago and already quesions! :(

3 Quick questions.  I have been reading on the forum about installing applications and running them afterwards.  Some have been having problems with running/finding programs after they are installed.  Now i have read some about the ubuntu file structure, and to my understanding, "basically" most all apps are installed in to the /bin directory (if i'm wrong please correct me). 

1. Is there anyway to specify the initial installation path when using either sudo apt-get install appname or synaptic or is it always installed into the /bin directory? (Please expound as much as neccessary ;))

Secondly, People have been stating that they cannot find a program after it is installed to execute it and experienced users post for them to simply type the name of the app (.exe equivilant) in the terminal (or so that is what i gather from reading it.) If this is true how does linux search for the app if by default the terminal wd, when opened, is the /home directory. (please correct me if i'm wrong. i think that is what i understood from what i read) 

Lastly, what is the actually equivilant to a windows .exe file?
It's a little confusing to know which file to execute after installing a program and changing to the 
directory which is was installed in. Thank you.

---

### Post by iver2435 on 2007-07-12
In Linux, just as in Windows, there is a PATH environment variable that the system uses to look for a program when you use a relative path.  If you sit down at a Windows machine and click "Start" -> "Run" and type "notepad", how does it know where notepad is?  It uses the PATH environment variable and searches each directory sequentially until it either finds a match or gives up.  The behavior is exactly the same in Linux.

To see your current path in Linux type:

```
echo $PATH
```

There is no (to my knowledge) .exe equilvalent under Linux.  ANY file can be marked as executable.  This doesn't mean that executing every file will DO something, but it's possible.

Most of the time, package designers make it easy on the end user by making the command to run the program the same as the name of the package.  This is not ALWAYS the case, but I always try that first, and then if it doesn't work I go on the hunt for the file to execute.

---

### Post by tcpip4lyfe on 2007-07-12
> 1. Is there anyway to specify the initial installation path when using either sudo apt-get install appname or synaptic or is it always installed into the /bin directory?

Yes but why would you want to do this? It's best to leave them default to avoid conflicts. If you want to see what directory things are installing into try:

```

sudo apt-get install locate
sudo updatedb
locate [I]program
[/I]

```

> Secondly, People have been stating that they cannot find a program after it is installed to execute it and experienced users post for them to simply type the name of the app (.exe equivilant) in the terminal (or so that is what i gather from reading it.) If this is true how does linux search for the app if by default the terminal wd, when opened, is the /home directory. (please correct me if i'm wrong. i think that is what i understood from what i read)


If you go to terminal and type:
```
export | grep PATH
```

You will see all the places you are looking for programs in.  Example k3b is a cd burning program and when I type k3b it searches in the following directories for that program. 

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

k3b is located in /usr/bin so I can execute k3b from any directory.

> Lastly, what is the actually equivalent to a windows .exe file?
It's a little confusing to know which file to execute after installing a program and changing to the
directory which is was installed in. Thank you.]

If you go to the directory you want to execute the program from in terminal, the executable ones are in green.

---

### Post by StRiFe10101 on 2007-07-12
Great posts.  Thank you  guys.  So if i understand it correctly you can install a program to a differet directory but if you put it in any place other than what your "path" is (example PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games")  then linux will not find the file to execute it?  So just let your programs install to a default directory?

---

### Post by Nekiruhs on 2007-07-12
> **StRiFe10101 said:**
> Great posts.  Thank you  guys.  So if i understand it correctly you can install a program to a differet directory but if you put it in any place other than what your "path" is (example PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games")  then linux will not find the file to execute it?  So just let your programs install to a default directory?
Prety much yes. You could add a folder to your path. Actually,  if you make a /bin directory in your home folder (/home/USERNAME/bin) and log out and back in its automatically added to your path. That only works for that one folder though. You have to do it manually for anythin else.

---

### Post by StRiFe10101 on 2007-07-12
Just for curiosity's sake, how do you edit your path environment variable... adding to the path=  list of directories? I got how you view it but editing?

---

### Post by iver2435 on 2007-07-12
You can edit it like this:

```
PATH=$PATH:/name/of/dir
```


This makes your path equal to your current path plus the directory you specify.

---

### Post by StRiFe10101 on 2007-07-12
Thanks ton.  You guys are great!

---

