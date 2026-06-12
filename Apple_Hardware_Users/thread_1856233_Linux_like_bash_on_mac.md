---
title: "Linux like bash on mac?"
date: 2011-10-07
forum: Apple Hardware Users
---

### Post by kaizo2560 on 2011-10-07
Hi I have been using kubuntu for the last 5 years and was told recently by my boss that I will have to use a mac for my new job. 

The problem is that when I went to the terminal and typed in commands like firefox, safari etc... the command was not found. Making the access to the programs rather difficult.

Other commands like ls, man, cd etc... seems to work.

It seems illogical to do this and have no idea why they have done this but is there any way of making the terminal in mac more like the one in linux?

They are both bash and there is no reason why it should not work.

---

### Post by pindar on 2011-10-08
> **kaizo2560 said:**
> Hi I have been using kubuntu for the last 5 years and was told recently by my boss that I will have to use a mac for my new job. 

The problem is that when I went to the terminal and typed in commands like firefox, safari etc... the command was not found. Making the access to the programs rather difficult.

Other commands like ls, man, cd etc... seems to work.

It seems illogical to do this and have no idea why they have done this but is there any way of making the terminal in mac more like the one in linux?

They are both bash and there is no reason why it should not work.
It has nothing to do with bash but with the way in which gui programs are started from the shell in OS X. In a terminal, type
```
open -a Firefox
```
to open a program.

---

### Post by kaizo2560 on 2011-10-08
Hi thank you for your reply 

That solves most of the problems. For the benefit of my (and future reader's) reference please let me know:

1) The reasoning behind this. Is the commands different out of a cleaver reason that is beyond my perception?

2) Is there any other common difference like the one above between linux terminal commands and mac terminal commands?

Again thanks for your reply

---

### Post by pindar on 2011-10-09
I think you're misunderstanding the role of the shell. OS X is a different operating system. If you open a shell in Solaris, or one of the BSDs, you'll find that a number of commands are different and/or work differently, even though you're using a bash shell. Even between linux systems, there are differences (e.g., the way system init scripts are executed and modified); if you invoke apt-get on Fedora, you will be disappointed. If you want Ubuntu-like syntax in the shell, stick to Ubuntu.

---

### Post by kaizo2560 on 2011-10-09
Hi thanks the penny dropped.

I think I will go ahead and find a mac command tutorial to familiarise myself with the mac shell.

Again thanks for all your help

---

### Post by robvas on 2011-10-09
> **kaizo2560 said:**
> The problem is that when I went to the terminal and typed in commands like firefox, safari etc... the command was not found. Making the access to the programs rather difficult.

Other commands like ls, man, cd etc... seems to work.

It seems illogical to do this and have no idea why they have done this but is there any way of making the terminal in mac more like the one in linux?

They are both bash and there is no reason why it should not work.

They both run bash, but think about this:

Ubuntu 11 uses bash version **4.2.8**
OS X Snow Leopard uses bash version **3.2.48**

Also remember that Mac OS X is BSD-based, not Linux. They are very different, but have a lot in common.

Why can't you simply type a command like 'firefox'? Many reasons.

In Linux, if you enter 'firefox', the /usr/sbin/firefox binary is in your path and it will load. But on the Mac, that isn't where 'firefox' is located. It is stored in /Applications/Firefox.app

What is .app? It's an *Application bundle*, which is basically a folder that contains not just the program itself but all the files associated with it. When you double-click the programs icon (which is really the .app file), it runs Firefox.app/Contents/MacOS/firefox (actually, firefox-bin, but that's another story)

Like pindar says, you can use the 'open -a Firefox' command to open an application on the Mac. Every UNIX-like operating system is very different, from Solaris to Linux to Mac OS X to FreeBSD.

---

### Post by webfiend on 2011-10-14
You can make your system a little more familiar with the help of [MacPorts]("http://www.macports.org/"). No, it's not exactly the same, but there are fresh versions of lots of familiar software. For example, the MacPorts bash package is at version 4.2.

There is a similar project called [Homebrew ]("http://mxcl.github.com/homebrew/")which also works very well. Its only shortcomings are that it does not have quite as many packages and it is not as well-organized as MacPorts.

MacPorts works well enough that I've been comfortable with using the home iMac as a dev workstation for a few years. Of course, neither Homebrew nor MacPorts are Linux, so I have Ubuntu on the MacBook Pro. :)

One tweak that made the OS X shell even more comfortable for me was setting up coreutils for the brightly colored ls output I'm so accustomed to. [This Apple Support Community post]("https://discussions.apple.com/thread/1924086?start=0&tstart=0") provides good tips.

---

