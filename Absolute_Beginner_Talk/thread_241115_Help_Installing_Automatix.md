---
title: "Help Installing Automatix"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by pink_taco on 2006-08-21
I'm attempting to follow the directions located at [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)
I pasted the commands listed under the heading "Automatic Automatix Installer" into the terminal.  It says that the Automatix Dapper Repositories have been added to my source list.  I'm confused.  I was under the impression that those three commands alone were supposed to complete the installation.  HELP!  What am I doing wrong? :confused:  

***ALSO, when I try to run automatic Ubuntu updates, it gives me the error "The Following Problems Were Found On Your System: An error occured.  Please run the package manager from the right-click menu or apt-get on a terminal to see what is wrong.  The error message was: 'Error: Opening the cache (E: Type '$' is not known on line 34 in source list/etc/apt/sources.list, E: The list of sources could not be read.)'  It tells me to go to the repository dialog to correct the problem.  It tells me to "fix the broken packages first"..

Could someone help me please?  I don't really understand the way that software is installed.  Can applications be installed directly from the terminal?  Can someone give me the lowdown on the terminal, packages, repositiories, etc.?:rolleyes:

---

### Post by nalmeth on 2006-08-21
To all appearances you should be right!
What happens when you type:
```
sudo apt-get install automatix
```
If it said it added Automatix Dapper Repos, maybe you have to still install it yourself? :-k

---

### Post by click4851 on 2006-08-21
not to be anti-terminal, but what does the Synaptic Package Manager indicate, is the package Automatix installed? I just installed this using Synaptic, and it went thru without a hitch. I believe the terminal install will work, but I believe the commands are a little more complicted than you describe, but not overly so.

---

### Post by b_martinez on 2006-08-21
> **pink_taco said:**
> I'm attempting to follow the directions located at [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)
I pasted the commands listed under the heading "Automatic Automatix Installer" into the terminal.  It says that the Automatix Dapper Repositories have been added to my source list.  I'm confused.  I was under the impression that those three commands alone were supposed to complete the installation.  HELP!  What am I doing wrong? :confused:  

***ALSO, when I try to run automatic Ubuntu updates, it gives me the error "The Following Problems Were Found On Your System: An error occured.  Please run the package manager from the right-click menu or apt-get on a terminal to see what is wrong.  The error message was: 'Error: Opening the cache (E: Type '$' is not known on line 34 in source list/etc/apt/sources.list, E: The list of sources could not be read.)'  It tells me to go to the repository dialog to correct the problem.  It tells me to "fix the broken packages first"..

Could someone help me please?  I don't really understand the way that software is installed.  Can applications be installed directly from the terminal?  Can someone give me the lowdown on the terminal, packages, repositiories, etc.?:rolleyes:

It seems that the file /etc/apt/sources.list has this symbol 
$ in front of a line and that is confusing the apt-get daemon. Look in the file [with gedit,or nano] and check line 34. If that symbol heads up or is in the line that would explain the message.
hth
Bill

---

