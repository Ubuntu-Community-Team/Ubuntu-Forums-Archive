---
title: "Very basic questions about command line."
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by Layman on 2005-12-04
This is going to sound incredibly stupid, but I have been searching for absolutely ages on this forum and google and can't find some REALLY basic information.

E.g. a question is always answered by "go to command line and type xxxxx ".

My problem is that I don't even know what the command line is, or how to go get to it! Second, I need to find an absolute idiots guide to Ubuntu which explains what repositories are as well as what words like root mean. Seriously, the Ubuntu FAQ guide thing skips out the really basic explanations of terms.

You can stop laughing now :razz:

---

### Post by Glass Casket on 2005-12-04
I'm pretty sure that what they mean by the command line is the Terminal.

---

### Post by Layman on 2005-12-04
What is the terminal and how do I access it?

---

### Post by atoponce on 2005-12-04
The command line is similar to DOS back in The Day.  In most Linux circles, however, the command line is commonly referred to as the terminal or the shell.  In Ubuntu, to pull up the terminal, just click on the Gnome menu at the top left of the desktop.  Applications -> Accessories -> Terminal.  From there, you will be able to launch all the commands that frequent this foum.

To get a good grasp on the commands, I would grab [Teach yourself UNIX in 24 Hours]("http://www.amazon.com/gp/product/0672321270/qid=1133710103/sr=8-3/ref=pd_bbs_3/102-5668445-8472915?n=507846&s=books&v=glance") from a bookstore or Amazon.  It's an excellent book, and really helped me understand the terminal and moving around a UNIX system.  Everything in there is 100% compatible with Linux, and it is written for the complete newbie.

---

### Post by Kvark on 2005-12-04
It is much easier to say "type: some command" then to say "click on that thing up there and then on this thing that looks odd". Thats why people always give answers for the command line terminal instead of for the graphical user interface.

Check out [http://linuxcommand.org/](http://linuxcommand.org/) to learn a bit about the terminal.

---

### Post by ekarni on 2005-12-04
The command line (aka terminal or shell) is a way to interact directly with the system, without using a graphical interface.  It can be faster to use (once you learn a few key commands).  It's also much easier to say "type xyz on the command line" than give instructions for doing it graphically.  

To answer your other questions, I looked and you're right, there is no definition in any obvious spot.  Best glossary I could find was this:
[Ubuntu Glossary]("http://www.ubuntulinux.org/support/documentation/glossary/document_view")  

Here are some quick definitions to get you going:
Repositories are web servers where software packages for Ubuntu are kept.  You connect to them (graphically) using a program called Synaptic (System -> Administration -> Synaptic).  Synaptic lets you search for the programs you want and handles downloading and installing them.

"Root" has a couple different meanings.  Concerning file structures, it refers to the highest (maybe lowest makes more sense!) level.  Say your home directory is /usr/home/joeblow.  Root is that first "/"  above usr.  

When used in terms of users, the "root" user is like the "administrator" on Windows.  Like Windows, Linux assigns "permissions" to files, saying who (user, a group, or everyone) can do what (read, write, execute) them. The root user can do ANYTHING.  Ubuntu doesn't have a roor user by default.  Some things (mostly installing programs or working on special system files) need this special power though.  You can tell this is happening when you get prompted for a password -- just type your user password.  On the command line, putting the command "sudo" before the command you want to execute will have the same effect.

Please feel free to ask away!  Everyone reading these forums was at your stage of the game once too.  There's no shame in asking, we've all been in your shoes (and still are most of the time!)

---

### Post by aysiu on 2005-12-04
If you have the latest version of Ubuntu (5.10), it's in Applications > Accessories > Terminal

If you have the previous version (5.04), it's in Applications > System Tools  > Terminal

---

### Post by atoponce on 2005-12-04
[quote=aysiu]If you have the latest version of Ubuntu (5.10), it's in Applications > Accessories > Terminal

If you have the previous version (5.04), it's in Applications > System Tools  > Terminal[/quote]

Good call!  I hadn't realized that the menus were different between releases.

---

### Post by aysiu on 2005-12-04
[QUOTE=atoponce]Good call!  I hadn't realized that the menus were different between releases.[/QUOTE] Personally, I think it's annoying that they moved it. It's just another thing I have to differentiate for users (if you use x, then y; if you use a, then b). The change seemed unnecessary. Nevertheless, it is there.

---

### Post by TeeAhr1 on 2005-12-04
Another tip I got from a wise sage last night:
If you're looking for help/definition on a command, from the command line, there are three different ways to do it.

Large: **info** <command>
Complete info you can study to learn a command.

Medium: **man** <command>
A general reminder to refresh your memory of a command you know kinda how to use.

Small: <command> **--help**
An even shorter reminder for when you master the command but forgot which exact letters/words to use.

Example: Someone told you to **tar xjf Firefox_1.5.tar.bz2**  You don't know what that means, do you?  That's okay, the help files are here for you.  All commands go like this: [command] [modifiers] [what we're doing the command to].

So you go into the terminal, type **man tar**.  A help file will appear telling you what the "tar" command is, what you do with it, and what that "xjf" stuff means too (remember, those are modifiers to the command, you're telling it that you want it to execute the "tar" command in a specific way).

Didn't find enough information?  You're golden.  Type **info tar**.  This will bring up the "everything you ever wanted to know about "tar" but were afraid to ask" help file.

Three weeks down the road, maybe you're "tar"ing something else.  You remember what "tar" is, and for the most part what it does, but maybe you just don't remember the exact syntax the command is supposed to be in.  That's where **tar --help** comes in.  It's just the barebones info, it'll tell you stuff like what the "xjf" means, and what your other options there are, and how to write the command so the terminal will understand it.

Go try it yourself, it's a godsend!

Some helpful links for learning the terminal:
[http://www.linuxcommand.org/](http://www.linuxcommand.org/) Learning The Shell
[http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal) Linux Terminal: A Beginner's Bash
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html) Bash Guide For Beginners
[http://www.ss64.com/bash/](http://www.ss64.com/bash/) Bash Commands A-Z
[http://linuxcommand.org/index.php](http://linuxcommand.org/index.php) Learning the Shell

*Thanks to 23meg for the links, Kvark for the help files mini-tutorial.*

---

### Post by wyohermit on 2005-12-04
[QUOTE=Layman]This is going to sound incredibly stupid, but I have been searching for absolutely ages on this forum and google and can't find some REALLY basic information.

Check out this thread I thought it had a lot of good basics
 Terminal for Beginners
[http://ubuntuforums.org/showthread.php?t=73885&highlight=basic+command+line](http://ubuntuforums.org/showthread.php?t=73885&highlight=basic+command+line)

Ken

---

