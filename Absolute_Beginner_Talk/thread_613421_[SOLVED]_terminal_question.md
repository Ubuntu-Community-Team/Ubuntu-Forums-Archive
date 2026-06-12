---
title: "[SOLVED] terminal question"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by NWAmama on 2007-11-14
Hi, I've been using Ubuntu for about 1.5 years but I am recently new to navigating the terminal.  I've been reading the sticky post on the Complete Guide to Install...and Learning the shell Lessons 1, 2 & 3.  (just installed Ubuntu 7.10)  I have a couple questions...

In the Complete Guide, it says that my terminal should say:  username@hostmachine:~$  My terminal says  username@username-desktop~$
Is this correct?  I'm thinking the -desktop part should not be there but I cannot make it go away.  When I try cd .. it says the same thing.  I feel like I am missing something that is obvious or maybe not? :confused: 

My real issue is that I am trying to install the flash plug in to my browser.  I have tried each download option and tried a couple different ways access it.  I do log in as root user (sudo) before trying their instructions.  It keeps saying that it cannot find the install file that I am typing in.    I have a feeling that I am not navigating to the correct place-the desktop.  Visually, the file is sitting on my desktop so I know it it there and am confused as to why it isn't recognizing it.  Is it technically hidden?  

So when I do an ls on my user acct, it shows several folders: music documents desktop etc.  I realize these are case sensitive so when I try to navigate forward using cd ~Desktop or whatever, it says there is no file by that name.  I'm pretty confused and would love to have some light shed on my situation. 

Thanks!
NWAmama

---

### Post by Duck2006 on 2007-11-14
Did you meen this?

> 
duck@duck-desktop:~$ cd ~/Desktop
duck@duck-desktop:~/Desktop$ 


---

### Post by Partyboi2 on 2007-11-14
> $  My terminal says  username@username-desktop~$
Mine says:
> karl@karl-desktop:~$

---

### Post by Inxsible on 2007-11-14
the hostmachine is the name of the machine, which in your case is username-desktop.

There was an option where you could name the machine. By default, it is always the rootuser-dekstop or rootuser-laptop depending on what kind of machine you have. But you can also change it if you like.

---

### Post by Dr Small on 2007-11-14
A little more simplified understanding:

username@hostmachine:~$

username = the user logged in at the terminal; This would be your username.
hostmachine = the hostname of the system. This can be changed with 'sudo hostname newhostname', editing /etc/hostname, or under network.

: = a seperator
~ = Home folder 
$ = the dollar sign symbol, meaning the end of all of that, and the beginning where you begin your commands.

I know there is a website around here somewhere explaining all of this, and I'll have to find it and post it for you.

Dr Small

---

### Post by Paul820 on 2007-11-14
I think it is supposed to be like that, mine says
> paul@paul-laptop:~$

To find out where you are you can type
> pwd
Which means 'print working directory', the directory you are in.

---

### Post by jordank on 2007-11-14
perfectly normal. name-desktop is just the NAME of your machine.
you're getting two types of desktops confused.
a) there is the workspace desktop, where you can open windows and have things open on your desktop on your computer.
b) You have a desk in your home. Your computer probably has a tower and a monitor. It sits on your desk, hence it's called a desktop.
if you were on a laptop, it would read
username-laptop

don't worry, you're in the clear.

---

### Post by NWAmama on 2007-11-14
To Duck & Partyboi,

Yes!  I see now that it is correct but also that I was leaving out the / in /Desktop.  I'm off to retry.  I knew it was something small that I was leaving out.  Will let you know if it doesn't work.  Thank you.

NWAmama.

---

### Post by Partyboi2 on 2007-11-14
To get to your desktop try:
```
cd /home/*username*/Desktop 
```* username change to what your username is
That will get you to the desktop file, Then:
```
ls
```to check you are where you are meant to be.

make sure you use a captial D for desktop

---

### Post by Duck2006 on 2007-11-14
[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

---

### Post by NWAmama on 2007-11-14
Ok..I'm now moving this in the direction of the install Flash question..

Here's what I did....

base@base-desktop:/$ cd ~/Desktop
base@base-desktop:~/Desktop$ ls
adobe-release-i386-1.0-1.noarch.rpm
base@base-desktop:~/Desktop$ sudo # rpm -Uvh <rpm_package_file>
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
base@base-desktop:~/Desktop$ 

What's next?

---

### Post by NWAmama on 2007-11-14
"b) You have a desk in your home. Your computer probably has a tower and a monitor. It sits on your desk, hence it's called a desktop.
if you were on a laptop, it would read"


This was helpful, thank you ;)

---

### Post by arashiko28 on 2007-11-14
You got too confused. you're using a desktop computer, not a laptop, therefore it is username@session-hostmachine:

If it's a laptop it changes desktop to laptop. you have to do cd Desktop to get to your desktop, to make sure the file is there write ls, you'll see all that you have on it. I'm sure you know the rest.:)

---

### Post by Inxsible on 2007-11-14
if you want, you can change your hostname by System>>Administration>>Network. On the General tab, change the name to whatever you like.

After doing this, you will have to reboot because you won't be able to do anything.  Next time you start, your machine will have a new name.

The CLI way to do it would be to edit the following two files.
```
gksudo gedit /etc/hostnames /etc/hosts
```

---

### Post by Inxsible on 2007-11-14
> **NWAmama said:**
> Ok..I'm now moving this in the direction of the install Flash question..

Here's what I did....

base@base-desktop:/$ cd ~/Desktop
base@base-desktop:~/Desktop$ ls
adobe-release-i386-1.0-1.noarch.rpm
base@base-desktop:~/Desktop$ sudo # rpm -Uvh <rpm_package_file>
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
base@base-desktop:~/Desktop$ 

What's next?Are you trying to install a rpm file ? Well you can't. Not directly anyway. 

you need to install alien and then convert the rpm to a .deb file and then install.

Alternatively, you can simply install flash from the repos. Why are you installing it from the rpm file?

---

### Post by Dr Small on 2007-11-14
> **Inxsible said:**
> if you want, you can change your hostname by System>>Administration>>Network. On the General tab, change the name to whatever you like.

After doing this, you will have to reboot because you won't be able to do anything.  Next time you start, your machine will have a new name.

The CLI way to do it would be to edit the following two files.
```
gksudo gedit /etc/hostnames /etc/hosts
```
Restarting X will also do the trick, as I have tested ;)

---

### Post by NWAmama on 2007-11-14
> **Inxsible said:**
> 
Alternatively, you can simply install flash from the repos. Why are you installing it from the rpm file?

Because I don't know what the heck I'm doing! :)  What is the repos and how do I get to it?

---

### Post by NWAmama on 2007-11-14
Oh, repository.  Still, how do I get to it?

---

### Post by Dr Small on 2007-11-14
> **NWAmama said:**
> Oh, repository.  Still, how do I get to it?
Applications > Add / Remove
Search for Flash, or whatver you are trying to install, and install it ;)

---

### Post by Inxsible on 2007-11-14
Make sure the universe and multiverse repos are switched on. Then do ```
sudo aptitude install flashplugin-nonfree
```

---

### Post by NWAmama on 2007-11-14
Well, that took about 2 seconds.  For future reference, how would I install it via the terminal...or do I want to know?

---

### Post by Inxsible on 2007-11-14
> **NWAmama said:**
> Well, that took about 2 seconds.  For future reference, how would I install it via the terminal...or do I want to know?read my earlier post.

or were you implying installing the rpm file ?

---

### Post by NWAmama on 2007-11-14
> **Inxsible said:**
> Make sure the universe and multiverse repos are switched on. [/code]

Where would I find those settings and exactly what are universe/multiverse repositories?

---

### Post by Dr Small on 2007-11-14
> **NWAmama said:**
> Where would I find those settings and exactly what are universe/multiverse repositories?
System > Administration > Software Sources

---

### Post by Inxsible on 2007-11-14
> **NWAmama said:**
> Where would I find those settings and exactly what are universe/multiverse repositories?
System>>Administration>>Software Sources

---

### Post by NWAmama on 2007-11-14
They were turned on.  Thanks to everybody for your help.  I'm sure I will be back with more exciting questions for you :)

---

### Post by Dr Small on 2007-11-14
That is fine. This is what the community is for :D
Please mark your thread as Solved, from Thread Tools :D

Dr Small

---

