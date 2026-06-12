---
title: "How to install program not found by Synaptic?"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by paker on 2007-01-09
1) I need to install a program called nabi. Synaptic>Search gets an older version (nabi 0.15). The file name of the newer version is nabi-0.16.tar.gz. How do I install this program?

2) nabi needs another program (libhangul-0.0.4.tar.gz) to be installed. Synaptic>Search does not find the program. How do I install it?

3) I downloaded both programs to desktop from [http://www.kldp.net](http://www.kldp.net).

4) The website shows the following debian code for installation: sudo apt-get install nabi. 

Thanks for your help.

---

### Post by ajmorris on 2007-01-09
sudo apt-get install nabi is for getting it from your package manager.

Just do [PHP]tar -zxvf "filename"[/PHP]

Then follow the install instructions in the folder they get extracted to. Probably less INSTALL (from the shell) but could be something different like readme.

---

### Post by deadgobby on 2007-01-09
So what you need to do is open up your terminal window at Apps>Accessories>Terminal.
When you get the terminal window open. Copy and paste this command.

sudo aptitude install nabi

It will ask for a pass word. That pass word should be the same as when you logged into Ubie
 What is the difference between Apt-get and Aptitude. Simple. Apt-get get the software to install. If there is depends programs to make the program go. It will stop and say you need this installed to able for and bla bla bla.
 Aptitude will have the system look for depends and load them up.
Gobby

---

### Post by ajmorris on 2007-01-09
> **deadgobby said:**
> So what you need to do is open up your terminal window at Apps>Accessories>Terminal.
When you get the terminal window open. Copy and paste this command.

sudo aptitude install nabi

It will ask for a pass word. That pass word should be the same as when you logged into Ubie
 What is the difference between Apt-get and Aptitude. Simple. Apt-get get the software to install. If there is depends programs to make the program go. It will stop and say you need this installed to able for and bla bla bla.
 Aptitude will have the system look for depends and load them up.
Gobby

that only works if he has it in his repositories doesn't it?
He downloaded the tar.gz files and he wants to know how to compile and install them.

---

### Post by vf514 on 2007-01-09
It appears as though you would need to compile nabi. To do so, change your working directory to your installation site, and untar the package using

$ tar -xzvf nabi-0.16.tar.gz

A directory named "nabi-0.16" should be created; hence, you should issue:

$ cd nabi-0.16

To compile a program, one would run the following commands in most cases:

$ sudo ./configure
$ sudo make
$ sudo make install

It may be helpful to run:

$ sudo apt-get build-dep nabi

beforehand to install any dependencies that may be needed.

---

### Post by deadgobby on 2007-01-09
> **ajmorris said:**
> that only works if he has it in his repositories doesn't it?
He downloaded the tar.gz files and he wants to know how to compile and install them.

Why compile from source when it is in the repos?

---

### Post by vf514 on 2007-01-09
> **deadgobby said:**
> Why compile from source when it is in the repos?

He would like to run a newer version of the software (0.16), which is not currently available in the repositories.

[QUOTE=paker]Synaptic>Search gets an older version (nabi 0.15). The file name of the newer version is nabi-0.16.tar.gz.[/QUOTE]

---

### Post by deadgobby on 2007-01-09
OK fine try this
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
 Some times when you install older programs. You'll get Ubie to prompt you that there is a newer version to install. 
Just trying to help......
Gobby

---

