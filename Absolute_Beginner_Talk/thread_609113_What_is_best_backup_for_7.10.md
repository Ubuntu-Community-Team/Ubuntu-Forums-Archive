---
title: "What is best backup for 7.10??"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by calldrin on 2007-11-10
I've just installed 7.10 and it works great :-)
Now I need to get a backup program setup

I'm really impressed with Mac's Time machine... is there something like it for Linux?
If so, can I get complete step by step help to install and run the program?

Any other ideas?

Chuck

---

### Post by Pumalite on 2007-11-10
You might want to try these:

[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by matthewcraig on 2007-11-10
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)

This is just what you are asking to find!

---

### Post by calldrin on 2007-11-10
> **matthewcraig said:**
> [http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)

This is just what you are asking to find!

Thanks for the lead :-)

instructions

To use, make sure you have the following packages installed:
Debian 	$ sudo apt-get install python python-glade2 python-gnome2 python-gnome2-extras python-gtk2 rsync
Ubuntu 	$ sudo apt-get install python python-glade2 python-gnome2 python-gnome2-extras python-gtk2 python-gconf python-gobject rsync
Redhat/Fedora 	$ yum install pygtk2 gnome-python2-gconf gnome-python2-extras pygtk2-libglade

Then download, extract, change to the new directory and run:

$ ./flyback.py

Documentation

    * How it works
    * How to use 
--------------------------------------
But now my problem!

" Ubuntu 	 $ sudo apt-get install python python-glade2 python-gnome2 python-gnome2-extras python-gtk2 python-gconf python-gobject rsync "

This says all are installed.

"Then download, extract, change to the new directory and run:

$ ./flyback.py"

Download what??
extract what and how?
change to what directory?
run what? 
I tried $ ./flyback.py 
nothing appears to happen :-(

I  tried to follow the steps as outlined but I get no results.. 

chuck

---

### Post by bluepowder7 on 2007-11-10
try going to the downloads tab from where you read that set of instructions.  i assume he means download that flyback....tag.gz file he's providing.

---

### Post by calldrin on 2007-11-10
> **bluepowder7 said:**
> try going to the downloads tab from where you read that set of instructions.  i assume he means download that flyback....tag.gz file he's providing.

Yes I found it and I think it is installed.. Now I don't know how to run it.

I'm sorry I'm so damn stupid when it comes to Linux.. Most of the commands are "Greek" to me! 
I thought I'd see some sort of a Icon or something on the desktop to start the program.. nothing showing..
I'm now quite sure I'm in way over my head.. Maybe I'll just give it up until I can find something that will self/auto install ;-(

chuck

---

### Post by bluepowder7 on 2007-11-10
did you download?  seems you did.  ok.

did you extract the downloaded tar.gz file?  if not, you can just double-click it (i think) and ubuntu will extract it - probably to a folder in the same directory where the .tar.gz file is (kind of like "Extract to here" in the winzip world)

once you extracted it, open up that terminal window, change directories so that you're in the newly made directory (the one that contains all the extracted crap), and type that funky "$ ./flyback.py" commad.  did that?

i'm not sure if it would put an icon on the desktop, though.  it might have placed the program in one of the "Applications" or "System" menu items...  check there...

---

### Post by maharbA on 2007-11-11
Hi
**In my** (limited) **experience, I've found that right-clicking on an archive file (.zip, .rar, .tar.gz, etc.) and selecting "Extract Here"** (assuming you're using Gnome/Ubuntu rather than KDE/Kubuntu) **is much easier than double-clicking and using the extractor program.**

Also, the "./" part of "$ ./flyback.py" means that you're executing a command in "this" folder (the folder you're in -- so make sure you're in the right folder) you don't have to type "$" that's part of the command prompt. So you're opening flyback.py in the folder that you're in.

For example, if you extracted the archive into /home/you/Desktop (where "you is your username), and it created a folder called FlyBack, open a terminal and type "cd /home/you/Desktop/FlyBack" (remember, the terminal is case-sensitive) to move to the new folder and the type "./flyback.py" to open the program. If you don't want to go into that folder, you can type "/home/you/Desktop/FlyBack/flyback.py" to open the program. So if you want to make an application launcher, right-click on the Desktop and select "Create Launcher" name it what you want (probably FlyBack), put what you want in the Comment field and put /home/you/Desktop/FlyBack/flyback.py in the command field.

NOTE: the above is just an example! I have no idea what the folder that comes out of the archive will look like, so adjust the commands accordingly. This should give you an idea of what to do and why. I doubt that an icon will be added automatically since this app is in a very early stage of development. But, as I said, you can make your own icon/launcher so you don't have to keep going into the terminal. Also, since this app is so early in development you may not want to rely too heavily on it for you backups -- yet.

Sorry for the long post, I hope this helps

---

### Post by newlinux on 2007-11-11
you could try sbackup - in the repos...

---

### Post by calldrin on 2007-11-11
WOW !!! Thanks so much.
I got more usefull information from your post than I've had in the last 2 months of working with Linux.( printed a hard copy and put it in my file)
I will try again using your info.
For now, I an using  "sbackup" as also suggested. This seems to work... but I still want to get something like the "Time Machine".

Thanks again to ALL who have helped me since I got on board with Linux.

Chuck

---

