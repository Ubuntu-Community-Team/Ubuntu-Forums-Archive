---
title: "installing drivers, programs, ect."
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by pesach on 2007-03-13
I have a big problem with Ubuntu that I cannot just double click on the package that  downloaded form the internet and have Ubuntu install it for me.  Instead, I have to go through a whole list of steps, including writing code, finding locations, and a whole another slew of things..
I am not against doing all this stuff, but the problem is, I do not know what I am supposed to do.  Can some one please tell me what I should do in general when installin g a program , driver, or anything like that.
(please answer my question as if speaking to someone who knows nothing abotu code, ubuntu, or anything.  All I know is how to open terminal.)
thanks!

---

### Post by Vajra Vrtti on 2007-03-13
I think this is a good guide: [COLOR="Blue"]http://cutlersoftware.com/ubuntuinstall[/COLOR]
Post again if you still have doubts after reading it.

---

### Post by raja on 2007-03-13
About 99% of applications you need will be in the repositories. Installing them is easier than downloading something and double-clicking, believe me. 
Let us say you want to burn cds. The graphical way of going about it is to open synaptic (System --> Administration --> Synaptic package manager). Click on search and type 'cd burn'. You will get a list of applications that are available. Just select what you want to install and the manager will do it for you. 
While the terminal may look scary at first, it is even easier to use. To do the same thing from the terminal, I would type ```
apt-cache search 'cd burn'
sudo apt-get install <app name>
```.

---

### Post by bapoumba on 2007-03-14
Thread moved to "Absolute Beginner Talk" forum.

You can read:
[http://psychocats.net/ubuntu/installingsoftware]("http://psychocats.net/ubuntu/installingsoftware")
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

