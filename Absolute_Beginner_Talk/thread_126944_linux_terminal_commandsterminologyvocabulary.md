---
title: "linux terminal commands/terminology/vocabulary"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by bountonw on 2006-02-07
I am new to linux and have been reading an online manual

[http://writers.fultus.com/garrels/ebooks/Machtelt_Garrels_Introduction_to_Linux.pdf](http://writers.fultus.com/garrels/ebooks/Machtelt_Garrels_Introduction_to_Linux.pdf)
There are also other sites of this in html, but I wanted to print it and hold it.  Google the first phrase "Many people still believe that learning Linux" will give you many different sites and formats of this simple user guide.

A useful link to the forum post "Terminal for Beginners" is here
[http://www.ubuntuforums.org/showthread.php?t=73885&highlight=linux+commands](http://www.ubuntuforums.org/showthread.php?t=73885&highlight=linux+commands)

I have found a nice list of linux commands at the following sites.  Each command is linked to a definition.

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

The following terminal commands help give information on  individual linux commands.  These are listed in order of usefullness, although info and man as are as I can tell are quite similar in the ammount of information given.
info coreutils <command name>
info <command name>
man <command name>
whatis <command name>

I hope that this is helpful for other beginners.  Now I have a question regarding all of this that I will post as a reply to this thread.

---

### Post by bountonw on 2006-02-07
As I said, I am new to linux.  If any experienced user would like to add links for resouces to learning linux and basic linux commands, that would be appreciated and I think it would be a good resource.

This might also be a good place for beginners to ask questions that they still have after reading the different links and using the man and info commands.

My first question is this:
when doing an ls [list]
command, some of the folders are so large that several pages of  contents scroll by before I know what happened.  Is there a way to get the list to stop at each page?  It has been an eternity since I used DOS (I have used mainly windows), but I think that they had a dir /p command that did this.

---

### Post by Kyral on 2006-02-07
Thanks for noticing my Terminal For Beginners. As I think I mentioned, the output of almost any command can be piped through less to stop that scrolling

So
```
ls <dir> | less
```

Would work nicely

---

### Post by bountonw on 2006-02-07
Thank you.  I just found the | less command in reading through your tutorial and was going to post the answer here, but you beat me to it. 

Thank you very much for the detailed  instructions.   I have subscribed to your thread and have practiced some of your examples.

---

### Post by Madpilot on 2006-02-07
[BasicCommands]("https://wiki.ubuntu.com/BasicCommands") is the Ubuntu wiki's basic command-line page; I also like [linuxcommand.org/]("http://www.linuxcommand.org/")'s tutorials - very nicely laid out & easy to follow.

---

### Post by cwaldbieser on 2006-02-07
[QUOTE=Kyral]Thanks for noticing my Terminal For Beginners. As I think I mentioned, the output of almost any command can be piped through less to stop that scrolling

So
```
ls <dir> | less
```

Would work nicely[/QUOTE]
And if you'd like it to still show the colors for different file types:
```

$ ls --color <dir> | less -R

```

---

### Post by Kyral on 2006-02-07
*forgot that his Bash Alias file has ls doing that by default..*

---

### Post by Madpilot on 2006-02-07
[QUOTE=Kyral]*forgot that his Bash Alias file has ls doing that by default..*[/QUOTE]

I thought Ubuntu's stock Bash config (.bashrc?) had colours enabled by default in ls?

---

### Post by vialick on 2006-02-07
Hey, thanks heaps for those links they shall prove to be useful I do believe. :D

---

### Post by cwaldbieser on 2006-02-07
[QUOTE=Madpilot]I thought Ubuntu's stock Bash config (.bashrc?) had colours enabled by default in ls?[/QUOTE]
It does, but only for output to a tty (--color=auto).  For piping through less, you need to force the colors (--color) on and then tell less to pass through the raw escape codes (less -R).

---

### Post by bountonw on 2006-02-08
1.  Is there a bash command to moniter what is going on in the internet?  I am installing a program and would like to know the rate of download.  (For that matter, it would be nice to know who I am connected to etc.)  

2.  Is there a command to lock/freeze everything while I step out of the room for a minute so that my kids/cats don't accidently mess up what I am in the middle of.

Scanned through various sources on this (see original post), but didn't come up with anything, but I often miss things.

---

### Post by bountonw on 2006-02-09
Still learning bash every day but haven't found anything on my previous post that I know how to use.

> 1. Is there a bash command to moniter what is going on in the internet? I am installing a program and would like to know the rate of download. (For that matter, it would be nice to know who I am connected to etc.)

2. Is there a command to lock/freeze everything while I step out of the room for a minute so that my kids/cats don't accidently mess up what I am in the middle of.

---

### Post by cwaldbieser on 2006-02-09
[QUOTE=bountonw]Still learning bash every day but haven't found anything on my previous post that I know how to use.[/QUOTE]
This shows who you are connected to via TCP.
```

$ netstat --tcp

```

This shows packets transferred and received for each interface:
```

$ ifconfig

```

---

### Post by bountonw on 2006-02-09
with netstat --tcp I get 5 lines of answers with the first 4 being localhost....
The last one is 192.168.1.2:#####  Is this normal?  

Also is this the way to check if someone else has hacked on to ones computer through the internet?  I had a firewall and spyware program on Win-XP, but don't have anything on linux yet and have a long list of things to do before I get any installed (unless it is urgent, but from reading through the threads it seems that linux is safer than Windows and doesn't require firewall.)

---

### Post by cwaldbieser on 2006-02-09
[QUOTE=bountonw]with netstat --tcp I get 5 lines of answers with the first 4 being localhost....
The last one is 192.168.1.2:#####  Is this normal?  

Also is this the way to check if someone else has hacked on to ones computer through the internet?  I had a firewall and spyware program on Win-XP, but don't have anything on linux yet and have a long list of things to do before I get any installed (unless it is urgent, but from reading through the threads it seems that linux is safer than Windows and doesn't require firewall.)[/QUOTE]
By default, you won't have any servers set up for someone to break into.  Once you set up some sort of server (samba, ssh, etc.), then you might want to consider putting up a firewall.

---

### Post by bountonw on 2006-02-11
A couple of days ago I asked if there was a command to lock/freeze the window while I stepped out of the room.  Guess what???  It was right in front of me all along!!!  Here I was scanning the bash pages for a terminal command while I had a GUI.  On ubuntu breezy it is in System and the second to last option.  (Although I am probably the only one who didn't notice it.)  With this, I found the option of changing users and signed in with my wife's username on another screen just to see what would happen.  After that I got bounced around between the screens at odd moments.

Anyway, a command line for this would be nice too as I am trying to master the command line.  Would like to be able to freeze the screen from command line without logging out.

---

### Post by christhemonkey on 2006-02-16
Does not scroll lock lock the keyboard?
i seem to rememeber pressing some key around there and then being very stuck till accidentaly pressing it again!

---

### Post by carlosqueso on 2006-02-16
```
xscreensaver-command -lock
``` should work (I can't check it from here, as I'm at work and ssh'ed into my machine at home.

---

### Post by bountonw on 2006-02-18
scroll lock doesn't seem to lock the key board.

carlosqueso, thank you for the command.  It works.

---

