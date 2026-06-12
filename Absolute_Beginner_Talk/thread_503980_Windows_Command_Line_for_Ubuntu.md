---
title: "Windows Command Line for Ubuntu?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by 7Priest7 on 2007-07-18
I know shell is slightly similar to Windows Command Line
and there are things Shell does that Windows Command Line can't

I want to know if I can Upgrade the shell to work with Windows Command Line statements?

I do not feel like learning multiple Command Line utilitys...

Any/All help Appreciated 

Alex

---

### Post by asmoore82 on 2007-07-18
The Terminal or Command Line on modern Linux systems is the result of Decades of evolution.

The Command Prompt on Windows PC's is, well, pretty much a broken echo of DOS.

A Command Line should not be just for using command line utils. Quite the contrary, on
*nix systems the Command Line gives you access to your entire OS.

About learning multiple command line utils...
The UNIX stuff is applicaple to UNIX, Linux, BSD, and Mac OS X
so I believe it would be well worth the effort in learning.
Micro$oft will eventually come on board and take a stab at
building a *nix compatable system in another 10~15 years or so.

---

### Post by AlexenderReez on 2007-07-18
i think alt + f2 is equals to command line in windows....terminal equals to cmd.exe ....right?

---

### Post by Raineer on 2007-07-18
You'll have to provide an example of what "Windows Command Line" can do that Linux can't?

If you mean you don't like opening a terminal when you just need a quick command line, press Alt-F2

---

### Post by Henry Rayker on 2007-07-18
in your home directory, you should have a .bashrc file. In it, there should be a reference to aliases (just search the file for alias). Using this format, you could alias some of the commands.

For example, you might want to use dir instead of ls to list the contents of the current directory. In this case, use this line:
alias dir="ls"

Hope that helps somewhat. If not, try to explain your issue a little clearer.

---

### Post by wolfen69 on 2007-07-18
windows command lines will not work(without major tweaking). besides, it is possible to configure ubuntu without having to use the command line at all.

---

### Post by 7Priest7 on 2007-07-18
The "evolution" sucks...
Terminal does the same things with diffrent keywords...
"Stick with what works"

Anyhow I am not asking to get rid of the terminal altogether

I am asking to be able to patch the terminal to traslate the windows command line keywords into linux keywords...


Alex

---

### Post by 7Priest7 on 2007-07-18
> **Henry Rayker said:**
> in your home directory, you should have a .bashrc file. In it, there should be a reference to aliases (just search the file for alias). Using this format, you could alias some of the commands.

For example, you might want to use dir instead of ls to list the contents of the current directory. In this case, use this line:
alias dir="ls"

Hope that helps somewhat. If not, try to explain your issue a little clearer.

Thank You greatly

Alex

---

### Post by Raineer on 2007-07-18
Well, Unix was around before Windows, so I'd be careful with the "evolution" you're reffering to.

If you really just want things named the same, I'd follow Henry's advice above.  You can set it up where "dir" is the same as "ls -al"  or whatever you want.

---

### Post by asmoore82 on 2007-07-18
> **7Priest7 said:**
> 
"Stick with what works"
Alex

UNIX came first my friend :D

---

### Post by asmoore82 on 2007-07-18
what exactly do you use your Windows CMD for that you need to do in Linux?

And the vast majority of these commands aren't "Keywords" ...
they are autonomous executable programs on the OS.

---

### Post by Orochi on 2007-07-18
If you plan on using Linux for any length of time I really recommend you learn the *nix terminal commands. In the long run it'll be far easier than trying to alias DOS commands. It's not all that hard, a few weeks of regular use of Linux and you will know all the basic commands by heart.

---

### Post by 7Priest7 on 2007-07-18
Is there a list of Windows to Linux Aliases?

Alex

---

### Post by Gadren on 2007-07-18
>  	Is there a list of Windows to Linux Aliases?

Alex

I don't think so, but there are lists of basic Windows commands and Unix commands, and you could probably work something out from that.

Although I really do encourage you to learn the Unix system -- I believe that using Linux effectively requires a change in perspective and a recognition of its differences.

---

### Post by meborc on 2007-07-18
alias is a great way to shorten some commands you use often... but changing all linux commands to win alternative ones... well... if you use any other linux box or if you reinstall ubuntu or if you install any other *nix distro you would need to do it all over again... or copy the file :)

i wouldn't do it... if you don't like linux way - stick with windows... linux is not compulsory you know ;)

---

### Post by asmoore82 on 2007-07-18
> **7Priest7 said:**
> Is there a list of Windows to Linux Aliases?

Alex

I don't really think that would help you...

The Linux Command Line Environment is so functional it would be much better to
find out what exactly you are trying to do and Let's do it the *nix way.

---

### Post by Motoxrdude on 2007-07-18
Here is a man page on linux bash commands: [http://www.ss64.com/bash/]("http://www.ss64.com/bash/"). Hope this helps.

---

### Post by cmnorton on 2007-07-18
Most requests I've seen have to do with emulating linux under Windows or running Windows applications under Linux. There are many excellent posts in ubuntu forums about wine and probably about cygwin (I have not searched for cygwin here).

The best I could find was to emulate windows commands, but you would have to implement these in the shell. 

[http://www.go4expert.com/forums/showthread.php?t=3477](http://www.go4expert.com/forums/showthread.php?t=3477)

---

### Post by dpar on 2007-07-18
If you want a distro that looks and works just like windows, heres the link............>[http://www.microsoft.com/windows/default.mspx](http://www.microsoft.com/windows/default.mspx)

---

### Post by Raineer on 2007-07-18
Well the whole issue with creating aliases is...how hard is it to really learn?

I mean, any new console at first seems daunting, but 99% of the commands you will use have what it called a "man" page built right in.  You don't even have to go anywhere for a manual!

The easy ones:
dir = ls   (list)
copy = cp   (copy)
del = rm  (remove)

Plus you can always type **man cp** and it will show you the syntax and all you need to know.

---

### Post by bigboy_pdb on 2007-07-18
To understand the advantages of the command line you should probably read my post in this thread:
[http://ubuntuforums.org/showthread.php?t=463895&page=2](http://ubuntuforums.org/showthread.php?t=463895&page=2)

One of the best aspects of the command line is input and output redirection. With GUIs you can't redirect output to another GUI program, but with a command line you can. For example, if someone prints non-selectable text on a screen, in order to get the text you'd probably need to take a screen shot and use an optical character recognition program to convert the image to text (or you could retype it). With a command line everything is text so you can manipulate anything that is printed to the screen. There are definitely places where GUIs are better (and I explain this in the thread that I posted a link to), but GUIs are neither superior nor always better.

Many people have this concept that command lines are backwards interfaces that are completely useless and that everything should have a GUI implementation first and the program can have commands that allow a person to use it on the command line only if it is necessary for certain people (such as developers). This is a bad way of thinking. Command lines are incredibly powerful and productive interfaces when you know how to use them. Unlike Windows, Linux doesn't dumb down the operating system and make it less useful in order to appeal to laypeople (and this is one of the reasons why I changed operating systems among many other reasons).

Also, it is easier to develop programs for the command line than to create a "so-called" user friendly GUI program. The funny thing about this is that it seems as though many of the people who complain about lack of GUIs don't appear to be helping projects to implement user friendly GUI interfaces for programs, but maybe I'm wrong about this (which is why I use the word "seems").

---

### Post by bigboy_pdb on 2007-07-18
By the way, if someone were to make a shell that uses Windows commands, it would be pretty useless because the Windows commands can't do very much and there are far more Linux commands than Windows command. I'd suggest learning the Linux commands.

Some commands that would be good to learn are:
**man** Following this command type the name of the command that you want to learn about. A manpage for the command will be shown. Use the up and down arrows, as well as, the "page up", "page down", "end", and "home" keys to move through the manpage. Also, don't forget to look at the "See Also" section at the end for a list of additional commands that may be related to the one that you looked up.
**cd** Changes your current directory (just like the Windows CD command).
**ls** Lists the subdirectories/folders and files in the current directory.
**sudo** Allows a command to be run as the root user (a keylogger could read your password when using this but only root commands can be typed in the terminal for a certain amount of time).
**gksudo** A GUI that asks for the user password (it is highly unlikely that a keylogger could read read this but it grants root access to all GUI programs for a certain amount of time).
**chmod** Changes the user permissions on a file that is owned by the current user.
**chown** Changes the owner and/or group for a file that is owned by the current user.
**ps** Lists the processes that are running. When used with "-e", all system processes are listed.
**kill** Sends a signal to a process. The default signal is the terminate signal.
**mount** Adds a mountable device (such as a hard drive or CD-ROM) to the directory tree at a point that you specify.
**umount** Removes a device from the directory tree.
**iwconfig** Lists network interfaces and the information corresponding to each interface.
**gedit** Opens a file in the gedit (GUI) text editor.
**nano** Opens a file in the terminal text editor.
**fdisk** Partitions and formats hard drives (and it does not create a new file system).
**mkfs** Creates new file system on hard drives that have been formatted but don't have one. The files system must match the type of file system that you partitioned the hard drive to have. 

There are far more commands that you can learn that will be useful depending on your needs. The ones that I listed are some good ones to start with.

Something else that is useful to know is the "tab" key attempts to fill in file/directory/folder names when you start typing them. If there is more than one match and they all have the same characters up to a certain point, it will fill in what it can. If there is more than one match and they don't all have the same characters up to a certain point, it will list all the files/directories/folders that match what you've written so far. Also, the up and down keys let you scroll through commands that you've previously written.

---

### Post by RomeReactor on 2007-07-18
Hi **7Priest7**. In case you come back to check the thread, I suggest you give the Linux command line a shot; [this site]("http://www.linuxcommand.org/") contains a very good overview of the terminal.

However, if you still want to stick to windows commands, you could install [dosemu-freedos]("http://www.dosemu.org/"), which will give you access to [FreeDOS]("http://en.wikipedia.org/wiki/Freedos"), a DOS environment emulation. Look for it in Synaptic (System->Administration->Synaptic Package Manager), or to install from the command line:
```
sudo apt-get install dosemu-freedos
```
I don't know how functional this implementation is, but it may be what you're looking for and save you the trouble of creating many aliases for the command line.

---

### Post by deepclutch on 2007-07-18
Did anyone mentioned mtools as reply to OP?hrmm...
[http://mtools.linux.lu/](http://mtools.linux.lu/)

---

### Post by coolen on 2007-07-18
You may not think much of the command line right now, but you will. Once you start using the system more and see how useful it the command line is, you'll want to be using the standard commands, if only for easier communication with the outside world.
I'd only ever used the command line a handful of times before turning to Linux. Mostly for formatting old Windows installs, seeing as how they'd become all slow and crappy and infected.
Bash is a wonderful environment. Learn it, love it, live it.

---

### Post by machoo02 on 2007-07-18
> **7Priest7 said:**
> Is there a list of Windows to Linux Aliases?

Something like [this]("http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html") perhaps?

---

### Post by anewguy on 2007-07-19
I'm new to this myself, but I would definitely say to follow machoo02 post.  While it does show how to set up aliases at the end, I also would suggest you skip the aliases and just follow the posted list.  In this way you can learn as you go, and it will help you further down the line.  While it is beyond what you need to know now, the *nix "shell" you run (sort of like the windows command line on steroids) handles all of the functions of the command line but does SO much more.  No post here can do it justice - you have to see shell scripts that do big things to understand what I mean.:)

I hope you will take the time to follow the cross reference and gradually learn to use the shell to do the things you need to.  Look at it as a challenge to learn something new!:)

---

### Post by odiseo77 on 2007-07-19
Haven't followed the whole thread, but IMO it's better to get familiar with the unix/linux commands if you really want to learn linux (instead of using aliases). 

Did anyone mention these couple of usefull links??:

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

[http://tldp.org/](http://tldp.org/)

Greetings.

---

