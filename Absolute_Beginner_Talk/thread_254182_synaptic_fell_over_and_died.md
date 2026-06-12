---
title: "synaptic fell over and died"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by thorby on 2006-09-09
I installed Ubuntu 6.06 live cd into a virtual machine under Parallels. Everything seemed to work - internet, etc. Synaptic showed me a nice list of packages and updated its info. Yeah!

Then I tried to install jEdit following the instructions [here](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_jedit) which have me use wget to download a .deb file and sudo dpkg to install it.

This install failed with a very confusing error message about how it could not create "./usr/lib/menu/jedit no such file or directory" (to what does the dot refer? Home? Root? desktop? Anyway, I was sudo, why couldn't it create it?)

So ok, forget it, do something else, I restarted Synaptic and now it won't work. It comes up and says that "package jEdit needs to be reinstalled but can't be found" or something. I guess it's mad at me for installing behind its back? But if it knows that, how come it doesn't know where the package is? And why won't it let me TELL it where it is?

Anyway, after it displays that error, Synaptic no longer shows me ANY packages -- the main window is empty, and search doesn't find any names. It's like its inventory has been completely wiped.

I don't have a clue what to do next. Reinstall the whole system from CD? What?

---

### Post by dannyboy79 on 2006-09-09
synaptic may not being displaying anything because if you did a search and it can't find jedit or whatever than it has nothing to show you. as far as find jedit, go to the terminal and type in sudo find / -name "filename". As far as the directory not being able to be created, why don't you at least create the directory that it wants to throw stuff in then I am sure the deb won't fail.otherwise I cant because it may have something to do with you using ubuntu through a virtual system so I am guessing the . you are asking about has something to do withj that. why don't you gogle something like, install software in virtual os install? I wish I could help you more but I am just a newbie trying to offer advice on what I might do.

---

### Post by thorby on 2006-09-09
> **dannyboy79 said:**
> synaptic may not being displaying anything because if you did a search and it can't find jedit or whatever than it has nothing to show you.That's cool - but how do I reset it and get it to display the list of installed/available packages, like it did right after the system first started? All the panes in the main window are empty.

Also I just discovered this on a jEdit forum> I installed rencentlly jEdit, the last debian package. Maybe, I installed the package wronged? I have Ubuntu 6.06. I receive the message (in Synaptic):
Unknown Error: exceptions.SystemError (E: The package jedit needs to be reintalled, but I can't find an archive for it)Hah! That is just what I see (only I couldn't actually complete the jedit install).

So there are at least two problems here: (1) Why won't Synaptic show me any packages any more? (2) there is some conflict between dpkg and synaptic when this jEdit package is used.

Regarding the jEdit package, my problem is what file couldn't it create? The path starts with a dot, meaning current-directory, but where was that, to dpkg? I manually created /usr/lib/menu and ~/usr/lib/menu and the same error occurred.

---

### Post by dannyboy79 on 2006-09-12
i believe that the . represents the current username. So if your username is Ed than you need to create the directory /home/Ed/usr/lib/menu. all you would have to do to display stuff in synaptic again is click on all which shopuld be in the left column? I am not exactly sure what you mean when you say synaptic isn't showing you anything?

---

### Post by jordanmthomas on 2006-09-12
Actually, the dot represents the current directory.
Two dots represents the directory one level up.

To fix your synaptic, run this on a command line
```
sudo apt-get -f install 
```
This will attempt to fix any errors in the package manager.

It probably won't make jedit work, but you know...whatever
Can't you run jedit statically from anywhere you want?  (I could in Windows last time I used it anyway)

---

### Post by NRTech on 2006-09-12
I am currently switching over my network to Ubuntu.  My pc went without a hitch...good-bye Windows for me.  The family pc has installed OK, but none of the users have Synaptic Package Manager available in their menus.  Not even sudo apt-get anything works in a terminal, just returns to the prompt.  In fact, no sudo request gets any results at all.  How do I get it back?

---

### Post by jordanmthomas on 2006-09-12
Go to System --> Administration --> Users and Groups
On each user's properties, go to the user privileges tab and make sure 'executing system administration tasks' is checked.  The user will then be allowed to use sudo.

---

### Post by hooked on 2007-02-05
Actually, the same thing happened to me when I tried to install the alien-made deb "armagenotrad" with dpkg. It gave me the 'Unknown Error: 'exceptions.SystemError' (E: The package armagenotrad needs to be reinstalled but I can't find an archive for it.) This error is quite pervasive and does not allow me to update or install new programs. I would love to know a simple fix for this (sudo apt-get -f install) doesn't help, it just restates the error.

---

