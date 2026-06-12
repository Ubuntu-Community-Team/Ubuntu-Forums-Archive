---
title: "Pannel"
date: 2005-09-24
forum: Absolute Beginner Talk
---

### Post by Corrupt on 2005-09-24
Hi, ummm what can i say, i am running Ubuntu 5 and while playing around i deleted the top pannel with the three drop menus. is there any way that i can get that back?

Also in the bottum pannel i have added a mini command line bar but i dont know any commands can you also helo me out?

---

### Post by heimo on 2005-09-24
[list]
[*]Right click on bottom panel -> New Panel
[*]Right Click on new panel -> Add to Panel
[*]Add Menu Bar, Notification Area and Clock (and what-ever you want on it)
[/list]Someone else will give you links / advice to learning command line / bash. :)

 

 EDIT: It's a very wide subject and depends what you want to do on it. Here's one link:
[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by Corrupt on 2005-09-24
yeah ummm what is bash? i saw it when i was playing in the terminals. Also what is the difference between root terminal and terminal (from what i can see isnt it like command in windows)

---

### Post by heimo on 2005-09-24
Oh, sorry for using Linux-lingo. Bash is default shell / command line interpreter - something like command.com on Windows, but much more powerful. Commands are different. For example dir -> ls (list), copy -> cp. Change dir is the same 'cd'.

You can do just about anything on command line - configure software, install and uninstall software, connect to remote computers, copy files around network, surf on web (using lynx or links text based browsers), program, write email... play games. :D It's something very powerful, very versatile and you can never master it fully - there's always something to learn.

If you want to do some specific thing, you can ask us and we'll help if possible - if you want to learn command line basics (that's where we all started!), you have to find some good tutorials or book about bash, command line, shell. Here's one place to start:
[https://wiki.ubuntu.com/BasicCommands]("https://wiki.ubuntu.com/BasicCommands")

Oh, and to clarify - that command area you have is meant for "oneliners" - you could for example start some program on it - try typing 'gimp' on it. To learn shell properly, open terminal window Applications->System Tools->Terminal or alternatively type gnome-terminal or xterm on the command area to open terminal window / shell. :)

---

### Post by Corrupt on 2005-09-24
I am aware of some linux commands due to the education department that i am a high school student under (and also a computer tech at a Primary school) has ftp access for websites, and i did a bit of exploring using command 

all i know about linux commands for the os its self is rm -rf (i think that is how it is)

---

### Post by heimo on 2005-09-24
To sum it up:

[https://wiki.ubuntu.com/BasicCommands](https://wiki.ubuntu.com/BasicCommands)
[http://linuxcommand.org/](http://linuxcommand.org/)

And when you open terminal - this is something that you should read through one day if you want to know more about bash: man bash (I don't recommend you to do it right away, it can be a bit daunting at first sight, but contains lots of helpful tricks). You can get help for most of the commands using

 ```
man [command]
```
or
 ```
[command] --help
``` 
For example:
 ```
ls --help
``` 

Careful with that rm -rf ! :D (rm stands for *remove *r for *recursively *and f for *force*

---

### Post by phen on 2005-09-24
the difference between root terminal and terminal is the user who is using the terminal. actually, it will be you in both cases, but you have to enter a super user password to start the root terminal. root is the administrator of your linux box. root is allowed to do anything. 

when you install software , you do a "sudo apt-get install"

sudo means, that you run apt-get as root (Super User DO). in the root terminal, you dont have to sudo for every command, as you are allready the super user!

cheers!

---

### Post by Corrupt on 2005-09-24
ok now i under stand, also do you know how i can edit the login screen, like the colors where everything is, the background image, the login sound (and i woudl prefure not to do it in terminal untill i know what i am doing)

---

### Post by heimo on 2005-09-24
These may be different (I'm running Breezy Badger prerelease version of next Ubuntu, version 5.10).

Check System->Administration->Login Screen Setup

and System->Preferences->Sound 
SoundEvents->SystemEvents->Log In

---

### Post by Corrupt on 2005-09-24
ok, not exactly what i ment, i should have said how do i create my own graphical greeter (a tab under Check System->Administration->Login Screen Setup)

---

### Post by PsyberOneZero on 2005-09-24
Here's a mini HOWTO on creating your own gdm login theme:
[http://julian.coccia.com/blog/index.php?p=51&more=1](http://julian.coccia.com/blog/index.php?p=51&more=1)

It's alot of playing around with the XML file for the theme (placement, location, transparency, etc...)

Here's how to take a screenshot of your login to post or check for errors:
[http://julian.coccia.com/blog/index.php?p=29&more=1](http://julian.coccia.com/blog/index.php?p=29&more=1)

---

### Post by Corrupt on 2005-09-25
Is there any way that i can get more options, like where the login is situdated, Having Both username and password on the same screen (not just one)

---

