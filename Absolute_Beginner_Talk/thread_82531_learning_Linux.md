---
title: "learning Linux"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by Shaun32 on 2005-10-26
I have a very general Linux question and I didn't really know where I should post it.  Anyway, here goes:

I've been dabbling around in Linux for a few years now and played with 3 or 4 different distros.  However, I still feel like quite a noob.  I don't know how to compile things, and I don't have any handle on what is where in the filesystem.  Does anyone know of a website or some resource that I could learn the ins and outs like file system organization, possibly customization commands via terminal?  It seems like each time I ask a question about a problem I have, I have it answered with certain steps to get the job done, which is fine, but how do you learn to do these steps instinctively with using your knowledge of how the system works?  It seems like everyone just blabs about all these technical stuff, and it's not that I don't know terms or anything, it's just for instance I barely know how to compile something.  And I would have no clue how to make something from source.  I want to have some system knowledge about how linux works instead of you telling me the exact steps to get there.

Know what I'm talking about?  Hope someone does.

Thanks in advance,

Shaun

---

### Post by erikpiper on 2005-10-26
[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

That site might get you started.

---

### Post by Pathogenix on 2005-10-26
And for a quick desktop reference, I can recommend O' Reilly's Linux Cookbook which is full of short, snappy recipes for common tasks (including installation from source and debian packages) with just enough extraneous information to let you play around and break your machine again.

There's another Linux Cookbook out there which I haven't read, so stick with O'Reilly, or get the other one and tell us what you think.

---

### Post by SilentCacophony on 2005-10-26
That linuxcommand.org link above is a very good place to start.

One thing I have been doing any time I see shell commands that I don't know, is  to open up a terminal and get more info on them. For example, say you want to know more about the **mount** command:

**mount --help** will display usage info on the command. The **--help** option will work with most any well-written command.

**man mount** or **info mount** will display the manual page for the command, with detailed information.

Alternatively, if you're running Breezy, *System > Help* and select the 'Manual Pages' link, if you want an organized and more readable list of manual pages.

Another link that I've found useful is from the debian site:

[http://www.us.debian.org/doc/user-manuals#quick-reference](http://www.us.debian.org/doc/user-manuals#quick-reference)

Much of that info is relevant for ubuntu, since it's debian-based.

---

### Post by herrpoon on 2005-10-26
I'm like you - a noob...but I'm learning.  My advice is to get a book or two out from your library or get one from a friend or something, I find sitting down with a book, reading through some of the basics really helps when I come to try them for real :razz:

---

### Post by egraham23 on 2005-10-26
>  Does anyone know of a website or some resource that I could learn the ins and outs like file system organization, possibly customization commands via terminal?

[Linux-Tutorial.info]("http://www.linux-tutorial.info/modules.php?name=Tutorial&pageid=224") is a very good site which gives you a ground-up explanation of *NIX operating systems. When I decided that it was time to stop dipping in and out of Linux, I set up an old computer on my network with the base (i.e., non-graphical) Debian 3.1 system. I then used a Windows-based SSH client to tunnel into my Debian box and play around, using the above tutorial as my guide. When I felt comfortable enough to use Ubuntu on my main computer, I was used to working in terminal mode and was able to fix things without freaking out or relying on the GUI. For example, when I installed the wrong driver for my video card I was able to navigate in terminal mode to the directory where my X-settings were stored and edit the configuration file to set everything straight. 

Like most users today I come from a Windows background. Windows is great for making it easy to get started and then giving you time to learn what's under the hood (what little the OS will let you see, at least). I've found that, in Linux, it's better to know a bit about what's under the hood before you get behind the wheel. Ubuntu is the most user-friendly distro I've ever tried, but I still try to take things slowly and understand the fundamentals of what I want to do before I throw my hands in the air. This can be frustrating for Windows "power-users" who aren't able to port over much of their OS knowledge. This is also one of the greatest strengths of Linux: if you learn the OS from the most basic commands up, then you're able to exercise a lot more control over your computer in the long run.

In short: check out that tutorial, find a way to just "play around" with Linux until you're ready to jump in, and enjoy the learning curve!

---

### Post by Espy on 2005-10-26
I learned a lot about Linux by examining the 4000-entry Debian 2.2 package list, and figuring out what I would need for a running Debian system.

I don't recommend it.  And it didn't work.  But I learned a lot.

I learned even more by installing [Linux From Scratch](http://www.linuxfromscratch.org).  It's basically a Linux system in which you compile *everything* from its source code.  The book is very comprehensive, it's an excellent step-by-step guide to the inner workings of a basic Linux system, for beginners.  I didn't know how to compile source before that either, but afterwards, I was a master (well, OK, I was less inept).  The main guide only takes you up to a base system, but there are good resources for installing other essential programs, a GUI, and so on.  It's not really a usable system, since there's no package manager, but just fooling around with LFS on a spare gigabyte of hard drive space is worth it, even if you never actually boot into it.

I do recommend that.

SP

---

