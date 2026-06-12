---
title: "Access programs anywhere in terminal?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by pac-man on 2007-06-01
Hi, I'm using xubuntu 6.06.1 and as many of you might know, it comes with firefox 1.5 by default. Well, whenever I wanted to start firefox from a terminal window I just typed "firefox", that's it! no matter if I was in /home/user or anywhere; it was like "wide system available" command.

Then I uninstalled it and installed the verion 2.0.0.3, when I tried to open it from a terminal window now I gotta go to /usr/lib/firefox, no more "wide system available" as a command.

Now, when I try to access to firefox via the top panel icon, is impossible. In the properties of that button, in the "command" field, there was just a plain "firefox", and now I had to change it using the full path.

Is there a way to make it a wide available command again? I'd like to know that not only for firefox, but also for java and some other apps. I installed java 6 and it's quite annoying to type sudo /usr/java/bin/jre-blah blah blah -jar anyprogram.jar :(

Any info will be much appreciated, thanks!

---

### Post by kernel tom on 2007-06-01
how did u install firefox?

you might have to do a "clean" install... 

also it might not be firefox, it could be mozilla-firefox

your icon path might also be incorrect

---

### Post by Sparkster185 on 2007-06-01
This has to do with your PATH environment variable.  PATH contains a sequence of directories, separated by colons, that the shell searches in when you type in a command.

The directories in PATH are traversed, from beginning to end, until a match is found.  Note that if a binary resides in more than one directory found in PATH, the first match is executed.

You can append new directories to your PATH variable if you want.  What I do is I edit my login/bash.rc file so my PATH is modified everytime I login/use a terminal.

If you want to add  ~/myPrograms to the beginning of path, you can do
```

export PATH=/home/clarkb/myPrograms:$PATH

```
To add ~/myPrograms to the end, you do
```

export PATH=$PATH:/home/clarkb/myPrograms

```

---

### Post by Bachstelze on 2007-06-01
Please follow those steps to install FF 2.0 on Dapper :

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by pac-man on 2007-06-01
Sparkster185: thanks a lot, your answer was exactly what I needed; but I'd like to know something else.

Where is located that file where I can see the paths ?? I did the export path= thingy and it worked well, but i'd like to know where are all paths like those located.

THanks

---

### Post by pac-man on 2007-06-01
OH!! That only worked temporarily, I rebooted and now ive got to type that export comand again :( 
 
is there a way to make it last forever?

---

### Post by taurus on 2007-06-01
If you want to make it permanent, you need to add that line, export path thing, to the end of your ~/.bashrc.

```
mousepad ~/.bashrc
```

---

### Post by pac-man on 2007-06-04
Alright, but i've got a problem:

I added those PATH=/path/of/the/program to my ,bashrc file and when I restarted the computer, the shell didn't recognize most of the commands, not even the most basic ones (ls, rm, cp, mv). I couldn't even access mousepad to reedit the file! I had to login using my sister's user, login as root in xterm and from there, edit the .bashrc file and delete those lines I added... then everything was back to normal in my user.

Is there any special syntax to add those lines? I added them without the "export" command, just the PATH= and the path of the program.

And finally, I've got a question about this. How is that firefox was formerly recognized as a command in a terminal window even without a path declared in the .bashrc???

---

