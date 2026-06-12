---
title: "[SOLVED] Ubuntu 101 Questions"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by vortex0007 on 2007-10-13
I'm completely new to *nix and decided to try to get Ubuntu 7.04 Server up and running on my Dell Optiplex GX280 desktop. I haven't felt this dumb in years. I've spent the last hour searching the forums and documentation for basic 101 type information and can't find the answer to a few questions. Here we go:

_Question 1: _

Is there a GUI included with Ubuntu 7.04 server? If so, what is the name of it and what is the command to start it?

I ask because when I boot my system after running through the initial OS setup, I'm dumped at a CLI with no idea where to go from there.

_Question 2:_

Everytime the system boots I'm greeted with the following message:

"apache2: could not reliably determine the server's fully qualified domain name. Using W.X.Y.Z for servername" 

In place of the W.X.Y.Z is the actual IP address that I manually configured.

I can ping the server from other machines on my network, and as I said I'm stuck in the CLI so the only thing I could figure out how to do to test if the machine had internet access was to run:

sudo apt-get update
sudo apt-get dist-upgrade 

and both of these commands worked proplerly.

Should I be worried about this error message? Any thoughts on how to fix this?



_Question 3:_

I installed the OS and incorrectly configured my partitions. I have 2 hard drives and because I chose Guided Partitioning during the intial OS configuration it skipped my second hard drive. I thought I would fix this by re-installing the OS (as I'm still learning) so the booted from the install CD, and ran back through the OS install. The second time I chose manual partitioning and got both drives configured. But at the end of the 2nd round of OS installation, a message came up asking me about the GRUB bootloader. The message said something similar to "we already found a boot menu - would you like to update it" Or at least that's what I thought it was doing. Instead, after I rebooted the server when the OS install was complete, I now have the following in the GRUB menu:

[INDENT]Ubuntu, kernel 2.6.20-16-server
Ubuntu, kernel 2.6.20-16-server (recovery mode)
Ubuntu, kernel 2.6.28-15-server
Ubuntu, kernel 2.6.28-15-server (recovery mode)
ubuntu, memtest86+
Other operating systems:
Ubuntu, kernel 2.6.28-15-server (on /dev/sda1)
Ubuntu, kernel 2.6.28-15-server (recovery mode) (on /dev/sda1)
Ubuntu, memtest86+ (on /dev/sda1)[/INDENT]

But what I want it to read is:

[INDENT]Ubuntu, kernel 2.6.20-16-server
Ubuntu, kernel 2.6.20-16-server (recovery mode)
ubuntu, memtest86+[/INDENT]

So I tried highlighting one of the entries I wanted to remove  and I pressed "e" to edit the option, but this didn't let me remove the complete line item, instead it let me edit the subcommands that are run when the option is selected. How do I go about editing this menu to remove the options? 

Regarding this problem I found a couple of posts elsewhere in this forum about using gedit to do this, but when I run "sudo gedit" I get an error about the command line not being found. So I'm completely lost on how to edit this menu.

Any help would be appreciated.

---

### Post by NavmaN on 2007-10-13
I can't answer the other Q's, but try nano or vim instead of gedit.
I.e. "sudo nano" or "sudo vim" instead of "sudo gedit".

Hope that helps,
Van

---

### Post by llamakc on 2007-10-13
#1. No. The server version does not ship with a GUI by default. There are many to install (and quite easily too) and choose from. What do you have in mind? There's GNOME, KDE, XFCE, WindowMaker, OpenBox, FluxBox and so on. 

#3. You have to edit the file /boot/grub/menu.lst to get those entries out of there permanently.

Another way is to use the package management system (apt-get, aptitude) on the CLI to remove the kernel package that the line in menu.lst refers to.

Meanwhile, Gedit is a graphical program, not one for use in the console. You should have the program "nano" installed by default. Replace instances of gedit with nano in any file editing advice.

2.6.28? Are you certain there's a kernel image in /boot that matches that number?

---

### Post by defrex on 2007-10-13
if you want to use gnome as your windows manager (it's the default for Ubuntu), run this to install it:
*sudo apt-get install ubuntu-desktop*

Then run this to start it:
*startx*

That should load up a vanilla Ubuntu desktop GUI, where you can use gedit, if you so desire.

---

### Post by om1 on 2007-10-13
this may help if you want to try to set up one with out a gui
you will want to set it up to your needs but it is a good reference
[http://howtoforge.com/perfect_setup_ubuntu704](http://howtoforge.com/perfect_setup_ubuntu704)

---

### Post by llamakc on 2007-10-13
> **defrex said:**
> if you want to use gnome as your windows manager (it's the default for Ubuntu), run this to install it:
*sudo apt-get install ubuntu-desktop*

Then run this to start it:
*startx*

That should load up a vanilla Ubuntu desktop GUI, where you can use gedit, if you so desire.

If you run the recommended command above, you will additionally install GDM, which is a graphical login manager. Many folks who run servers and still feel a need for a GUI choose to install the WM/DE by itself along with Xorg (and its dependencies).

You need to decide what you want before proceeding.

---

### Post by justinmiller87 on 2007-10-13
> **vortex0007 said:**
> _Question 1: _
Is there a GUI included with Ubuntu 7.04 server? If so, what is the name of it and what is the command to start it?
There is no GUI in Ubuntu Server. There is no need for one. The server is designed to be used in hardcore geek mode, but that doesn't mean you couldn't install GNOME, KDE, or one of many other GUIs if you wanted to. Check around, you'll find the answers in the forums.

> _Question 2:_
I can't help you with this one.

> _Question 3:_
Grub Menu
I can't help you with this one either, I know how to do it through GNOME, but no other way.


Ok, one out of three ain't bad, now let's have it with your other 98 questions. :-P

---

### Post by vortex0007 on 2007-10-13
Thanks for the suggestions so far. So I went ahead and did this:

sudo apt-get install ubuntu-desktop

and now I'm getting prompted several dozen times to press "enter" with the message:

Media change: please insert the disc labeled 'Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)' in the drive '/cdrom/' and press enter

I have the OS install CD I used in the CD-ROM drive and when I press enter, it waits for a second then prompts me again. After three or four times of hitting the enter button,  t displays a GET command and then shows some websites and then reprompts. 

Is there a way to tell it to stop asking me to press "enter'

if this ever gets finished I'm going to try to get into the GUI.

---

### Post by christhemonkey on 2007-10-13
Just having the cd in the drive isnt enough. (this is only because you install the server version, the normal ubuntu will mount things automagically for you)
You need to mount the cd.

Press <Ctrl>+<Alt>+F2 to get to the 2nd terminal.
Log in.

Then type:
```
sudo mount /dev/sdb /media/cdrom 
```

/dev/sdb might not be the correct location for your cd device, please supply the output of this command if that one doesnt work:
```
ls /dev/ | grep sd 
```


Once this is done, you can then type <Ctrl>+<Alt>+F1 to get back to where it is asking you to insert the cd.
Then you should be able to press <enter> and continue the installation.

---

### Post by llamakc on 2007-10-13
If you are installing packages from the install cd's the command to use is:

sudo apt-cdrom add

---

### Post by vortex0007 on 2007-10-13
Thank you for your help so far. 

I'm thinking that the server version isn't for me at this stage of my Unix knowledge. I'm currently downloading the desktop version and am going to attempt to start over.

Will I still be able to run LAMP on the desktop version? What about BIND?  

Any suggestions to starting over to make sure this GRUB boot menu problem doesn't happen a second time? 

I'm thinking of breaking out my old DOS 6.2 Boot disk and running FDISK /MBR to clean out the MBR and the be at a fresh state.

---

### Post by llamakc on 2007-10-13
When it gets to the partition section of the graphical install, tell it to use the entire disk, and to format it. You'll be all set. 

Yes, you'll be able to install Apache2, MySQL, and PHP.

---

### Post by om1 on 2007-10-13
all applications are in synaptic

synaptic is accessed buy the system menu

system >> administration >> synaptic package manager

just search for what you want

---

### Post by HermanAB on 2007-10-13
If you want a server with a GUI, then you should install ordinary Ubuntu/Kubuntu or best for a server Xubuntu.

The server edition is meant for use in data centres where there are no screens and keyboards attached to the machines.

Cheers,

H.

---

### Post by llamakc on 2007-10-13
> **HermanAB said:**
> If you want a server with a GUI, then you should install ordinary Ubuntu/Kubuntu or best for a server Xubuntu.

The server edition is meant for use in data centres where there are no screens and keyboards attached to the machines.

Cheers,

H.

The server edition is meant for computers that run server software and do not have the needs of full blown desktop environments. The presence of keyboards, monitors, or location in a data center doesn't matter.

The official word: [http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition)

---

### Post by louieb on 2007-10-13
Once you get your desktop up. Follow this guide. [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Setting up lamp is as simple as ```
sudo tasksel install lamp-server 
```
BTW: the guide will also answer your question #2

---

### Post by Jive Turkey on 2007-10-13
Ithink for question 3 you could try 

sudo vim /<path to grub file> and then you're on your own I'm scared to touch that thing, but there are some guides out there I'm sure.

also sudo nano /<path to file> I think nano is more likely to be installed by default, if not get them both using 

sudo apt-get install nano vim

vim and nano are both cli text editors.

You probably have a GUI up by now though huh?

---

### Post by vortex0007 on 2007-10-13
I have the Desktop version up and running - so I click on "Applications" > "System Tools" > "Konsole" then run 

sudo tasksel install lamp-server

the Package Configuration blue menu launches, says "Please wait" and then disappears - never getting past 0% and I'm dropped back down to the console prompt.

Should I be launching the installer a different way?

---

### Post by defrex on 2007-10-13
You have to be connected to the internet, incase that's the problem.

---

### Post by vortex0007 on 2007-10-13
Nah that wasn't the problem. Looks like it had already installed correctly the first time and completed - when I went into the Package Manager I could see everything was running. Thanks for the help. Off to start a few more posts with a bunch of other newbie questions.

---

