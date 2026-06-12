---
title: "making a script"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by tedrampart on 2007-04-17
hey,  I'm not sure this fits in the beginners section, but I figure its a good place to start.

I need help writing a script to combine a bunch of tasks in order to help me with an ssh session on my works' network.

I want to combine these commands into one script if possible

$ chown <username> /home/<username>/.Xauthority
$ XAUTHORITY=/home/<username>/.Xauthority
$ export XAUTHORITY
$ DISPLAY=:0
$ export DISPLAY

now is this even possible?  I have it memorized and have a decent understanding of what it means, but I would like to save some keystrokes here.

I've tried all that in say "script.sh" starting with "#!bin/bash", and ending in "&" with "$"'s before each command, and without them as well.. but nothing seems to work.. 

anyone give me a hand with this?
thanks

---

### Post by Bachstelze on 2007-04-17
What should <username> be, exactly ?

---

### Post by igknighted on 2007-04-17
> **tedrampart said:**
> hey,  I'm not sure this fits in the beginners section, but I figure its a good place to start.

I need help writing a script to combine a bunch of tasks in order to help me with an ssh session on my works' network.

I want to combine these commands into one script if possible

$ chown <username> /home/<username>/.Xauthority
$ XAUTHORITY=/home/<username>/.Xauthority
$ export XAUTHORITY
$ DISPLAY=:0
$ export DISPLAY

now is this even possible?  I have it memorized and have a decent understanding of what it means, but I would like to save some keystrokes here.

I've tried all that in say "script.sh" starting with "#!bin/bash", and ending in "&" with "$"'s before each command, and without them as well.. but nothing seems to work.. 

anyone give me a hand with this?
thanks

you dont need a # or $.  Just start the lines blank.  Also, you need to chmod +x <filename> to make it executable.  If you symlink it to /usr/local/bin (make sure you dont over write anything) you could just run the command, no ./ or path involved

---

### Post by anujseth on 2007-04-17
what is the terminal output when you type ->
```
type bash
```
if it says /usr/bin/bash rather than /bin/bash, you must begin your script with that particular path. for eg:
#! /usr/bin/bash

the other thing you must take care of is to make the script executable and have it in your PATH variable. 
```
ls -l <scriptname>
```
should help with checking whether it is executable or not

and 
```
./<scriptname>
```
when in the directory of the script should run the script.

best of luck

---

### Post by tedrampart on 2007-04-17
I just put <username> as a replacement for the actual username on here.. in the script its the user..

I made sure it was also executible, as well, and the output of "type bash" was infact /bin/bash, so thats correct..

so having said that.. I think I've set it up right, its an executable.. here's what I have inside the script (I left out the chown command for now):
#! /bin/bash
XAUTHORITY=/home/staff/.Xauthority
export XAUTHORITY
DISPLAY=:0
export DISPLAY

now the outcome of this, should make it so apps load up on the screen of the host computer, not my computer (which if I type this all out line by line in the terminal it works..), instead, with the script, I still get errors like "cannot load gtk" blah blah which would tell me it didn't work.. 
I must be missing something..

---

### Post by anujseth on 2007-04-17
what does the script do by the way :D

---

### Post by tedrampart on 2007-04-17
well like I said, the idea is to have all these commands combined into one.  and all these commands allow me to (under ssh bash onto my work computers) remotely load x-apps onto their screen.  sort of like X forwarding in SSH, but only the apps don't load on my screen, they load on their screen.  

like I said, if I enter the commands individually, it works.  Say I want to load up vlc on the work machine's screen from home, if I enter all the commands, it will display on the work screen.. if I use the script, it outputs that it can't load gtk for that command and vlc won't display

---

### Post by anujseth on 2007-04-17
to be honest i'm not so sure of what you're trying to do but maybe you can try this instead.
```
export PATH=/home/anuj/Desktop/research/jdk1.6.0/bin:$PATH
```
thats how i set up my PATH variable to get java into my path when i'm programming. the $PATH in the end is to add the previous contents of the path to the variable. this does the work in scripts as well. try writing your shell variables like XAUTHORITY DISPLAY etc. this way ... hope it helps

---

### Post by tedrampart on 2007-04-17
I'm trying to load x-apps onto the computer I'm logged into remotely via SSH .. 

by default if I ssh into the computer and try to run a program, it says it can't load gtk.  so after hours or searching and asking, I finally got the commands above, and they worked.  so I thought I could put them into a script.  

entering in each line individually works for this, and the apps I run from the remote system display on the screen of the computer I've logged into.  the script doesn't do that.

sadly, what you suggested went way over my head :)

---

### Post by tedrampart on 2007-04-17
did you mean in the script having something like this?
(minus the quotes)
"#!/bin/bash
chown staff /home/staff/.Xauthority
XAUTHORITY=/home/staff/.Xauthority
export PATH=XAUTHORITY:$PATH
DISPLAY=:0
export PATH=DISPLAY:$PATH" ?

or am I totally off on this..

what about this?
"#! /bin/bash
export XAUTHORITY=/home/staff/.Xauthority:$XAUTHORITY
export DISPLAY=:0:$DISPLAY"

the more I try, the more confused I get.. it seems easier just to input each line like I originally did...

haha, can someone just give me the answers???

---

### Post by anujseth on 2007-04-17
now theres 2 of us who dont understand each other ... the first set of commands is way off ... the second ones are kinda like what i meant. i've never used ssh before ill read up and let you know. till then u can also try

[http://loll.sourceforge.net/linux/links/]("http://loll.sourceforge.net/linux/links/")

---

### Post by bodhi.zazen on 2007-04-17
LOL

to forward X with ssh use the -X flag :

```
ssh -X user_name@server
```

---

### Post by tedrampart on 2007-04-17
> **bodhi.zazen said:**
> LOL

to forward X with ssh use the -X flag :

```
ssh -X user_name@server
```

no, I already stated a couple times, this isn't what I want... that will load apps onto my screen.. I want to load them on the other screen....but thanks though...

anujseth: I'll try that link out after I wake up some more..  its pretty confusing stuff hah, but good for learning..
my second attempt at what yuo suggested seemed to make more sense after reading your suggestion a number of times.. the good thing, is that this isn't time sensitive...

---

### Post by tedrampart on 2007-04-24
okay, so I'm less of a noob now.. I got it to work with some advice from my brother.. 

seems I just had to add:
$1
to the end of the script, then when I want to load a program, I run the script before the command.. so example:
$ ./xauthscript.sh vlc

and it works.. I still have to run the script before each command, but atleast its only one line at the prompt.. 

thanks all for the help!!

without ubuntuforums.org I'd be one lost mofo..

---

### Post by bodhi.zazen on 2007-04-24
Well done !

You should post a copy of the working script and mark this thread as "resolved", if you do not mind of course ...

---

### Post by brennydoogles on 2007-04-24
> **tedrampart said:**
> okay, so I'm less of a noob now.. I got it to work with some advice from my brother.. 

seems I just had to add:
$1
to the end of the script, then when I want to load a program, I run the script before the command.. so example:
$ ./xauthscript.sh vlc

and it works.. I still have to run the script before each command, but atleast its only one line at the prompt.. 

thanks all for the help!!

without ubuntuforums.org I'd be one lost mofo..

You could add an alias to your .bashrc file in your home folder to look something like this
```
 alias forward='./xauthscript.sh' 
```

which would allow you to input something like 
```
forward vlc
```
into terminal and save yourself some typing. And you can change "forward" to anything you want... even a single letter if you do it often enough.

---

