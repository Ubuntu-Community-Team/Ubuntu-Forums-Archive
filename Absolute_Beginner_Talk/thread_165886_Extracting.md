---
title: "Extracting"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by RobyX on 2006-04-25
Just started using linux this afternoon. So im relativly new, im wondering how to open these .RPM and .DEB files? Im guessing there is a command to use but i've no clue what and linuxgoogle gave me a program to do it but was in .rpm format to lol.

---

### Post by Jagot on 2006-04-25
Check down the page a bit on this link (points 2 and 3):

[http://psychocats.net/ubuntu/installingsoftware.php](http://psychocats.net/ubuntu/installingsoftware.php)

---

### Post by bswilson on 2006-04-25
[SIZE="5"]Introduction[/SIZE]
There are basically 2 options for you on a Ubuntu system.  The files you're talking about are known as _packages_.  They are binary software programs pre-compiled and placed into a special archive so that you can easily install them.

Files that end in *.deb are Debian packages, and *.rpm files are Red Hat packages.  Ubuntu is based on the Debian Linux distribution, so the easiest files for you to install will be *.deb packages.

The RPM system (Red Hat Package Manager) was invented by Red Hat, but you can install the RPM tools on just about any Linux system.  Also, there's a program called **alien** ([see this post]("http://ubuntuforums.org/showthread.php?t=163709")) that can convert a *.rpm file to a *.deb file.

I personally recommend that you stick with *.deb packages, unless there's a specific program you want that only comes in *.rpm format.  I would offer that there are few that fall into that category.  :) 

So, to install *.deb packages, you have 2 basic choices; you may use the command line tool **dpkg** and **apt-get**, or the graphical tool **Synaptic Package Manager**.

[SIZE="4"]Using dpkg and apt-get[/SIZE]
The command line tools are not terribly difficult to use.  If you want to download and install a program, there are 2 steps with apt-get:
Step 1. Read the Ubuntu software database, make sure your local copy is up to date.
```
sudo apt-get update
```
Step 2. Install the package you want (you must know it's name).
```
sudo apt-get install package-name
```

or

If you already have downloaded a *.deb package, you can install it via the command line using this syntax:
```
sudo dpkg -i package-name
```

[SIZE="4"]Using Synaptic Package Manager[/SIZE]
Step 1. Click on System --> Administration --> Synaptic Package Manager
Step 2. Enter your administration (e.g. root) password.

You can now see all the software choices you have.  The cool thing is you can search for packages without having to know their actual name.

As I stated, the easiest way for most folks is to use Synaptic Package Manager.  

_*Good luck!!!*_

---

### Post by RobyX on 2006-04-25
BIG Help guys.

I am really surprised as to how much help I got from IRC and this thread. 
I promise to return the favor when I am actually good with Linux one day ;)

---

### Post by RobyX on 2006-04-25
Sorry for double post.

But I am lost here, [http://img243.imageshack.us/img243/8894/screenshot12ye.png](http://img243.imageshack.us/img243/8894/screenshot12ye.png)

What did I do wrong? it said I've installed it.. then it says its not installed. :-?

---

### Post by Jagot on 2006-04-25
You will need to change to the directory where you've downloaded the file.  Then:

sudo dpkg -i frostwire.deb

Then to see if it is installed do dpkg -l frostwire

Do not try and list the .deb - just the name of the program now.  It should show up.

---

### Post by mostwanted on 2006-04-25
I know you've been given lots of good advice already, but take a look at the guide in my signature for some other time. It's a highly graphical guide to installing packages in Ubuntu.

---

### Post by RobyX on 2006-04-25
mostwanted, I searched up frostwire in the SYnaptic package manager and the only options I see are "Mark for removal/Mark for complete Removal/Properties"

Edit: Nevermind im dumb lol

---

### Post by Jagot on 2006-04-25
[QUOTE=RobyX]mostwanted, I searched up frostwire in the SYnaptic package manager and the only options I see are "Mark for removal/Mark for complete Removal/Properties"[/QUOTE]

That means it is installed.

---

### Post by RobyX on 2006-04-25
Ok I promise this is going to be my last question! ;) 

I have learned to install programs... finnaly, thanks to you guys but I can't execute them.

[http://img259.imageshack.us/img259/5443/screenshot9xu.png](http://img259.imageshack.us/img259/5443/screenshot9xu.png)

I dont see why I DONT have permision this is my admin account or atleast I think it is, how do you change it?

---

### Post by Jagot on 2006-04-25
Press Alt+F2 then type Frostwire.  

You are not root.  Check out this wiki about it:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

