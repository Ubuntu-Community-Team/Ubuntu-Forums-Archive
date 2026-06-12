---
title: "A few questions about the command line."
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Feba on 2007-06-04
First off, "why should i use a command line?" 

I, personally, have already seen some of the amazing things the terminal can do (compare sudo apt-get install thingy to using Add/Remove), so I don't need to be convinced in this, but I'd like to hear some opinions people have on the command line, to explain it to other newbs

Secondly, "What is there to do on the command line?"

Mainly, I've been thinking about forcing myself to use the terminal at least an hour a day, so I can become more familiar with it, but what is there to do? More specifically, what programs work in a terminal enviroment? naim I know of, nano for editing text files, I know there has to be more out there (and no, i'm not interested in MUDs) Is there a package out there that would let me get a lot of them at a time? (sudo apt-get install terminalthingys?)

Lastly, "What easter eggs does the terminal have?"

This kinda applies to linux in general, easter eggs are always fun. So far I know about apt-get moo, aptitude (-v/vv/vvv/vvvv/vvvvv) moo, ddate, I think i've seen a few others I can't remember now, funny little things like this to show people.

Thanks!

---

### Post by Tux Aubrey on 2007-06-04
For me, knowing some key commands is essential to fixing things that sometimes break (usually because I played with them).  I think basic file management (mv, ls, chown, chmod, etc) are essential, as is being able to use a command line editor.  Just as important is knowing which files (xorg.conf, menu.lst,...) are the ones likely to break things.

Yes and things like apt-get are truly very good - Like many other packages, apt-get is so much more versatile from the command line.  A gui can be very neat but will only allow you access to a subset of the power of the underlying program.

That said, I am dead lazy and will use a gui 90% of the time.

Oh, if you like apt-get moo - get cowsay (apt-get install cowsay).  Hours of mindless fun.;)

---

### Post by Feba on 2007-06-04
So there aren't any other easter eggs?

---

### Post by jonward0690 on 2007-06-04
Nope learn the terminal and you can fix your system a lot easyer.

---

### Post by arsenic23 on 2007-06-04
wget has got to be my favorite use of the terminal.  Whenever I want to download something I just tab over to one of my open terminal windows and use wget.

Other things I use that run out of the terminal

links2 - web browser
nmap - port probe and other misc tasks
lanmap - neat network mapping tool
sdparm - manually spins down hard drives ( just recently was turned on to this )
vlc - can play music without a GUI

and a bunch of other stuff that doesn't come to mind right away.

---

### Post by shae on 2007-06-04
Personally I love the command line so I am biased, but if I had to explain to someone who is new, I would say:

The command line allows for faster input.  One example would be to compare apt-get install inkscape epiphany . . . to a similar process in synaptic.  I am not saying that I hate synaptic.  I use it all the time.  The command line is also a powerful tool because it allows you to create shell scripts.  These can be used to automate several processes that may need to be repeated.

One of the best thing about learning command line is empowering you to use the recovery console.  Another thing I enjoy is command line installations and building the OS up from that.    If anything could teach you some of the powers of the command line, I think that compiling your own kernel (with ck patches) would be a great practice as well as setting up the latest drivers from your video card manufacturer (without the help of envy or the use of the ones in the repo)  After that try your hand at writing a shell script or two.  

Good luck with your exploration of the command line.

---

### Post by pbw on 2007-06-04
> **arsenic23 said:**
> wget has got to be my favorite use of the terminal.  Whenever I want to download something I just tab over to one of my open terminal windows and use wget.



Give aria2 a try, it's got some nice features such as segmented downloading. Here's a list of some features off the homepage:
> 
Command-line interface
Download files through HTTP/HTTPS/FTP/BitTorrent
HTTP Proxy support
FTP through HTTP Proxy
HTTP BASIC authentication support
HTTP Proxy authentication support
Segmented downloading
Download speed throttling
Upload speed throttling in BitTorrent
Cookie support(currently aria2 ignores "expires")
Run as a daemon process.
Selective download in multi-file torrent
BitTorrent Fast extension support
Metalink version 3.0 support(HTTP/FTP/BitTorrent)
Chunk checksum validation in Metalink
netrc support
Configuration file support

I believe it's in universe.

If you find yourself using the terminal for alot of tasks, I'd the most useful'd gotta be screen hands down.

rtorrent, irssi, centericq, grep, ssh and vim are some other nice apps that come to mind.

---

### Post by RedSquirrel on 2007-06-04
I don't like having to reach for a mouse more than necessary so I prefer to use my keyboard for most things.

I don't bother with a file manager. I just use the command line for that.

I also rip CDs on the command line with crip.

There was a thread around with all sorts of command-line ideas and easter eggs. Do a search and I'm sure you'll find it.

EDIT:

Here it is: [**How To: Interesting Terminal**]("http://ubuntuforums.org/showthread.php?t=424104")

---

### Post by pbw on 2007-06-04
> **RedSquirrel said:**
> I don't like having to reach for a mouse more than necessary so I prefer to use my keyboard for most things.


I don't know if you'd tried it. But ion3's an excellent window manager for making the most out of your keyboard (and screen real estate). Really efficient. There's others of course, but that's my favourite for sure. Check it out for a try for a week if you haven't already.

---

### Post by Nekiruhs on 2007-06-04
Well, If you want something to do in the terminal, you could help me make it more userfriendly, but making aliases (macros in a sense) for commonly used commands!
My Thread is [http://ubuntuforums.org/showthread.php?t=464585]("http://ubuntuforums.org/showthread.php?t=464585")here

---

### Post by Tyke91 on 2007-06-04
i've found an easter egg in many install errors (dunno if it's an easter egg or not)

if something fails horribly, it will say at the end - this program does not have super cow powers.

---

### Post by RedSquirrel on 2007-06-04
> **Nekiruhs said:**
> Well, If you want something to do in the terminal, you could help me make it more userfriendly, but making aliases (macros in a sense) for commonly used commands!
My Thread is [http://ubuntuforums.org/showthread.php?t=464585](http://ubuntuforums.org/showthread.php?t=464585)here

Here's another one:

[Handy command-line aliases and tricks]("http://ubuntuforums.org/showthread.php?t=204382")

---

### Post by RedSquirrel on 2007-06-04
> **pbw said:**
> I don't know if you'd tried it. But ion3's an excellent window manager for making the most out of your keyboard (and screen real estate). Really efficient. There's others of course, but that's my favourite for sure. Check it out for a try for a week if you haven't already.

Yeah, I've heard of that. Haven't tried it yet. I still have the Fluxbox SVN addiction (which is not a bad thing!). 

Thanks for the reminder about ion. :)

---

### Post by Feba on 2007-06-04
> if something fails horribly, it will say at the end - this program does not have super cow powers.Do apt-get --help, and aptitude --help, this is part of the two things I mentioned in my OP.


Thanks for those links! telnet star wars is amazing.

---

### Post by pbw on 2007-06-04
> **RedSquirrel said:**
> Yeah, I've heard of that. Haven't tried it yet. I still have the Fluxbox SVN addiction (which is not a bad thing!). 

Thanks for the reminder about ion. :)

yeah no prob, i used to only run flux svn for quite awhile. Then found out about pekwm and ion3, pek being a happy medium between ion3 and flux imo. I haven't used flux in ages now, got the tiling window manager addiction (which isn't a bad thing either ;) ) might be time to revisit one of these days.

-- pbw

---

### Post by RedSquirrel on 2007-06-05
> **pbw said:**
> yeah no prob, i used to only run flux svn for quite awhile. Then found out about pekwm and ion3, pek being a happy medium between ion3 and flux imo. I haven't used flux in ages now, got the tiling window manager addiction (which isn't a bad thing either ;) ) might be time to revisit one of these days.

-- pbw

Nice to hear this from a former Fluxbox SVN user. :)

Your comments just might be the impetus for me to try out some new window managers. It's something that's been on my TO DO list for a while. I was considering dwm as my first candidate, but I'll try ion and others as well. :D

---

### Post by antini on 2007-06-06
> **pbw said:**
> Give aria2 a try, it's got some nice features such as segmented downloading. Here's a list of some features off the homepage:
I believe it's in universe.


yep, in universe. [http://packages.ubuntu.com/feisty/net/aria2](http://packages.ubuntu.com/feisty/net/aria2)

aria2 is great. metalink/torrent downloading is really convenient.

---

### Post by bigboy_pdb on 2007-06-10
I think to address those questions a person should think about where GUIs and command lines are most useful.

GUIs restrict input more than command lines, but this can be good. Since GUIs often use widgets such as check boxes, radio buttons, labels, text boxes, and buttons, a user knows exactly what he/she can do and is restricted to those things. Also, there are many cases where GUIs should usually be used over a command line for viewing/editing images or visual content. For example, viewing web content would be cumbersome from a command line, and images wouldn't be able to be viewed properly. In addition, GUIs can be used somewhat quickly when shortcut keys are used.

With that said, I will now state where a command line has its uses. Command lines are good for viewing and manipulating text. A shell allows you to perform tasks such as running programs, creating/removing files and directories, and redirecting input and output. There are a number of different shells where each have a different syntax and different benefits. A few of them are:
bash (Bourne-again shell), zsh (Z shell), csh (C shell), ksh (Korn shell), psh (Perl shell), scsh (Scheme shell)

Like in GUI programs, command line programs have a common interface. You type a command/program name followed by a space and everything else that is separated by spaces and not enclosed in quotes is an argument (or a parameter) that is used by the command/program. Also, many commands/programs have fewer input restrictions than GUIs (although this isn't always a good thing because it is easier to make mistakes when attempting to perform tasks.

NOTE: By command, I mean a program that is built into the shell and by program I mean an executable file that takes in input on the command line, performs some task, and (possibly) produces output.

The commands for a given shell are usually the same across different linux systems, meaning that you can move from system to system and still use the command line fairly easily (provided that the same programs are also on those systems). However, with Operating Systems with GUIs (such as KDE and Gnome), even though they might be somewhat similar, there can be drastic changes between programs that are meant for performing the same tasks.

From a security perspective, as you run more programs on a computer, your system has more bugs and more ways for people with ill intentions to gain access to your system. Thus, if you decide to run a web server where security is a necessity, you are better off using only a command line.

Command lines allow pattern matching to be used. An example of this would be 'rm *L*', which removes all files from the current directory that contain an uppercased letter L. Some programs allow a form of pattern matching known as 'regular expressions' to be used. Regular expressions allow you to match complicated text patterns. For example, the pattern 'bbb' matches all lines that have the letter b occurring three times in a row, the pattern '^d' matches all lines starting with the letter d, and the pattern 'c.b*' matches all lines that have a letter c followed by any character followed by zero or more occurrences of the letter b.

On the command line, you can use input/output redirection. For output redirection, you can use '>' (the greater than sign) to send text that would normally be printed on the screen to a file and you can use '|' (the pipe character) to send text that would normally printed on the screen to another program. For example, in 'ls > list.txt' the program 'ls' prints the contents of the current directory and '>' sends the text to a file called 'list.txt'. Another example is 'lsmod | grep dingle' in which 'lsmod' lists the modules that have been loaded and sends them to the program 'grep' and 'grep' prints all the lines matching the regular expression 'dingle' (meaning that it prints all lines that contain the character 'd' followed by the character 'i' followed by the character 'n', and so on). Basically, 'lsmod | grep dingle' prints all modules that have the word 'dingle' in it (regardless of whether or not it is contained within another word).

Due to pattern matching and the ability to pipe input from one program to another program, the command line can be quick and it can perform complex tasks (when used efficiently).

There are also other advantages to the command line:
* It can be used to compile programs.
* Some programs provide more information when run on command line (such as error messages or hints which can both be helpful for fixing a problem or performing search engine searches for a solution).
* A number of programs don't have GUIs. This isn't because someone couldn't create a GUI for it but because it doesn't always make sense to do it. For example, a frontend GUI for grep would make it either more complicated to use or less powerful.
* If there is a long command that you commonly use (such as a series of programs that are connected with pipes) you can use an 'alias' to make running the program/programs easier.
* You can't usually copy/manipulate text in the labels of a GUI, but all output on the screen of a program can be manipulated using a combination redirection and text editing programs.
* You can write your own programs using scripts.

Here's some other helpful information:
* I've seen some GUI programs that utilize regular expressions. However, a good number of command line programs have options for using them. Some powerful programs for performing text manipulation are 'grep', 'sed', and 'awk'.
* If you know the name of a shell program and need more information on it then you can use 'man program_name', where 'program_name' is the name of the program, to display more information on the program. Also, for some manual pages, near the end of the manual page there is a list of other programs that perform tasks that are similar to the program related to the current manual.
* Initially it might seem as though scripts can take longer than doing something manually but writing scripts gets easier with time, and as this happens you'll find that they become more and more useful.
* Some scripts might seem as though you'll only use them once, but if you reinstall the operating system you may need them again, or you might use them on someone else's computer.
* Some people prefer to use methods other than scripting for redundant tasks but the advantage of scripting with a shell like bash is that there's a good chance that if you move to another system, many of your scripts will still work

You can learn more about the linux command line, scripting for bash, and about other things related to linux by looking them up in search engine, but there are also some useful documents that can be found here:
[http://tldp.org/guides.html](http://tldp.org/guides.html)

---

### Post by bone43 on 2007-06-10
Maybe take a look at this guide...

[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

There are many more!! :)

---

### Post by bigboy_pdb on 2007-06-11
I forgot to mention a few things. Another reason why it's a good idea to keep scripts is because you may take pieces from an old script to create a new script, or if you haven't scripted in a long time, you may need them to refresh your memory.

---

### Post by Sasabune on 2007-06-17
I'm not sure if this is installed as default, but try "fortune".

---

