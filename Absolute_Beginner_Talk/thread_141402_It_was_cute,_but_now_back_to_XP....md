---
title: "It was cute, but now back to XP..."
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-03-08
I have tried to work through all of the many wonderful suggestions I have received throught these forums, but evidently this software and my hardware are just not going to play nice together. I was using XP pro with the occaisional snag, but this OS is beyond me.

I cannot figure out how to make the OS do anything. I cannot make anything actually install, and other than reformatting and re-installing the OS, I have no idea what to do to 'uninstall' anything. I can't spend another three hours attempting to figure out what 'kernel source version' I have, nor can I begin to comprehend the implications or actions involved in "compiling and building a kernel"

It took me three days to figure out I didn't have to reboot and select 'session' at the OS login page just to get a command terminal.

I apologize to those who wasted their time with suggestions...  Some people just cant' figure it out...

---

### Post by Klaidas on 2006-03-08
[http://www.linux.org/lessons/](http://www.linux.org/lessons/)
A great guide, maybe iot would help you to answer those common linux user questions :) Don't give up so soon! :cool:

---

### Post by trorion on 2006-03-08
You've done an excellent job of pointing out some of the major problems with the *nix development mentality vs the windows user mentality.  I think a lot of developers would be well inclined to consider what you are saying as far as the general system as a whole if they want windows users to go to *nix.

I myself have switched because Microsoft told me I would have to send my XP disks back to them and pay $30 to have replacement disks shipped to me in order to re-install XP after I downloaded their patch and it broke my computer.  There's just something wrong with that.

But I'm pretty saavy with computers as a whole and understand a lot of what people are saying.

I'm glad you tried *nix and I hope that you realize that there are some fantastic open source options even if your using windows..
Use [www.openoffice.org](www.openoffice.org) instead of Microsoft Office to save $400.
Use Firefox instead of MSIE
Use [www.gimp.org](www.gimp.org) for your picture editing.

Someday *nix will work seamlessly for people such as yourself that want more consistency etc.  The community will welcome you back then.

---

### Post by taurus on 2006-03-08
Just like any new operating system, you need to spend some time learning it!  Don't expect to know everything right away because I bet you the first time you used Windows, you didn't know where were heads and where were tails, either!  I think that is the major problem with some newbies.  They expect Linux or at least the desktop environment to look and behave like XP and when they can't do something that I would normally do in XP by clicking it, they would just give up and go back to XP!  It is a shame because XP is crap compared to Ubuntu or any other Linux distro...

---

### Post by Papa-san on 2006-03-08
I kinda have to give up. I am pretty severely physically handicapped, and the only way I can currently use this thing is to be sitting on the floor five feet from the router I am plugged into. I get about ten minutes before I have to get up and move around.  My wireless card, which allows me to be in my chair, won't work...  I will muddle my way through the guide, but somehow I don't see it helping much...lol

---

### Post by trorion on 2006-03-08
[QUOTE=taurus]Just like any new operating system, you need to spend some time learning it!  Don't expect to know everything right away because I bet you the first time you used Windows, you didn't know where were heads and where were tails, either!  I think that is the major problem with some newbies.  They expect Linux or at least the desktop environment to look and behave like XP and when they can't do something that I would normally do in XP by clicking it, they would just give up and go back to XP!  It is a shame because XP is crap compared to Ubuntu or any other Linux distro...[/QUOTE]
The end user is right.  The programmer/developer needs to adjust their programs to fit the end user.  Windows commands the major market because they realize this (and they have a fantastic business model that dominates).

Papa-san: I had a lot of problems with my wireless card as well.  May I ask you a couple questions and maybe help you out?
1- Is it possible for the short term to hook up your computer to your router via cat-5 cable?  Not forever just until we can figure out the drivers?  That way you won't have to struggle with running back and forth.
2- What kind of wireless card do you have?  As much detail as possible.

---

### Post by Zeroangel on 2006-03-08
Wow. That's too bad that you are put off by linux so quickly. There will be a time someday when a linux OS is ready for the normal person who does not want to commit themselves to exploring an OS just to get it working properly exactly the way they want it. Especially when it flakes out with their particular hardware config just like mandrakelinux did to mine.

I say that linux is a good learning experience if you are up for that experience, but if you are not (or don't have time), then use windows. I for one have grown to LOVE linux.

---

### Post by Papa-san on 2006-03-08
[QUOTE=trorion]The end user is right.  The programmer/developer needs to adjust their programs to fit the end user.  Windows commands the major market because they realize this (and they have a fantastic business model that dominates).

Papa-san: I had a lot of problems with my wireless card as well.  May I ask you a couple questions and maybe help you out?
1- Is it possible for the short term to hook up your computer to your router via cat-5 cable?  Not forever just until we can figure out the drivers?  That way you won't have to struggle with running back and forth.
2- What kind of wireless card do you have?  As much detail as possible.[/QUOTE]
Very true. unfortunately, they created the entire environment with a plethora of patches, rather than rewriting code from where it went bad.  I have been using Firefox exclusively for two years now, and have been a stalwart netscape user since version 2.3 came out... never liked using msie... I know the linux distros are so superior to the best of windows, but just don't seem able to wrap my brain around the inner workings.  (Mounting, right?) lol

---

### Post by trorion on 2006-03-08
OK, you have: Broadcom Corporation BCM4306 802.11b/g network card on a dell latitude.  This is a motherboard card and I believe the latitudes came with a cat-5 connection as well right?

Lets get your wireless working then lets get you to the desktop you love!

By the way, I'm a newbie too.  Are you willing to go through this with me?

---

### Post by Papa-san on 2006-03-08
OK... sounds good
I am hooked with the cat5
 OK gonna take a mint to backpedal to the guides...

---

### Post by Papa-san on 2006-03-08
BCM4306 802.11b/g Wireless LAN Controller

It doesn't show that there is a driver for it

.

---

### Post by Papa-san on 2006-03-08
*-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:f8ffc000-f8ffdfff irq:11

---

### Post by Papa-san on 2006-03-08
I  think i installed ndiswrapper, but the error when trying to run it was that it couldn't find 'ndisgkt' or something

---

### Post by Lord Illidan on 2006-03-08
[quote=Papa-san]I have tried to work through all of the many wonderful suggestions I have received throught these forums, but evidently this software and my hardware are just not going to play nice together. I was using XP pro with the occaisional snag, but this OS is beyond me.

I cannot figure out how to make the OS do anything. I cannot make anything actually install, and other than reformatting and re-installing the OS, I have no idea what to do to 'uninstall' anything. I can't spend another three hours attempting to figure out what 'kernel source version' I have, nor can I begin to comprehend the implications or actions involved in "compiling and building a kernel"

It took me three days to figure out I didn't have to reboot and select 'session' at the OS login page just to get a command terminal.

I apologize to those who wasted their time with suggestions...  Some people just cant' figure it out...[/quote]

Hehe, I was like you when I started out. I remember flaming some linux forum (not this one), telling them that they were a bunch of junkies. I couldn't do anything with Linux. But I kept on trying, it was like a drug. Heaven knows how many cds I downloaded!

 Until I found this forum, that is.

[Installing software]("https://wiki.ubuntu.com/UserDocumentation#head-57224fc8a4bfcbe0286245ae95b4f4c7ebb4c4ef"). Have you tried Synaptic? And apt-get? And automatix? Boy, you are going to love them.

And I believe you were going to compile the kernel for the wireless drivers? I think that now you are with the cat5, you should learn your way around first.

---

### Post by Papa-san on 2006-03-08
I love this forum... no flaming here!

I have tried synaptic (no luck) apt-get is what got me the ndiswrapper, and automatix isn't found...  Would love to learn how to make this work...

---

### Post by Lord Illidan on 2006-03-08
[quote=Papa-san]I love this forum... no flaming here!

I have tried synaptic (no luck) apt-get is what got me the ndiswrapper, and automatix isn't found...  Would love to learn how to make this work...[/quote]

I didn't mean that you were flaming. Your post is a very good one.

Why do you have no luck with synaptic? Are you using kubuntu? If so, type : ```
sudo apt-get install synaptic
```
To run synaptic, then it is a simple :
```
sudo synaptic
```

Automatix can be found here : [http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix)

---

### Post by Papa-san on 2006-03-08
$ sudo synaptic


(synaptic:4103): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:4103): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

---

### Post by Papa-san on 2006-03-08
using ubuntu

---

### Post by Papa-san on 2006-03-08
Automatix can be found here : [http://www.ubuntuforums.org/showthre...ight=automatix](http://www.ubuntuforums.org/showthre...ight=automatix)

I went thru it, and it seems to have loaded, but when I try to run thru the command terminal, I get:
john@laptop:~$ automatix
bash: automatix: command not found

---

### Post by Zeroangel on 2006-03-08
Oh yea, Synaptic is a graphical installer tool. To launch GUI based programs as root (such as nautilus) you should use **gksudo** not **sudo**. Sudo is usually only used for executing single commands as root.

Use the menu. System > Administration > Synaptic Package Manager . It will then ask you for your admin password.

Automatix isn't included in the default installation due to copyright issues. It's a tool that you will have to download yourself (disclaimer: if it is legal for you to do so).

---

### Post by Papa-san on 2006-03-08
Am I supposed to be replying directly, or quoting or something..? Or sending to someone direct?

---

### Post by Lord Illidan on 2006-03-08
[quote=Papa-san]$ sudo synaptic


(synaptic:4103): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:4103): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed[/quote]

But does it stop there? Or it continues to load?

About Automatix, you should find that you don't load it from the terminal, but from the menu.

---

### Post by Papa-san on 2006-03-08
No, it stops there.

Automatix... OK, I was just following the author's instructions which said to use terminal.

---

### Post by Papa-san on 2006-03-08
OK got the automatix to run

---

### Post by Papa-san on 2006-03-08
OK... I'm gonna go take another Lortab so I can handle the gymnastics... back in two (Automatix is loading anyways...)

---

### Post by trorion on 2006-03-08
Alright!  THIS IS FOR YOUR WIRELESS CARD.

First off look on your dell CD's or your windows system for one of these files:
bcmwl5.inf or bcmwl5a.inf

Then do this:
```
sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
```

This will clean out your old stuff.  To execute this code launch a terminal window.  The terminal window is the equivalent of "command" on your old windows system.

FYI sudo is a command that says "run the command I am giving you under root."  Root is the administrator of the computer.  When you first type sudo *command* it will ask you for a password which is **your** password.  if that doesn't work let me know.

Breakdown:
sudo modprobe -r bcmwl5    I believe this removing the card.
sudo rmmod ndiswrapper    This is removing your ndiswrapper stuff.
sudo apt-get remove ndiswrapper-utils     again removing ndiswrapper stuff
..actually it's all removing ndiswrapper stuff.


Tell me if you found either one of these.
bcmwl5.inf or bcmwl5a.inf

---

### Post by trorion on 2006-03-08
[QUOTE=trorion]Alright!  THIS IS FOR YOUR WIRELESS CARD.

First off look on your dell CD's or your windows system for one of these files:
bcmwl5.inf or bcmwl5a.inf

Then do this:
```
sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
```

This will clean out your old stuff.  To execute this code launch a terminal window.  The terminal window is the equivalent of "command" on your old windows system.

FYI sudo is a command that says "run the command I am giving you under root."  Root is the administrator of the computer.  When you first type sudo *command* it will ask you for a password which is **your** password.  if that doesn't work let me know.

Breakdown:
sudo modprobe -r bcmwl5    I believe this removing the card.
sudo rmmod ndiswrapper    This is removing your ndiswrapper stuff.
sudo apt-get remove ndiswrapper-utils     again removing ndiswrapper stuff
..actually it's all removing ndiswrapper stuff.


Tell me if you found either one of these.
bcmwl5.inf or bcmwl5a.inf[/QUOTE]
Sorry, I think I have confused the issue.  If you have either one of the above drivers then the normal procedure WILL NOT WORK.

This guide is useful
[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+HOWTO](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+HOWTO)
It seems to work overall for Broadcom cards like yours.

---

### Post by Papa-san on 2006-03-08
OK... there is no windows system anymore, the cd with the drivers will not read. It says "invalid coding"

---

### Post by trorion on 2006-03-08
[QUOTE=Papa-san]OK... there is no windows system anymore, the cd with the drivers will not read. It says "invalid coding"[/QUOTE]

Let me look up your card for you then.  I'm simply doing a search for the drivers on broadcom's web page....I will edit this message to tell you if you need to use the non-automatix route.

You need: bcmwl5.inf
Since you don't have it we will get it from the windows version of the driver.  This is kind of weird to do since it will download as an "exe" program.  You will download it to your desktop and then "unzip" it.  I'll walk you through it.

---

### Post by Papa-san on 2006-03-08
I'm just frustrated because I can't get past the first part of any 'setup' because something else doesn't jibe... I have downloaded the drivers, but they are unusable as an .exe file. I got the program that unzips them, unzipped the files, and now cannot find the .inf files.  The file structure and user interface just dont make sense yet. The biggest issue with this laptop is the organic defect between the keyboard and the chair...

pci id 14e4: 4320 (rev02)

---

### Post by trorion on 2006-03-08
[QUOTE=Papa-san]I'm just frustrated because I can't get past the first part of any 'setup' because something else doesn't jibe... I have downloaded the drivers, but they are unusable as an .exe file. I got the program that unzips them, unzipped the files, and now cannot find the .inf files.  The file structure and user interface just dont make sense yet. The biggest issue with this laptop is the organic defect between the keyboard and the chair...

pci id 14e4: 4320 (rev02)[/QUOTE]
cool.  You have them unzipped on your desktop then right?  There is a file there that you can open right?  But you can't find the file?

Check the unzipping program and see where you are unzipping them too.
If you want to try the download again I KNOW the files are in this:
[http://ftp.us.dell.com/network/R94826.EXE](http://ftp.us.dell.com/network/R94826.EXE)

---

### Post by Lord Illidan on 2006-03-08
The lack of synaptic worries me more, somehow.

Are you using GNOME or KDE? Is there the word Applications at the top of the screen? If so, it is GNOME. If there is a single large panel at the bottom, then you are using KDE.

Also, what version of Ubuntu are you running? Breezy, Hoary or Dapper?

Try this :

```
sudo apt-get install --reinstall synaptic
```

---

### Post by Papa-san on 2006-03-08
[QUOTE=trorion]cool.  You have them unzipped on your desktop then right?  There is a file there that you can open right?  But you can't find the file?

Check the unzipping program and see where you are unzipping them too.
If you want to try the download again I KNOW the files are in this:
[http://ftp.us.dell.com/network/R94826.EXE](http://ftp.us.dell.com/network/R94826.EXE)[/QUOTE]
OK... I had R94827.exe

Now I have the one you gave me dl'd, and when I go to open it, I get a "Menu Editor"? when I d/l'd, I set it to use 'smeg' to open it... How do I do this?

---

### Post by Papa-san on 2006-03-08
[QUOTE=Lord Illidan]The lack of synaptic worries me more, somehow.

Are you using GNOME or KDE? Is there the word Applications at the top of the screen? If so, it is GNOME. If there is a single large panel at the bottom, then you are using KDE.

Also, what version of Ubuntu are you running? Breezy, Hoary or Dapper?

Try this :

```
sudo apt-get install --reinstall synaptic
```[/QUOTE]
I am using Gnome also Breezy.. 

I'll try to re- install synaptic
OK It seems to have reinstalled correctly

---

### Post by Papa-san on 2006-03-08
[QUOTE=trorion]cool.  You have them unzipped on your desktop then right?  There is a file there that you can open right?  But you can't find the file?

Check the unzipping program and see where you are unzipping them too.
If you want to try the download again I KNOW the files are in this:
[http://ftp.us.dell.com/network/R94826.EXE](http://ftp.us.dell.com/network/R94826.EXE)[/QUOTE]

I have the .exe file downloaded to desktop. I cannot find the program to use to unzip them...

(I warned you that you were dealing with a complete idiot!)  lol 
The one time a file was unzipped, it just did it on it's own... now I can't make anything unzip them...

---

### Post by Papa-san on 2006-03-08
I guess Admin here can close and delete this thread....
It's beyond this old dog....

---

### Post by trorion on 2006-03-08
[QUOTE=Papa-san]I guess Admin here can close and delete this thread....
It's beyond this old dog....[/QUOTE]
It's up to you.
This is, in my opinion, one of the biggest flaws with *nix.  Nothing is "easy" to install.

If you want to you can right click on the .exe program and select "open with file-roller" which is going to be a lot more familiar to you.
To make sure your file-roller will work you can type (in a terminal window)

```
sudo apt-get install file-roller zip unzip unrar
```

Then right click on r948626.EXE and select "Open with file-roller"
find the .inf file and "extract" it.  Now you know how to easily extract stuff!

Shall I go through the rest step by step or are you done?

---

### Post by Papa-san on 2006-03-08
[QUOTE=trorion]It's up to you.
This is, in my opinion, one of the biggest flaws with *nix.  Nothing is "easy" to install.

If you want to you can right click on the .exe program and select "open with file-roller" which is going to be a lot more familiar to you.
To make sure your file-roller will work you can type (in a terminal window)

```
sudo apt-get install file-roller zip unzip unrar
```

Then right click on r948626.EXE and select "Open with file-roller"
find the .inf file and "extract" it.  Now you know how to easily extract stuff!

Shall I go through the rest step by step or are you done?[/QUOTE]

I entered the code above, and it worked (In the terminal it went thru the installation process) when I right click on the .exe file, I do not get an option to use 'file-roller' unless maybe I need to browse to its equivalent of an ".exe" file?!?

I want to get this to work, but am not having much luck...

---

### Post by meborc on 2006-03-08
i think you are in over your head... but just hear me out for one second... :-D 

you find it completely scary and distractive, when you try to follow everyones suggestions what to type in the terminal... you probably just copy/paste from this forum, which is totally OK and i do it too, but before that you must understand what each line of code you insert acctually does... that is the key for learning and the key for success...

but i totally resent the implication to the fact that progz are harder to install in ubuntu than in XP... i myself have hard time using windows, to navigate to some ad-full page to try to download a file and then to discover that it is virus infected... not much fun is it?

linux/unix/etc is a different way to do things... and it is the better/worse way (depending on a person) and if you really don't want to learn things and want to stick with the BAD (my 2 cents) WINDOWS way of doing things... then i guess that you might just stay with windows then... linux isn't a cool thing to show your friends... it is a working environment to people who grasp it better than windows... :cool: 

long text short - start with simple commands... use command **man** to understand what different commands mean and get used to doing things differently... then comes ubuntulove :mrgreen:

---

### Post by Perfect Storm on 2006-03-08
Papa-san, perhaps you should try another distro which doesn't require to much command line.

pclinuxos: [http://www.pclinuxos.com/](http://www.pclinuxos.com/)
mepis: [http://www.mepis.org/](http://www.mepis.org/)

or if you don't mind paying a little:
Xandros: [http://www.xandros.com/](http://www.xandros.com/)
Linspire: [http://www.linspire.com/](http://www.linspire.com/)

Perhaps these suits you better.

---

### Post by Papa-san on 2006-03-08
[QUOTE=meborc]i think you are in over your head... but just hear me out for one second... :-D 

you find it completely scary and distractive, when you try to follow everyones suggestions what to type in the terminal... you probably just copy/paste from this forum, which is totally OK and i do it too, but before that you must understand what each line of code you insert acctually does... that is the key for learning and the key for success...

but i totally resent the implication to the fact that progz are harder to install in ubuntu than in XP... i myself have hard time using windows, to navigate to some ad-full page to try to download a file and then to discover that it is virus infected... not much fun is it?

linux/unix/etc is a different way to do things... and it is the better/worse way (depending on a person) and if you really don't want to learn things and want to stick with the BAD (my 2 cents) WINDOWS way of doing things... then i guess that you might just stay with windows then... linux isn't a cool thing to show your friends... it is a working environment to people who grasp it better than windows... :cool: 

long text short - start with simple commands... use command **man** to understand what different commands mean and get used to doing things differently... then comes ubuntulove :mrgreen:[/QUOTE]

I gaurantee I am in over my head. I am so absolutely sick of windows that I would rather never use a computer again than to re-install their crap. I do want to learn, and have no problem doing so. I guess the biggest issue is my physical ability to deal with the pain of the floor as I learn. I have thouroughly read a hundred pages in regards to linux (Ubuntu) I have found very comprehensive and helpful guides to solve the issues I have. I am frustrated by the fact that my wireless card that allows me to be in an orthopaedically correct chair to use my computer, is not available to me. I apologize for my profound ignorance in the structure of this OS. I am willing to learn, and actually enjoy it, it just hurts, that's all...

---

### Post by Lord Illidan on 2006-03-08
[quote=Papa-san]I gaurantee I am in over my head. I am so absolutely sick of windows that I would rather never use a computer again than to re-install their crap. I do want to learn, and have no problem doing so. I guess the biggest issue is my physical ability to deal with the pain of the floor as I learn. I have thouroughly read a hundred pages in regards to linux (Ubuntu) I have found very comprehensive and helpful guides to solve the issues I have. I am frustrated by the fact that my wireless card that allows me to be in an orthopaedically correct chair to use my computer, is not available to me. I apologize for my profound ignorance in the structure of this OS. I am willing to learn, and actually enjoy it, it just hurts, that's all...[/quote]

On no account do we don't want you to be physically uncomfortable with Linux. Regarding, your wireless drivers, perhaps SUSE is better for you. People have reported success with its wireless capability : [http://www.novell.com/products/suselinux/](http://www.novell.com/products/suselinux/)

You can download it free, too.

Then, when you have increased your savviness, you can go back to Ubuntu, at your pleasure.

---

### Post by meborc on 2006-03-08
hope you didn't get discouraged by my lecture... :mrgreen: but i always want to make sure that there wouldn't be a misunderstanding between

a) it is hard to install things in linux

&

b) linux is a different way to do things

you wouldn't believe what i had to go through when i got started... fortunately i had help from one of my friends as well as from this forum ;) and from reading the help (yelp) which i NEVER did in windows :mrgreen: 

hope you get lucky with your wireless... i have never encountered this problem, so i can't help... have faith ;)

---

### Post by Papa-san on 2006-03-08
k


It has nothing to do with luck. This is just me with computers. Give me two minutes on ANY system, and it will require a re-formatted hard drive before it is usable again by anyone...


So.... I guess I'm out...

(lol)

---

### Post by trorion on 2006-03-08
Basically you are going to need to get the driver unzipped.  If you can figure that then do this:

```

sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

```
To un-install everything you have done so far with the old installations.

Then click (on your 'start' bar) "system" -> "administration" -> "synaptic"

In the synaptic window ([http://www.nongnu.org/synaptic/images/0.53-main.png](http://www.nongnu.org/synaptic/images/0.53-main.png)) you will select _P_ackages and then _R_epositores.  Then select "add" and "universe" and "multiverse" then click on OK and Apply.

Then in the "packages" window on the right hand side of synaptic you will find and add:
ndiswrapper-utils

Click "apply"
When it finishes you shut down synaptic.

Go back to your terminal window and type:
```
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
```
Where ~/Desktop/bcmwl5.inf (~/ tells the computer /home/*user name*) is the place you have extracted the bcmwl5.inf driver to (maybe it will be ~/Desktop/R94826/bcmwl5.inf ?)

Then type
```
sudo ndiswrapper -m
```
Which starts the ndiswrapper stuff

then type
```
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
```
Which is a 'script' that you are running in the terminal which updates your files.


The rest is really easy from the HOWTO:
4. Reboot your PC. On restarting, the light on your wireless card should come on. If not, try entering
Code:

sudo modprobe ndiswrapper

5. Your card is now working. Open the networking configuration tool System --> Administration --> Networking

6. Select your wireless network card (probably wlan0) and hit the properties button.

7. Tick the 'This device is configured' box, and enter your network name and connection settings. Ask your office network administrator for support if you don't know what this question means, or copy your settings from Windows.

8. BE CAREFUL entering your WEP key, if you're using one. You're expected to enter this in hexadecimal form; if you don't speak hex, prefix your key with s:

9. Click OK. The screen should close fairly quickly; if it hangs, you probably aren't connected properly.

10. Back in the Network Settings screen, select your wireless device as the default gateway device.

11. Click OK. Again, the screen should close fairly quickly.

12. Enjoy wireless nirvana. If everything works, you can delete the file from your desktop.

13. You might notice that the signal strength applet doesn't work properly. This is a known bug with these cards.

---

### Post by AirIntake on 2006-03-08
Ubuntu is not really hard to install things in, but it still could get easier. I think many users would like it if you could just double click on a .deb or .rpm or whatever and have a little GUI installer do it for them. A few lines of text might be pretty easy, but if you say that to my Dad, you just lost him :)

---

### Post by trorion on 2006-03-08
[QUOTE=AirIntake]Ubuntu is not really hard to install things in, but it still could get easier. I think many users would like it if you could just double click on a .deb or .rpm or whatever and have a little GUI installer do it for them. A few lines of text might be pretty easy, but if you say that to my Dad, you just lost him :)[/QUOTE]
bingo.
easy = familiar.  familiar for 90% of computer users = windows.

---

### Post by Papa-san on 2006-03-08
Basically you are going to need to get the driver unzipped. If you can figure that then do this:

OK, I have all that down OK, now I am trying to see if I can figure out how to get the .inf file separated out of the .exe file

---

### Post by halfvolle melk on 2006-03-08
Papa-san,
Just a thought. Is it possible for you to get an UTP cable of lets say 20 meters or whatever so you can put your computer on a table until you tackle the wireless issue? Your current situation seems to take out the fun.

---

### Post by Papa-san on 2006-03-08
[QUOTE=halfvolle melk]Papa-san,
Just a thought. Is it possible for you to get an UTP cable of lets say 20 meters or whatever so you can put your computer on a table until you tackle the wireless issue? Your current situation seems to take out the fun.[/QUOTE]
LMAO!
Thanks! I have my son working on getting an area set up...

---

### Post by Papa-san on 2006-03-08
I tried this, and must have done it wrong:
then type
Code:

for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile done

This is what I got:
john@laptop:~$ sudo ndiswrapper -i ~/home/john stone/drivers/bmcwl5.inf
Password:
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-hotplug          (Re)Generate hotplug information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
john@laptop:~$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
john@laptop:~$ sudo cat $confile | sed -e 's/RadioState|1/RadioState|0/' > $confile
bash: $confile: ambiguous redirect
sudo ndiswrapper -m
john@laptop:~$ sudo ndiswrapper -m
modprobe config already contains alias directive

john@laptop:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile done
> done
cat: /etc/ndiswrapper/bcmwl5/*.conf: No such file or directory
bash: /etc/ndiswrapper/bcmwl5/*.conf: No such file or directory
john@laptop:~$

Did I enter it wrong?

I'll try it again...
It is looking for the pci id? 14e4:4320 (rev 02) ?

---

### Post by jjf on 2006-03-08
Papa-san,

I'm sorry to hear about your trouble with Ubuntu.  I'm relatively new to Linux (but fairly experienced with computers in general), and it gives me trouble, too.  :)  I'm developing a theory that part of the appeal of Ubuntu is the victorious feeling of conquering the untamed wilderness of computing.  But I will say this: Linux seems a more *transparent* operating system to me.  The more I learn about Ubuntu, the more I feel like I'm learning about the way computers work on some fundamental level.  It's often frustrating, but when I figure something out, it's enormously rewarding in a way Windows (or OS X) never was.  

Of course the reward of figuring something out is cold comfort when you're lacking basic functionality.  If you find that after tinkering with the Linux command line, you're still not getting it any better, you might want to consider one of the other distributions of Linux that have been mentioned.  

As for Ubuntu being harder to use and install things on, I would agree that it is.  Certainly "hard" and "easy" can only be judged relative to something else, but the only standard that makes sense is the knowledge and expectations of the average user.  For better or worse, most users expect layers of abstraction: GUIs, icons, wizards, etc.  So it is hardly noticed that the Windows Wizard fails to find drivers for your new hardware half the time, or contracts a virus after a week of steady use, or leaves Windows Messenger wide open to the outside world so that the desktop gets bombarded with male enhancement ads; because at least Windows smiled pretty while telling me it's not going to work.  Any time the average user has to open a terminal and type in these arcane symbols that don't make any sense to them is a time they are doing something *hard*.  

So double-clicking an installer file and finding that the program just *works* is, in this climate, superior to having to open a terminal and type "sudo dpkg -i pkg-w-n-vwls_0.9.1c.deb".  Fortunately, I think Dapper will include a little program that allows you to double-click .deb files to install.  

Anyway, best of luck with your continued efforts, whether they're with Ubuntu or any other OS.

---

### Post by jjf on 2006-03-08
Ok, I'm done philosophizing.  I'll try to help.

I had similar problems configuring my wireless.  It kept giving me some message that sounded like, "modprobe alias already somesuch," which I interpreted as, "hey, that stuff is already added to your wireless configuration."

After some digging around, I found that I had to edit the /etc/network/interfaces file manually (presumably *sudo ndiswrapper -m* should have done this automatically, but it didn't seem to take).

```
sudo cp /etc/network/interfaces /etc/network/interfaces_bak
sudo gedit /etc/network/interfaces
```

Then I had to add lines for my wireless card (called wlan0).  Here's what my config looks like:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0
	map eth0

# added manually on 3/5/2006
iface wlan0 inet dhcp
wireless_keymode open
wireless_mode managed
wireless_nick *my router host name*
wireless-essid *my SSID, or wireless network name*
wireless-key s:*my WEP key, in normal (ASCII) characters*

auto wlan0

```

Then I plugged my wireless PCMCIA back in, and presto! it worked.

Here's the link I used to get it working:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)

---

### Post by byen on 2006-03-08
This may not be much but .......[this thread]("http://www.ubuntuforums.org/showthread.php?t=25683") helped me and many others in configuring Broadcom wireless with ndiswrapper. See if this helps.
Note:
1.The how-to is for Hoary but works on Breezy too
2.I suggest you read the first few pages to get a grasp of what is going on.

Hope it helps.Good luck!

---

### Post by Papa-san on 2006-03-09
[QUOTE=jjf]Ok, I'm done philosophizing.  I'll try to help.

I had similar problems configuring my wireless.  It kept giving me some message that sounded like, "modprobe alias already somesuch," which I interpreted as, "hey, that stuff is already added to your wireless configuration."

After some digging around, I found that I had to edit the /etc/network/interfaces file manually (presumably *sudo ndiswrapper -m* should have done this automatically, but it didn't seem to take).

```
sudo cp /etc/network/interfaces /etc/network/interfaces_bak
sudo gedit /etc/network/interfaces
```

Then I had to add lines for my wireless card (called wlan0).  Here's what my config looks like:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0
	map eth0

# added manually on 3/5/2006
iface wlan0 inet dhcp
wireless_keymode open
wireless_mode managed
wireless_nick *my router host name*
wireless-essid *my SSID, or wireless network name*
wireless-key s:*my WEP key, in normal (ASCII) characters*

auto wlan0

```

Then I plugged my wireless PCMCIA back in, and presto! it worked.

Here's the link I used to get it working:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)[/QUOTE]

I don't even know how to begin thanking everyone who has tried to help!
So I'll just say "Thanks!"
In your post, you say:  "Then I had to add lines for my wireless card (called wlan0). Here's what my config looks like:"

My wireless card isn't called anything... I have 'lo' (assumes it is the internal comms) and I have eth0, which is the card I am using now, but the BCOM card only shows up in some queries. Somewhere in this computers little world, it knows that card is there, but isn't actually assigning a physical ID...

I WILL continue to work at this. I have bookmarked all the threads and pages. I have most of them in cache, so I can take this thing to my desk or bed, and work on it. I should only need to cat 5 on occaision.

---

### Post by xyz on 2006-03-09
Hang in there...papa-san! The guys here on the site are really great help!
As a total n00b, I can only add this: it seems to me you're not doing that bad!You're just coming along fine!...just like most of us n00bs!
Linux gets more FANTASTIC each day that goes by!

At the beginning (and I still am at the beginning...I mean the very beginning!) my main pbm was impatience. I felt so stupid if I didn't 'master' the Linux world by....say,...the end of the week!! Once I solved that pbm, lots of things started sinking in...little by little!

---

### Post by Cousindaddy on 2006-03-09
I've read the whole thread and it looks like you're gettin' 'er figured out!

I know the frustration you feel.  Sometimes I just have to walk away from it for a day or so...but I eventually get right back on the horse.

You'll have to bookmark this thread from the beginning, so in the future, when you see someone experiencing some of the frustration you have, you can post your thread/link and say: "Been there, know how you feel. Hang in there!"

BTW:  I need you to figure this out so you can explain it to me and the thousands that will follow.

Keep your chin up.

---

### Post by trorion on 2006-03-09
[QUOTE=Papa-san]I tried this, and must have done it wrong:
then type
Code:

for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile done

This is what I got:
john@laptop:~$ sudo ndiswrapper -i ~/home/john stone/drivers/bmcwl5.inf
Password:
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-hotplug          (Re)Generate hotplug information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
john@laptop:~$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
john@laptop:~$ sudo cat $confile | sed -e 's/RadioState|1/RadioState|0/' > $confile
bash: $confile: ambiguous redirect
sudo ndiswrapper -m
john@laptop:~$ sudo ndiswrapper -m
modprobe config already contains alias directive

john@laptop:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile done
> done
cat: /etc/ndiswrapper/bcmwl5/*.conf: No such file or directory
bash: /etc/ndiswrapper/bcmwl5/*.conf: No such file or directory
john@laptop:~$

Did I enter it wrong?

I'll try it again...
It is looking for the pci id? 14e4:4320 (rev 02) ?[/QUOTE]


WB papa.
It actually looks by what you typed here that you have some bad breaks in your code so the computer is reading the lines improperly.


```

sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done

```
Try doing each line individually rather than copying it all at one time.
I assume you have on your desktop the files right?  They are ON the desktop not in a file on the desktop right?  I ask because sometimes unzip creates a file FOLDER called bcmwl5 and then puts bcmwl5.inf and bcmwl5.sys in that file.  If thats the case then you can open the file folder, copy the 2 files and paste them to your desktop.

---

### Post by Papa-san on 2006-03-09
Nope... Once I got 'em, I saved just the files to desktop... no folder there.
I'll try it again. I do type everything in rather than copy and paste. I believe there's value to typing it in on a learning curve basis... I'll post results...
john@laptop:~$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
john@laptop:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' >$conffile
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:1028:0005.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:1028:0006.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:1028:0005.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:1028:0006.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0001.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0002.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0003.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0004.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0001.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0002.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0003.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0004.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied
john@laptop:~$

---

### Post by Stew2 on 2006-03-09
Hang in there! You will get it! :D  You definitely get an "A" for effort! :D

---

### Post by baysteve on 2006-03-09
i just read the entire thread..about 6 years ago I attempted to install Red Hat and had the exact problems you are currently..I gave up and FINALLY decided to give Linux another try on my new laptop..and I must say the end result is very rewarding. I regret becomming discouraged to the point of scoffing at the Linux as an OS..So, how's your progress comming along?

---

### Post by Papa-san on 2006-03-10
I need to let ALL of you know...

MY wireless card actually SHOWS UP NOW!!!!

I'm so excited, I could just pee!

Later today I will try to get it working...

Thank you! Thank you! Thank you! Thank you!

THANK YOU, ALL!

---

### Post by trorion on 2006-03-10
[QUOTE=Papa-san]I need to let ALL of you know...

MY wireless card actually SHOWS UP NOW!!!!

I'm so excited, I could just pee!

Later today I will try to get it working...

Thank you! Thank you! Thank you! Thank you!

THANK YOU, ALL![/QUOTE]
Please do NOT pee on the card!  I did that once and have regretted it ever since...

Could you tell us what you did that worked for you to get it recognized?  One of the things I see a lot is people getting their hardware recognized then fading off without summarizing what worked and what didn't.

---

### Post by meborc on 2006-03-10
who said that determination isn't everything :mrgreen:

---

### Post by Papa-san on 2006-03-10
[QUOTE=meborc]who said that determination isn't everything :mrgreen:[/QUOTE]

Exactly right. At least I have some hope now!

I still cannot connect thru that card, but The first frustrating difficulty has been overcome.
I will summarize all of this (actually have one started!) and will post it once it is complete. I will also host the .inf and .sys files on my site for the next person with this issue with the Bcom 1300 series wlan card. Might be an ugly post, but I will try to include the keywords I searched for... lol

---

### Post by essexman on 2006-03-11
[quote=Papa-san]Exactly right. At least I have some hope now!

I still cannot connect thru that card, but The first frustrating difficulty has been overcome.
I will summarize all of this (actually have one started!) and will post it once it is complete. I will also host the .inf and .sys files on my site for the next person with this issue with the Bcom 1300 series wlan card. Might be an ugly post, but I will try to include the keywords I searched for... lol[/quote]

Papa-san

I have stumbled in on your threads and seen the efforts you (with help from the forum) have made in the last 3 days.

You have turned around from quitting and that should be a positive lesson for all.

Ubuntu is still new, but could be a serious rival to Windows in 2-3 years.  Your willingness to learn will feed back into the community and help Ubuntu to develop.

Ubuntu is becoming more and more user friendly with each release.

Thanks for sticking with it and plase keep using the forums.

---

### Post by soc on 2006-03-11
i'd say that his problem was on this line:
```
john@laptop:~$ sudo ndiswrapper -i ~/home/john stone/drivers/bmcwl5.inf
```
you did everthing right Papa-san, but the thing is that you must "escape" the space.
sounds weird?
thing is, when you type ~/home/john stone/drivers/bmcwl5.inf there is a space between "john" and "stone" so the programm thinks this more than one command: ~/home/john AND stone/drivers/bmcwl5.inf.
so you have to show the app, that the space isn't a delimiter, but a space by doing either this:```
sudo ndiswrapper -i ~/home/john\ stone/drivers/bmcwl5.inf
```
or this should work too:```
sudo ndiswrapper -i "~/home/john stone/drivers/bmcwl5.inf"
```
your an example for me, if i had so much problems i would have given up! :-)

btw: in my experience i think linux is really much easier than windows ... if you get used to do stuff different you will eventually love it.
especially installing things is (most of the time :-P) much easier ...
this is a quite funny site: [http://www.whylinuxisbetter.net/]("http://www.whylinuxisbetter.net/")

---

### Post by Papa-san on 2006-03-12
OK, I did this, and this is what I got:
sudo ndiswrapper -i /home/johnstone/drivers/bcmwl5.inf
bcmwl5 is already installed. Use -e to remove it

---

### Post by steveneddy on 2006-03-12
Maybe there is a LUGS meeting in his area that someone there can help him while sitting right there so he can look on and ask questions and GET IT DONE!!

He may be a little uninformed, and everyone is trying to help, but I believe that the Local LUG is the best solution.

LUG is Linux Users Group.

Look here:
[http://www.linux.org/groups/usa/](http://www.linux.org/groups/usa/)

I assume that you were in the USA. There are links to other countries on thier site of not.

Good luck, Papa-San. We were all noobies at one time or another. Keep trying, or better yet, keep hacking away at it. You'll get it.

EDIT:
Cool! You made it. Let us know how it works now.
[http://www.linux-laptop.net/](http://www.linux-laptop.net/)

---

### Post by darkwarrior0404 on 2006-03-12
[QUOTE=Klaidas][http://www.linux.org/lessons/](http://www.linux.org/lessons/)
A great guide, maybe iot would help you to answer those common linux user questions :) Don't give up so soon! :cool:[/QUOTE]


I have to admit that site helped me ALOT, finally figuring out what that weird cd / command is haha, thanks : ) im slowly getting there, when at first i moved from xp to this i was like "oh my god i'll never get this im fixing to go back to windows" but its slowly moving on and im so addicted to it i dont wanna get up from here to go to bed lol... i definately recommend giving it another shot : ) that site that they gave you is great i suggest going to it if you have much time : )

---

### Post by nala on 2006-03-13
[QUOTE=Klaidas][http://www.linux.org/lessons/](http://www.linux.org/lessons/)
A great guide, maybe iot would help you to answer those common linux user questions :) Don't give up so soon! :cool:[/QUOTE]

Oh. My. God. That is incredibly helpful. I've been looking for something like this! n.n

</threadjack>

---

### Post by takayuki on 2006-04-04
Papa san,

did you get it all worked out?  i hope you are still using linux.

let us know how it's going.

---

### Post by eyesoftheworld on 2006-04-04
Good luck with your ubuntu trials, at first i had no idea what i was doing but im getting better and just a tip, when uninstalling something use the follonwing command in the terminal:


              yourname@ubuntu:~$ sudo apt-get remove (name of program)

do not forget to omitt the parantheses around name of program of course

---

### Post by Papa-san on 2006-04-04
[QUOTE=takayuki]Papa san,

did you get it all worked out?  i hope you are still using linux.

let us know how it's going.[/QUOTE]

takayuki... we got her ironed out...FINALLY! Thanks for your support!

I am still using linux, and am actually so pleased with it, I can't see defiling my computer with any Windows OS... Now I have to work on getting my wife to make the switch... Her computer (Win XP Pro) is so screwed up, we have to boot it off the cd every time. Once she gets her vital info saved off, the only Windows solution is a re-format and re-install. She had someone use Partition Magic to 'move' her hard drive to another drive... It didn't work well, and has never been right since... Her 'D' drive has about 19 gigs free, and I know what is going to be going there!

---

### Post by takayuki on 2006-04-04
papa san,

great to hear you stuck with linux.  i think you've faced the steep part of the learning curve, so hopefully it'll be a bit more gentle from here on out.  i'm a noob too, so i understand your pain!

get your wife's data on a cd, slick the hd, install ubuntu.  joy.

takayuki

---

### Post by Jedeye on 2006-04-04
Wow... what a thread, the team work and determination! I was really pulling for ya Papa-san.. I keept hitting the next page button hoping to see that it was working. I was on the edge of my seat until page 8 where I saw the good news. Congratulations!!!

---

### Post by takayuki on 2006-04-04
[QUOTE=Jedeye]Wow... what a thread, the team work and determination! I was really pulling for ya Papa-san.. I keept hitting the next page button hoping to see that it was working. I was on the edge of my seat until page 8 where I saw the good news. Congratulations!!![/QUOTE]

great point about team work and determination, Jedeye.  that sort of support ain't gonna happen in a Windows XP forum.

---

### Post by johnnymac on 2006-04-04
Papasan....sorry I couldn't help - I just saw the thread.  I have the EXACT same laptop as you and actually had this tuff someplace in a text-document (in-case my memory fades).

It's great to see someone come back to linux after the battle.  I have not used windows in over 3 years and I'm sure most here will tell you that once you go linux (and get it figured out) you'll never let yourself get tied down to windows ever again.

---

### Post by jason.b.c on 2006-04-04
Posted by **Stew2**

> Hang in there! You will get it!  You definitely get an "A" for effort! 

Yes, I would agree, What a real trooper you are **Papa San** Good for you.!

:D

---

### Post by wishy77 on 2006-04-05
Papa San..**Congratulations for your grit and determination**....well done.
Also to all the forum helpers..great assistance from everywhere.
I too am a new linux/ubuntu user and have found the forums great assistance.
I went back to XP twice..purely out of frustration, but kept on coming back and persevering and now happily run 100% Ubuntu Breezy, and am looking forward to Dapper.
 I am in the senior citizen category as well but thought if I could learn to wrestle with DOS commands and DBase3 commands and GWBasic back in the 80's surely I could "wrap my head" around a better OS.

Congrats again.
Wishy

---

### Post by henriquemaia on 2006-04-05
[QUOTE=Papa-san]I love this forum... no flaming here!

[/QUOTE]

- Off topic -

Quite true. This community is amazing. Even when the subject matter is somewhat controversial, things manage to flow without flame wars.

Sorry for this off topic remark. Good luck on your linux adventure.

---

### Post by duality on 2006-04-06
Heres how you do the most essential stuff;:
[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

you will probably find stuff here too:
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)


good luck

---

