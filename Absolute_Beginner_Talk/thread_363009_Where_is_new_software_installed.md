---
title: "Where is new software installed?"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Dejvid on 2007-02-16
Greetings...

When I install new software in Ubuntu Linux, in what directory is it installed?  How does the software "know" where to go?  

I installed Dapper Drake several days ago and have been practicing installing software using Synaptic, and I'd like to try installing some software from source code.  But it seems from what I read that most installations from source code are done starting with the source code file on the Desktop.  So how does the installed program wind up in the right place?

I'm trying to transistion from M!cr0S0ft products to an open source operating system and software.  So far I'm really pleased with what I've seen of Ubuntu.  I'm looking forward to learning more about it.

Thanks,

Dave

---

### Post by taurus on 2007-02-16
Apps that you install with synaptic/apt-get/aptitude will get installed in /usr/bin and it is in your path so you can execute anything in there from anywhere. 

And if you install something from source, then it is more likely it will get installed to /usr/local/bin and if /usr/local/bin is in your path, then you can run it anywhere you want to.  However, you can have the source to install somewhere else too by changing the PREFIX when you run the ./configure.

---

### Post by highneko on 2007-02-16
> **Dejvid said:**
> When I install new software in Ubuntu Linux, in what directory is it installed?  How does the software "know" where to go?

A package is like a tarbomb or something that explains where to put the precompiled files I think. If you're wanting to know where the files go when the package is installed you can type:
dpkg -L packagename

---

### Post by spoot on 2007-02-16
> **Dejvid said:**
> Greetings...

When I install new software in Ubuntu Linux, in what directory is it installed?  How does the software "know" where to go?  

I installed Dapper Drake several days ago and have been practicing installing software using Synaptic, and I'd like to try installing some software from source code.  But it seems from what I read that most installations from source code are done starting with the source code file on the Desktop.  So how does the installed program wind up in the right place?

I'm trying to transistion from M!cr0S0ft products to an open source operating system and software.  So far I'm really pleased with what I've seen of Ubuntu.  I'm looking forward to learning more about it.

Thanks,

Dave
Since you mentioned using Synaptic, you can see where the files of a specific package went by right clicking on it and selecting properties, after that select the "installed files" tab.

Downloaded package files (for example when you install new stuff in Synaptic) go into /var/cache/apt/archives/ .

When you compile programs from source you usually extract the downloaded file to somewhere in your home folder (Desktop is one example). The "./configure" and "make" commands, that you probably used to compile the program, only do things to the path you extracted the source code to. The last step, "make install", moves the compiled binaries to the proper locations in your filesystem so you can properly start it.

---

### Post by NeoGreen on 2007-02-16
Sorry to jump on this post but if I download an application from the internet to my desktop how do I install it?:confused:

---

### Post by taurus on 2007-02-16
What is the exact name of that program?

Section 4:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Maestro23 on 2007-02-16
Another How-To install link: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

---

### Post by NeoGreen on 2007-02-17
Outstanding links, thanks for the help.

---

