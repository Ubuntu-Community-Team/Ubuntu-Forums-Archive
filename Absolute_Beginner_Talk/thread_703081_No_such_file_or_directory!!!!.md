---
title: "No such file or directory!!!!"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by ferrettmerr on 2008-02-21
Right now i am really tired and frustrated, so i apologize ahead of time if my sentences look like gibberish(like everything does right now).
I am having a huge problem running any executible that i try to install. I thought it might be that one but i have tried 3 and none work!
the three i tried are
epsxe(two guides)
Aliensomething(the shooter)
the game created by aaron, 2d Dungeon crawler thingy, forget that name too

what happens is i set everything up, allow it to be run as an executable. and i go to run it with ./epsxe or other ./filename it is and it says file not found in directory....... but im in the dir. and i can see it with ls -l and it comes up in green!!! 

help me please, i really dont wanna have to go to windows every time i wanna play ffix or TLOTD thank you!!!
~ferrettmerr

---

### Post by jan de beuker on 2008-02-21
To run scripts and software from the terminal it has to be in the path.
When you type echo$PATH you can see what direectory are used 
If you want software to run from for example /home/user/bin  you have to ad this to the path

Jan

---

### Post by bodhi.zazen on 2008-02-21
did you make it executable and run as root ?

```
sudo chmod a+x ./file
```

Then

```
sudo ./file
```

---

### Post by raja on 2008-02-21
Can you post the output to both 'ls -lh' and './whatever'?

---

### Post by jan de beuker on 2008-02-21
I don't think it is that complicated
I also think nobody understands what I mean.
So I will try to explain the system  use.
Most people use ark to unzip and create directory's with the mouse and give it a name.
For example "my games".
Lets say this directory is on your desktop.
Open a terminal and use cd Desktop
Not a problem
Now use cd my games
It won't work
Now use the command for make a directory
mkdir my games
And there you have it two directory's one called my the other games
To make shure you can use  the commandline on these directory's you have to fill in the space.
For example "my_games¨ 
Now cd my_games will work
In my home directory I created a /bin and I make all the directory's with the command line so I  know the command line can use them.
I also changed the path from the terminal so that /home/user/bin is added

Jan

---

### Post by bodhi.zazen on 2008-02-21
Spaces in file names are easily handled.

1. "Escape" the space with a \

file\ name

2. Use quotes.

"File name"

3. Use Tab completion

file<tab> -> becomes -> file\ name

---

### Post by Trail on 2008-02-21
> **bodhi.zazen said:**
> Spaces in file names are easily handled.

1. "Escape" the space with a /

file/ name

2. Use quotes.

"File name"

3. Use Tab completion

file<tab> -> becomes -> file/ name
That should be \ instead of /, for example:

My\ Games

Tab Completion seconded.

---

### Post by bodhi.zazen on 2008-02-21
OOps, I hate typos (PEBKC), thanks I edited my post.

---

### Post by jan de beuker on 2008-02-21
So that is what I mean
I know but lots of people that start with linux don't know these things and searching hours for a litle space in directory name and don't  know why they get the message "no such directory"

Jan

---

### Post by ferrettmerr on 2008-02-21
Hey thanks for all your help so far, output = 
and yes i do have permission to run it and i have set it as an executable

ls-lh
drwxr-xr-x 2 root root 4.0K 2002-01-24 16:43 bios
drwxrwxrwx 2 root root 4.0K 2008-02-21 00:02 cfg
drwxr-xr-x 2 root root 4.0K 2008-02-21 00:02 cheats
drwxr-xr-x 2 root root 4.0K 2008-02-21 00:02 docs
-rwxr-xr-x 1 root root 642K 2003-08-04 16:52 epsxe
drwxr-xr-x 3 root root 4.0K 2008-02-21 00:02 $EPSXE
-rwxr-xr-x 1 root root 642K 2008-02-21 00:10 epsxe_bak
-rw-r--r-- 1 root root 1.7K 2002-01-27 18:04 keycodes.lst
drwxrwxrwx 2 root root 4.0K 2008-02-21 00:02 memcards
drwxr-xr-x 2 root root 4.0K 2002-01-27 18:02 patches
drwxr-xr-x 2 root root 4.0K 2008-02-21 00:02 plugins
drwxrwxrwx 2 root root 4.0K 2008-02-21 00:02 snap
drwxrwxrwx 2 root root 4.0K 2008-02-21 00:02 sstates

./epsxe
larry@larry-laptop:/usr/local/games/epsxe$ ./epsxe
bash: ./epsxe: No such file or directory

i understand what you are saying about the names, but i always use tab complete
Thank You
Larry
P.S. i dont think i understand how to run a program, im in the dir and use ./nameoffile and it wont run. Do i have to be in a different folder? or do i have to set it up differently?

---

