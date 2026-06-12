---
title: "Ubuntu 7.10 Serial Terminal Emulator"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by cronosmachine on 2007-11-12
dear all,
I'm trying to configure my firewall using console cable through serial com1. After i look over in forum people said using 'minicom'. But i tries to use minicom doesn't exist in my ubuntu.

do you know serial terminal emulator for ubuntu? beside minicom?

So i try to install it, but i counter an error:
[I][FONT="Courier New"]ubuntu:~$ sudo apt-get install minicom
Reading depencency tree
Reading state information... Done
E: Couldn't find package minicom
ubuntu:~$[/FONT][/I]

After that i found it at [here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fm%2Fminicom%2Fminicom_2.2-5_i386.deb&md5sum=fd4e6809f2eaf9c2845f288785c3e83a&arch=i386&type=main") to download. But i don't know how to install it. Can someone help me to solve it?

thanks

---

### Post by TadH on 2007-11-12
why do you want a firewall?

---

### Post by TadH on 2007-11-12
but to answer your question dont save it, just open it with the package manager and it should do it for you

---

### Post by robinl on 2007-11-12
I'm sure bash has inbuilt support for this, but if all else fails just do like

```

cat /dev/ttyS0     ' read from terminal
echo "hello world" > /dev/ttyS0            'input things to terminal

```

---

### Post by anewguy on 2007-11-12
Oh boy, I know I'm going to open a can of worms here, but......

In Unix, you have the capability to define how a specific "terminal" looks.  You do this by defining terminal types and capabilities in a file called "termcap".  It has been more years than I can almost count since I messed with that (needed to emulate a Honeywell terminal as best I could).  You also assigned the type to the terminal, but I can't remember that part right now.

The thing is, I don't even know if termcap exists anymore.  Maybe someone a little deeper in Ubuntu can explain how it's implemented now.  You used to be able to define all kinds of terminals - VT100, VT200, etc..

Anyone know how this works now?:)

EDIT:  BTW - the minicom stuff is in the regular synaptics package manager -> just open it and search for minicom, then select what you want and apply.

---

### Post by Japplet on 2007-11-18
I too am having trouble finding a terminal program to manage my Cisco equipment with. Minicom is NOT in the package manager as you have indicated, at least not in release 7.10. Any other ideas??

---

### Post by steve.horsley on 2007-11-18
Minicom most definitely is in the repositories in 7.10. I really don't understand your saying it's not. See screen shot.

I prefer gtkterm to minicom though. gtkterm is also in the repositories.

---

### Post by Japplet on 2007-11-18
Remember what forum this is.
Your screen shot is good, but all I have in there is wvdial. 
Any idea why the package isn't there for Minicom and gtkterm? Did I miss something on the install?

---

### Post by Japplet on 2007-11-18
Answered my own questions by mistake. Minicom and Gtkterm aren't in the distro that I downloaded yesterday but I did find the packages, quite by accident at Packages.ubuntu.com. 
I was suprised because I didn't see a link to it from anywhere on the Ubuntu home page. 
Now I just have to figure out application permissions so that I can run it.

---

### Post by anewguy on 2007-11-19
Minicom is in the repositories if you just have the defaults checked in sources and then use synaptic package manager.  That's where I looked - nothing special, nothing to it.  I'm just plain old everyday 7.10 Gutsy.  Next time please be move careful in your searching prior to saying something is NOT there.

You first need to decide what type of terminal you need - for example, do you VT200 functionality?  Once you know this, then you need to know how you are connecting - across the net (why you'd need an emulator then is beyond me), via a serial port, etc.  After that it's just a matter of accessing the port with the terminal type specified as per termcap.

---

### Post by steve.horsley on 2007-11-19
I wonder if you haven'r read the on-line repos indexes yet. Try this...

Start Synaptic - System->Administration->Synaptic
Menu Settings->Repositories
Make sure the first 4 boxes are checked (main, universe, multiverse and restricted)
Close the repos dialog
This is the important bit: Click the Reload icon top-left, to read the repository indexes.

I think it's the reload to read the indexes that you need to do really, but you might as well make sure the other repos are enabled while you are at it. 

Also, I like to disable the CD-ROM as a possible software source because it's easier for me to download packages than it is to find the install CD agan. I just hate being asked for the installer CD. 

If minicom and gtkterm aren't there after the index reload, I have no idea what could be going on.

---

