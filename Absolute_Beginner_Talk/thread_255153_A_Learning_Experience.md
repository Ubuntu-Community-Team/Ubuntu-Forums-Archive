---
title: "A Learning Experience"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by Yirimyah on 2006-09-11
I started using Ubuntu full time a few days ago, and I've had quite a few issues with it. Unsupported hardware, et cetera. The problems were fixed after I spoke to one of my friends who sent me scripts and terminal instructions to deal with the problem. More recently, I've been trying to download games, and I really don't know what's going on. They refer me to "INSTALL", which is not a file in their directory. Synaptic is a *brilliant* application, but it doesn't cover everything, and I've got no idea of where to go from here.

By the way, I don't want specific tech support, which is why I've been vague. The reason for this thread is that it seems to me that Ubuntu assumes a lot of knowledge. It may be basic knowledge to you guys, but to someone with a background using Windows XP and programming in Visual Basic, I really haven't got the faintest. What I would like to know is, is there some kind of tutorial for Ubuntu? Terminal would obviously be the most useful app to have a tutorial for, but things like tarballs and installation are also problematic. Ubuntu doesn't even tell you what a shell script is. I don't think that anyone is going to be fully satisfied with what they can get from Synaptic - and I think many newbies are unwilling to come here and whine about every little problem, especially when we're going to be given lines of terminal code that we don't understand. Help us help ourselves.

Thank you.

---

### Post by Requiem on 2006-09-11
The current situation is that comercial application support is lagging and it's not Ubuntu's fault.

We make a lot of effort to run comercial applications in Ubuntu, Ubuntu is already doing more than its part of the deal (providing the plataform) but if your favorite game doesn't give you a nice installer or a synaptic package its their fault, complain to them.

When you are ready for "specific tech support" we will try to help you here. Also have youtried looking in the wiki? It full of tutorials and how-tos

---

### Post by Mimsy on 2006-09-11
I have two problems with the wiki.

1. It assumes knowledge that I don't yet have.
2. If it doesn't, I end up copying and pasting in commands I don't understand, who makes Ubuntu do things I don't understand, for reasons I don't understand.

In the first case, the tutorial is useless to me. In the second, while the problem is solved, I have not learned anything, and the next time I have a problem that is almost but not quite the same as the first, I have to go find another wiki article, because I still have no idea what I'm doing.

Something along the lines of "Ubuntu for Dummies - Five Easy Ways to Learn the Basics" would be nice. If there already is such a thing, a link to it on the Ubuntu front page is probably a good idea.

/Mimsy

---

### Post by aysiu on 2006-09-11
> **Yirimyah said:**
> I don't think that anyone is going to be fully satisfied with what they can get from Synaptic I may be the lone exception, but I'm actually more than satisfied with what I can get through Synaptic. In fact, all the software I use is from the repositories.

---

### Post by bodhi.zazen on 2006-09-11
> **Mimsy said:**
> Something along the lines of "Ubuntu for Dummies - Five Easy Ways to Learn the Basics" would be nice. If there already is such a thing, a link to it on the Ubuntu front page is probably a good idea./Mimsy

There are several. Try starting with this one:
[ Unofficial Ubuntu 6.06 (Dapper Drake) Linux Starter Guide](http://ubuntuguide.org/wiki/Dapper)

---

### Post by Mimsy on 2006-09-11
Oh, that's a biiiiiig article. Neat. I hadn't quite made it past the articles on ubuntu.com yet, but that wiki looks a lot more like what I was looking for, not to mention that I now know where to start my reading. That's going to help.

Thanks! :-)

/Mimsy

---

### Post by 3rdalbum on 2006-09-11
I know it's not mentioned much, but there is an on-line manual (on-line, not "online") for each command.

For instance, with the command "sudo chmod +x script.sh":

Typing *man sudo* at the terminal tells you that the *sudo* command allows you to temporarily run a program with full privileges, by specifying the program after the command.

Then, if you type *man chmod*, that tells you that the command allows you to change the permissions of a file. It also goes through, in detail, what all the different flags do, so you can work out what the +x bit does. (it adds the "execute" permission to the specified file).

*man* is such a good command because it often helps me to help myself. If you do a sudo apt-get install info, you can also use the Info command (i.e. *info chmod*) which sometimes just echos the man pages, and sometimes has in-depth operating manuals. (for instance, if you install gtkdialog, the info pages have quite a good tutorial on how to use the package).

---

### Post by xyz on 2006-09-11
This one's nice,reassuring to start with:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

> and I think many newbies are unwilling to come here and whine about every little problem, especially when we're going to be given lines of terminal code that we don't understand. Help us help ourselves.

If you REALLY don't know anything about GNU/Linux, any tutorials may sound to you like Medieval Chinese! I experienced it, that's for sure.
You need to be willing to take some time and things will be sinking in little by little. 

Hang in there! And good luck, patience!

---

### Post by Yirimyah on 2006-09-11
Thanks, guys. Things like that Starter Guide are very useful.

---

### Post by Mimsy on 2006-09-11
As I was skimming through it over my breakfast this morning, I realised that solutions to a lot of the problems that I have wrestled with to the point of wanting to dropkick the laptop (as in dropping it from about chest height and kicking it punt-style) are right in that wikipedia article.

How very embarrassing... :oops: I feel a bit stupid now.

So thanks again for posting these things. It's a big help.

/Mimsy

---

### Post by richbarna on 2006-09-11
> **3rdalbum said:**
> I know it's not mentioned much, but there is an on-line manual (on-line, not "online") for each command.

For instance, with the command "sudo chmod +x script.sh":

Typing *man sudo* at the terminal tells you that the *sudo* command allows you to temporarily run a program with full privileges, by specifying the program after the command.

Then, if you type *man chmod*, that tells you that the command allows you to change the permissions of a file. It also goes through, in detail, what all the different flags do, so you can work out what the +x bit does. (it adds the "execute" permission to the specified file).

*man* is such a good command because it often helps me to help myself. If you do a sudo apt-get install info, you can also use the Info command (i.e. *info chmod*) which sometimes just echos the man pages, and sometimes has in-depth operating manuals. (for instance, if you install gtkdialog, the info pages have quite a good tutorial on how to use the package).

One thing for the new users, when you have finished reading the man file.

Type ":q" to quit, it's better than shutting down the terminal and then starting it up again to read another man page ;)

---

### Post by Mimsy on 2006-09-11
Wow. Talk about a wake-up call.

My SO's computer decided to only connect to the internet when it wants to. This bothers my SO a lot, and since he hates messing with these things and in fact hates computers in general because it's so much work to keep them working, he asked me to fix it.

An hour later I am finally done downloading all the cleaning tools, and installing them, so I can boot WinXP into safe mode and start scanning.

Learning Ubuntu suddenly doesn't seem that time-consuming after all. Freaking Windows. :rolleyes: 

/Mimsy

---

### Post by blackened on 2006-09-11
When I was at university in the mid 90s a Unix intro class was required for all 1st year students. I think most community colleges still offer these classes, and it would probably be well worth your time. You may also check if there is a Linux User Group (LUG) in your area as they can be an invaluable resource to new users.

---

