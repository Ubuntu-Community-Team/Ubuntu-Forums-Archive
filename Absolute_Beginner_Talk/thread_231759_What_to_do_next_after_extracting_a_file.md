---
title: "What to do next after extracting a file???"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by naomiangela on 2006-08-07
Hi, I'm new to Ubuntu and am trying to get the hang of installing, except i'm not sure how with some things. 
Right now I'm trying to install cabextract, I downloaded the file from the website, and extracted it, but I'm not sure what to do next. Anyone know??

---

### Post by cantormath on 2006-08-07
> **naomiangela said:**
> Hi, I'm new to Ubuntu and am trying to get the hang of installing, except i'm not sure how with some things. 
Right now I'm trying to install cabextract, I downloaded the file from the website, and extracted it, but I'm not sure what to do next. Anyone know??

delete what you downloaded,

open terminal
```
laptop:~$ sudo apt-get update
laptop:~$ sudo apt-get install cabextract
```

that should install it.

if you want to search for stuff

```
laptop:~$ apt-cache search whatever
```

Or if you want to skip the terminal all together, use synaptic and search/install from that program.
System>Administration>Synaptic

---

### Post by pdub on 2006-08-07
I would recommend installing applications from reporistories, unless they are not available or you want a version that is not yet in a reporistory.

I came from the SUSE world where I downloaded and compliled everything. 

You use the apt-get utility to install programs or you can use the GUI version called Synaptic. It is located in the tools>administration menu.

First I would recommend having a look at this how-to, especially the section for adding repositories.

Then you can just use:

sudo apt-get install cabextract

It's that easy!

---

### Post by naomiangela on 2006-08-07
I've got no clue how to delete it now. I know I extracted it into tmp or somthing. As for the repositories, i've been using that to download things, but I dont think i can with this one, plus i wouldnt mind knowing how to get things installed off of websites. 
the terminal way is going way over my head, i dont even know how to open 1 for starters. isnt there a way to install it after ive extracted it??

---

### Post by cantormath on 2006-08-07
> **naomiangela said:**
> I've got no clue how to delete it now. I know I extracted it into tmp or somthing. As for the repositories, i've been using that to download things, but I dont think i can with this one, plus i wouldnt mind knowing how to get things installed off of websites. 
the terminal way is going way over my head, i dont even know how to open 1 for starters. isnt there a way to install it after ive extracted it??

you can, I told you how.


open terminal
```
laptop:~$ sudo apt-get update
laptop:~$ sudo apt-get install cabextract
```

or
open synaptic, System>Administration>Synaptic, and search/install the cabextract that way.

that should install it, from the repositories, or the cd, if you cd is in the drive.

To delete the extracted file that is in the tmp folder, you can delete it or leave it there, whatever.

if you want to delete it, just go:
cd /tmp/
sudo rm -rf whateverFolder 
with that, dont just delete start deleting stuff.

---

### Post by cantormath on 2006-08-07
ubuntu is based on debian.  One of the big advantages of debian is that you can install programs that are packaged in deb files very easily.  There are repositories of programs all over the net, that you can download this software and install it with one command.......apt.

synaptic is gui program that connects you to search, install and delete software from these repositories.  It is safer for you to install things from these repositories when you have an option.

most anything you could possible want are in these repositories.
if its not, you can add repositories to /etc/sources.list or System>Administration>Software Properties.

---

### Post by pdub on 2006-08-07
I just installed cabextract using apt-get and it worked fine. You will need to add repositories.

Have a look at this how-to (I forgot the link in the last post)

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

If you cannot open a terminal then compiling programs may not be for you.

To open a terminal goto Applications>Accessories>Terminal in the menu.

You will need some things before you can compile programs such as build- essential.

Open a terminal as described above then type;

sudo apt-get install build-essential

Follow the instructions and wait for it to complete the install.

Then change to the folder where you extracted your program and type

./configure
make
sudo make install

Then you can type cabextract to start the program.

If you install using apt-get instead, you will be far better off.

---

### Post by powder on 2006-08-07
> **cantormath said:**
> 

if you want to search for stuff

```
laptop:~$ apt-get search whatever
```




Should be "apt-cache search whatever". ;)

---

### Post by naomiangela on 2006-08-07
alright thanks guys, got it to work

---

### Post by cantormath on 2006-08-07
to add/edit your repository list, open terminal

sudo gedit /etc/apt/sources.list

uncomment the repos that you want and save.

```
cantormath-laptop:~$ sudo apt-get update
cantormath-laptop:~$ sudo apt-cache search cabextract
Password:
cabextract - a program to extract Microsoft Cabinet files
```

if you add the right repo, it will show like that.
then........................

```
cantormath-laptop:~$ sudo apt-get install cabextract
```

---

### Post by cantormath on 2006-08-07
> **powder said:**
> Should be "apt-cache search whatever". ;)

fixed it

---

### Post by naomiangela on 2006-08-07
i got 1 more question, im tryin to install ies4linux here, ive got the terminal open so how do i "run the "ies4linux" executable"??

---

### Post by pdub on 2006-08-07
Have a look at this link.

[http://www.warrenguy.com/docs/ubuntu-linux/installing-internet-explorer-6.html](http://www.warrenguy.com/docs/ubuntu-linux/installing-internet-explorer-6.html)

---

