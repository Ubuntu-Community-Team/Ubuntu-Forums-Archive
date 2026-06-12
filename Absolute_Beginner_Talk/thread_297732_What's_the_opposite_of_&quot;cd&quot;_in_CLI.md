---
title: "What's the opposite of &quot;cd&quot; in CLI?"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-11-11
The only commands I know by heart is: ls and cd.
But still when looking at sites such as this: [http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

I still can't find an answer to my question.  What's the opposite for the command:
cd (change directory)?
I'm like a kangaroo I can go forward but I can't go backwards :-k 

Everytime I've cd'ed myself deep in a filesystem I have to exit and then start the whole process again just because I can't go upp 2 steps.

---

### Post by PriceChild on 2006-11-11
```
cd ../
```Will take you a step backwards.

Alternatively, use```
cd /path/to/where/you/want/to/be
``````
cd ~/path/to/folder/starting/in/home
```

---

### Post by Peepsalot on 2006-11-11
I just wrote this in another post with a similar question, i'll just some copy some of the relevant info:
```

a single period "." refers to the current directory.
a double period ".." refers to the directory above the current one(aka the parent directory)
a tilde "~" refers to the current user's home directory (ex. "/home/peepsalot" for me)
a slash "/" with nothing preceding it refers to the root directory of your filesystem.

```

there is no opposite of the cd command.
cd can instantly go to any directory on your system with a single command as long as you know what to type.

there are two sort of concepts that you have to undertand: **absolute** paths and **relative** paths.

An **absolute** path begins with "/".
some examples:
```
cd /
```
takes you to the root directory, all other directories lie somewhere inside this one.

```
cd /bin
```
takes you to the bin directory which is directly inside the root dir.

```
cd /var/log
```
takes you to the "log" directory which is under the "var" dir, which is under the root dir.



**Relative** paths are basically any path you give that does **not** start with a "/"
These will cause cd to operate relative to the current directory (which can be denoted by a single period ".")
```
cd bob
```
goes to the directory "bob" which is hopefully in your current directory.

```
cd ./bob
```
equivalent to the previous command.  remember that "." refers to the current directory.

```
cd ~/Desktop
```
go to the Desktop directory inside your "home" directory

```
cd ..
```
go back one directory

```
cd ../..
or
cd ../../
```
go up *two* directories.  (the slash at the end is optional)

```
cd ./
```
takes you to the current directory (does absolutely nothing ;))

Hope that helps

---

### Post by engla on 2006-11-11
And the last useful thing: 
go to previous directory
```
cd -
```
so if you're in ~/Documents/projects/proj1 and issue 'cd /etc/conf/something', you can just type 'cd -' and get back to the ~/Documents/... path..

---

### Post by Peepsalot on 2006-11-11
Thanks engla, I never knew about that one.  Very nice.

I also just realized that running cd with no parameters goes to your home dir... :-k

---

### Post by bodhi.zazen on 2006-11-11
cd with no arguement goes home.

So to go from /mnt/sda1/some_directory to ~:```
cd
```

---

### Post by llamakc on 2006-11-11
> **engla said:**
> And the last useful thing: 
go to previous directory
```
cd -
```so if you're in ~/Documents/projects/proj1 and issue 'cd /etc/conf/something', you can just type 'cd -' and get back to the ~/Documents/... path..

I didn't either. Ugh! Thanks!

---

### Post by jingo811 on 2006-11-11
Man this is a true goldmine for me :KS They should say this stuff more often in all FAQs and guides out there!  Practically every guide I've come in contact with in the past has missed informing entirely about this command.

---

### Post by Peepsalot on 2006-11-11
Well, most of the stuff mentioned is not really specific to the cd command.    

All the information about paths: using "..", "~", "/" etc. is universal to command line programs(it is built into the shell).  So you can use these concepts when calling all different kinds of commands.  For example "less" is a simple program for reading through text files.  So you can use these path concepts with it too.  The main difference is that the path that "less" expects must end in a file name that represents a text file.```

less /var/log/syslog
less ~/.bashrc
etc.

```
Use up and down arrow keys to scroll, q to quit.

In fact, the shell in MS Windows("cmd.exe") works very similarly.  I learned most of these concepts back in the days of MS-DOS. :rolleyes:

---

