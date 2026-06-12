---
title: "Terminal Kommands"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Takuhari on 2007-07-23
This Noobee needz help >_<

can someone help me with terminal commands for these situations?

1: I need to delete a directory...
2: i need to copy a directory from the folder before it. example... 
...we have filder A, B, C.
...I go into C aand i want to copy B into it.
3:I need to archive a directory.
4:how do you rename a directory and file?

This would really help me out.

thanks alot^^

:confused:

---

### Post by useResa on 2007-07-24
There are various sites with lots of information on the commands you can use in a terminal. I personally use [die.net]("http://linux.die.net/man/").
1. For removing a file or a directory the **rm** command is used. You can find information on usage [here]("http://linux.die.net/man/1/rm").
2. For copying files the **cp** command is used. You can find information on usage [here]("http://linux.die.net/man/1/cp").
3. To archive a file you would make use of the **tar** command. More info [here]("http://linux.die.net/man/1/tar").
4. Renaming is basically done by moving a file. Thus implicitly renaming it in the process. Information on the **mv** command can be found [here]("http://linux.die.net/man/1/mv").

I hope this information will help you achieve what you want.

---

### Post by tommcd on 2007-07-24
Here is a good beginner oriented site to learn command line basics:
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)
Another good site for linux basics:
[http://www.tuxfiles.org/](http://www.tuxfiles.org/)

---

### Post by sad_iq on 2007-07-24
And for the lazy :) install mc(the equivalent of norton commander): ```
sudo aptitude install mc
```

---

### Post by bulldog060 on 2007-07-24
1) if the directory is empty use **rmdir directory_name**, if there are files in it use** rm -Rf directory_name**  ** the -R is the common recursive flag, and -f avoids the `are you sure you want to delete...'

2) if your in directory C it would be **cp -R ../B/ .** if you were up a directory you could just **cp -R B/ C/**

3) **tar -cvf tarfile.tar directory/***  ... -c = create, v = verbose output f = file 

4) **mv file_or_directory new_name**


When I was first playing around with the shell I picked up `Unix Shell Programming' by Stephen Kochan and Patrick Wood ( Its a purple book ) and that has alot of basics as well as useful tips. Hope this helps.

~ron

---

### Post by Mornedhel on 2007-07-24
Careful with rm -rf :
sudo rm -rf / is not a good thing to type when you wanted sudo rm -rf *

---

### Post by bulldog060 on 2007-07-24
> **Mornedhel said:**
> Careful with rm -rf :
sudo rm -rf / is not a good thing to type when you wanted sudo rm -rf *

On that same note, **rm -Rf *.*** is also bad since **.** is the current directory and **..** is the parent and both will match your rm/chmod/chown etc. will go backwards

people new to command line, or used to winblows will try this alot.

~ron

---

