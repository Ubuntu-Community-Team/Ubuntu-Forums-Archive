---
title: "Process of installing software?"
date: 2005-10-24
forum: Absolute Beginner Talk
---

### Post by arsbadmojo on 2005-10-24
For those of us who have lived in a Windows world, the process of installing software has been largely standardized. Unzip a package, extract it to a temp location, find "setup.exe", install to C:\Program Files\...etc.

Is there such a 'process' in the linux world?

I was looking for a wireless intrusion program - something like AirSnare for Windows, and saw kismet may work. So I downloaded a package and it is on my desktop. Double-clicking it seems to be doing the equivalent of a Windows winzip operation, and I have the option to extract the contents.

Does it matter where in the filesystem that I extract these files? 

Once I do, what next? I know some steps won't have Windows equivalents - that's fine - but what I'm looking for here is not for someone to say "Type blah blah blah..." but rather WHY you do something, WHY you should extract files to a certain location...in other words, I'd like to try to learn something rather than merely follow directions.

Thanks!

---

### Post by az on 2005-10-24
In the open source world, you can download, compile and install anything you want, if you have access to the source code.

Linux distributions are mostly binary distributions.  Ubuntu has compiled all the 13000+ applications in the universe repository for you.  You just have to enable the universe repository in synaptic, refresh and search for your package.


If you want a newer version of a package, install the build-essential package and compile it yourself.

---

### Post by mostwanted on 2005-10-24
That depends what kind of package you've downloaded:

[http://ubuntuforums.org/showthread.php?t=80916](http://ubuntuforums.org/showthread.php?t=80916)

---

### Post by arsbadmojo on 2005-10-24
[QUOTE=azz]Linux distributions are mostly binary distributions. [/QUOTE]

As opposed to tertiary distributions? I don't know what that means "binary distributions". I'm going to take a guess that you mean as opposed to source code that I would need to compile myself?

> 
Ubuntu has compiled all the 13000+ applications in the universe repository for you.  You just have to enable the universe repository in synaptic, refresh and search for your package.

All the 13000+ applications? You mean there are 13000+ programs ready to install somewhere in an on-line repository called synaptic? I guess that's cool. Is kismet there?


> 
If you want a newer version of a package, install the build-essential package and compile it yourself.


Whut? What does build-essential mean?

---

### Post by xmastree on 2005-10-24
[QUOTE=arsbadmojo]WHY you should extract files to a certain location...[/QUOTE]To answer your question as to **where** to install stuff, I suggest you open Synaptic, pick a package, and look at the properties. You will see where its files are located. Typically, a program will have a binary, (the executable, equivalent to the .exe in windows) documentation, configuration files etc.
The executable will go in /usr/bin whereas the documentation will go in /usr/share/doc manual pages will be in /usr/share/man and so on.
In windows, one program tends to live in its own directory. In linux it's spread out through the filesystem. One advantage of this is that all the executables are in one directory (/usr/bin) and are therefore on the path. you can run **any** program from a terminal by just typing its name.

For applications not in the official repositories, you should look for a .deb package. Failing that, get a .rpm and use **alien** to convert it.
Where you actually do this is irrelevant, the package contains the intended locations for all the files within it.

---

### Post by arsbadmojo on 2005-10-24
From the linked thread - some useful info, but also some confusing bits:

> .tar is a non-compression archive format. tar.gz is tar with gzip compression applied to it. Normally these packages contain source code, so yes you'll have to compile it. 

This was a very informative answer, but still a bit vague - "Normally these packages contain source code..." well, OK - how do you know? How can you tell if it needs to be compiled?

> Fortunately that's dead simple. First you unzip the contents, go to the folder of the file and run

Code:
$ tar -zxvf mypackage.tar.gz


It would help greatly to break that command up a bit. tar - starts the extraction, but what does -zvvf mean???

---

### Post by xmastree on 2005-10-24
[QUOTE=arsbadmojo]Is kismet there?[/QUOTE]Yes.

But Synaptic isn't the repository, it's the graphical program you use to access and install the programs. Find it under **System > Administration**

---

### Post by arsbadmojo on 2005-10-24
[QUOTE=xmastree]To answer your question as to **where** to install stuff, I suggest you open Synaptic, pick a package, and look at the properties. You will see where its files are located. Typically, a program will have a binary, (the executable, equivalent to the .exe in windows) documentation, configuration files etc.
The executable will go in /usr/bin whereas the documentation will go in /usr/share/doc manual pages will be in /usr/share/man and so on.
In windows, one program tends to live in its own directory. In linux it's spread out through the filesystem. One advantage of this is that all the executables are in one directory (/usr/bin) and are therefore on the path. you can fun **any** program from a terminal by just typing its name.
[/QUOTE]

Thank you, this is very informative and helpful.

> For applications not in the official repositories, you should look for a .deb package. Failing that, get a .rpm and use **alien** to convert it.
Where you actually do this is irrelevant, the package contains the intended locations for all the files within it.

Does .deb stand for Debian? .rpm stands for Red Hat Package Manager doesn't it? This "alien" you mention - converts .rpm to .deb? alien would already be installed? I didn't see it on my applications menu, but I haven't tried it from a command line.

---

### Post by arsbadmojo on 2005-10-24
[QUOTE=xmastree]Yes.

But Synaptic isn't the repository, it's the graphical program you use to access and install the programs. Find it under **System > Administration**[/QUOTE]

Oh, I see, so there is a software repository with thousands of applications, and you access this with a GUI utility called Synaptic?

---

### Post by xmastree on 2005-10-24
[QUOTE=arsbadmojo]Thank you, this is very informative and helpful.[/quote]You're welcome.
> Does .deb stand for Debian? 
This "alien" you mention - converts .rpm to .deb? 
alien would already be installed?Yes, yes and yes.
Open a terminal and type alien. Withot including a filename to work on, it will return the help file.

---

### Post by xmastree on 2005-10-24
[QUOTE=arsbadmojo]Oh, I see, so there is a software repository with thousands of applications, and you access this with a GUI utility called Synaptic?[/QUOTE]
you're getting there. Soon you'll have an epiphany (and I don't mean the browser) that ubuntu linux is the best thing in the world, ever...

Read [this]("http://www.ubuntuguide.org/#extrarepositories"), follow the instructions then open synaptic from the System menu and search for kismet.

You may be pleasantly surprised...

What version of ubuntu are you running? That guide is for 5.04 so the repository info is for that version only.

---

### Post by Wolki on 2005-10-24
[QUOTE=arsbadmojo]
This was a very informative answer, but still a bit vague - "Normally these packages contain source code..." well, OK - how do you know? How can you tell if it needs to be compiled?[/quote]

Usually, there's a file called INSTALL, and one called README. They contain useful information regarding installation and the things you need for it.

> It would help greatly to break that command up a bit. tar - starts the extraction, but what does -zvvf mean???

z means the tar file is gZipped
x means that you tell tar to extract the files
v means that the output of the program is Verbose (ie it tells you more about what it dies)
f means that you specify a file to extract from

"man <program name>" is a useful command if you want to know more about what arguments and options a certain application takes. The so-called man pages  can be a little bit confusing and are often very long; if you have specific questions you can of course also ask in forums or irc channels.

---

### Post by arsbadmojo on 2005-10-24
[QUOTE=xmastree]
What version of ubuntu are you running? That guide is for 5.04 so the repository info is for that version only.[/QUOTE]

5.10 I believe.

Thank you for your help.

---

### Post by Wolki on 2005-10-24
Information on how to add additional repositories on any ubuntu version can be found here: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by herrpoon on 2005-10-24
Been reading through this thread and even though I've been using ubuntu for a month or so now, found it really helpful, perhaps it can be cleared up a bit and made into a sticky or something.  I think if every newcomer to ubuntu  read it, it'd help them enormously, I remember when I first started, I had no idea about synaptic and tried to compile everything myself!

---

### Post by arsbadmojo on 2005-10-24
[QUOTE=Wolki]
z means the tar file is gZipped
x means that you tell tar to extract the files
v means that the output of the program is Verbose (ie it tells you more about what it dies)
f means that you specify a file to extract from
[/QUOTE]

This is very helpful. Every download I've seen so far has been both .tar and .gzipped, so I'm thinking this would be a pretty 'standard' set of commands to learn.

---

### Post by xmastree on 2005-10-24
[QUOTE=arsbadmojo]5.10 I believe.[/QUOTE]In that case, you need to uncomment the commented-out repositories in your /etc/apt/sources.list rather than copying the one from the link I gave you.

---

### Post by aysiu on 2005-10-24
[QUOTE=arsbadmojo]Oh, I see, so there is a software repository with thousands of applications, and you access this with a GUI utility called Synaptic?[/QUOTE] If you want a step-by-step graphical tutorial on how this works, see the second link in my sig.

---

### Post by mostwanted on 2005-10-24
> **arsbadmojo]This was a very informative answer, but still a bit vague - "Normally these packages contain source code..." well, OK - how do you know? How can you tell if it needs to be compiled?[/QUOTE]

You don't have to know that, the make program consults the makefile inside the directory that appears after untaring your tar.gz. If it needs to call a compiler, it will do so magically by itself  said:**
> It would help greatly to break that command up a bit. tar - starts the extraction, but what does -zvvf mean???

$ man tar

This should explain basic tar usage. man is good command to know if you don't understand what a specific command does.

---

