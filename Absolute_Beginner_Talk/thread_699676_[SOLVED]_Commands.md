---
title: "[SOLVED] Commands"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Mlok on 2008-02-17
Hi all!

I have a few questions about some things that really bug me since I started using Linux. The linux terminal to be exact. But I'm pretty sure the answer must be simple. So I'm in the right place in the Beginner's section I guess.

1. How do I know all the commands I can run in the terminal?

2. When I install a package (through Synaptic or apt-get) how do I know the command to launch the newly installed features, since the package name is not the command name. (that seems obvious to everybody but me - I can't figure it out)

3. Again when a package has been installed through synaptic on ubuntu, most of the time there is no entry in the menu for the app, and I must launch it from a terminal (well... if I remember the exact name of the command to type!)

Thank you for this.
It's pretty difficult to live in a Linux world without this basic knowledge.

---

### Post by seventhc on 2008-02-17
heres a good place to start
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
what programs are you having trouble starting up?

---

### Post by sb12 on 2008-02-17
1)	[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)
2) you can check installed files from the properties of the package in synaptic or you can type the first few letters and hit tab to complete it

---

### Post by DrMega on 2008-02-17
> **Mlok said:**
> 
2. When I install a package (through Synaptic or apt-get) how do I know the command to launch the newly installed features, since the package name is not the command name. (that seems obvious to everybody but me - I can't figure it out)

In Synaptic, find the installed package, right-click it and choose properties, then look at the installed files tab. It should give you a clue.

---

### Post by y-lee on 2008-02-17
> How do I know all the commands I can run in the terminal?

[LIST]
[*][Command line How to]("https://help.ubuntu.com/community/CommandlineHowto")

[*][Using The Terminal]("https://help.ubuntu.com/community/UsingTheTerminal")

[*][Alphabetical Directory of Linux Commands]("http://www.oreillynet.com/linux/cmd/")
[/LIST]

> When I install a package (through Synaptic or apt-get) how do I know the command to launch the newly installed features, since the package name is not the command name. (that seems obvious to everybody but me - I can't figure it out)

Try google or ask here, check and see what was installed and where, look for file names that end in .bin or .sh 

> Again when a package has been installed through synaptic on ubuntu, most of the time there is no entry in the menu for the app, and I must launch it from a terminal (well... if I remember the exact name of the command to type!)

Some things add a launcher and some don't after you know the commands to use you can add a menu item or launcher yourself. For menu items use Alacarte menu editor in Accessories to add items, sometimes thingsare added there and not checked,

---

### Post by stoneybroke on 2008-02-17
Hi, in terminal enter HELP for all the commands, this will give you all the commands. Usually when you install a program with Synaptic Package Manager it automatically is shown in the Applications area so for example if you installed a game it would show up in Applications>Games>"name of game" other packages can only be accessed via a terminal window but as you have not specified what you are trying to install it is difficult to answer but I hope the above helps.

Malcolm

---

### Post by Mlok on 2008-02-17
Thank you all for this.

Finally,  (in the terminal) I see that if I write nothing but simply hit the tab key twice, I get the list of all the accepted/installed commands. (Obviously, the list is impressive...)

By the way [http://www.linuxcommand.org](http://www.linuxcommand.org) seems to be very good. That's what I need!

[edit] And [http://www.linuxcommand.org/superman_pages.php](http://www.linuxcommand.org/superman_pages.php) is a good place to find that perfect command I'm looking for every now and then, while writing a script.

Thank you again.

---

### Post by seventhc on 2008-02-17
Glad we could help :) :guitar:
For programs you can't start, you should ask here (with the name of the program you installed) and most likely someone here can help.

---

