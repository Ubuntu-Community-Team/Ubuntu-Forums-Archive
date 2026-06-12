---
title: "Is it really this difficult?"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by spacedogg on 2006-01-01
Hello all. I'm new to Ubuntu and the whole Linux scene, all the computers I have owned are windows machines. I've seen Linux Red Hat and a few Solaris things, but never cared to learn to much about Linux/Unix. MaximumPC Magazine did an article this month about Ubuntu and I figured I'd give it a try. It seemed easy enough to install, and it's time I learned something new. 

So I cruise over to Ubuntulinux.net, download the live CD and give it a try. I was pretty impressed with how easy it was to install. Much easier to install than windows I thought. (but what the heck is LVM during the partitioning section?)

I remove my cd, the install finishes and up comes this beautiful brown screen. Cool, my first linux distro. I start digging around and what do I find? Tetravex, that's right, Tetravex. I love that game and I can't find it anywhere for windows. I'm feeling pretty good at this point and I plug in my wireless card (it's a laptop) and Ubuntu doesn't reconigize my pcmcia card. Time to do some research. 

I google my card and it seems that there are no Linux drivers for a Linksys WPC54G Ver 1.2 notebook adapter. Then I find a post about a program called ndiswrapper that may be able to help. I download ndiswrapper-1.7.tar.gz file from sourceforge on my windows machine. I put it on my usb key, plug my usb key into my laptop and drag ndiswrapper to my Ubuntu desktop. 

Reading the directions located in the folder, I find that I am in a very different environment indeed. There is no .exe to install the program. I go to the command window and type in what it says in the install instructions. I get "can't find directory" message no matter what I try in the command window.

Question: Is there some directory that I should drag the folder to so that the console can "see" that the folder exists?

Then I try synaptic to install the program, but theres no way to change the directory in synapic that I could find. 

Can someone help me out here, I'm a bit frustrated, but I'd really like to learn this new OS.

Question: How do I change directories in the command window? 

Question: Is there a website that has Linux commands for the command window?

Any help anyone could give me would be great.

Nate

---

### Post by kaamos on 2006-01-01
Hello!

[QUOTE=spacedogg]I google my card and it seems that there are no Linux drivers for a Linksys WPC54G Ver 1.2 notebook adapter. Then I find a post about a program called ndiswrapper that may be able to help. I download ndiswrapper-1.7.tar.gz file from sourceforge on my windows machine. I put it on my usb key, plug my usb key into my laptop and drag ndiswrapper to my Ubuntu desktop. [/quote]
Ndiswrapper is included in the ubuntu cd. So make sure the cd is your drive, open synaptic, search for "ndiswrapper" and choose it to be installed. Click apply and synaptic will install the package from the cd.

You still need the windows .inf file though.
[QUOTE=spacedogg]Question: How do I change directories in the command window?  [/quote]
```
cd foo
```
this changes to the directory "**foo**".
```
cd ..
```
This changes one directory down the tree. So if you are in **/home/username/foo** you end up in **/home/username**
```
cd
```
Changes to the home directory. That is** /home/username**

[QUOTE=spacedogg]Question: Is there a website that has Linux commands for the command window? [/quote]
Someone will certainly come up with a good link.. Before that, google is your friend.

Hope this helps and welcome to ubuntu. :)

---

### Post by Omnios on 2006-01-01
Here is my terminal command links thread.

[http://ubuntuforums.org/showthread.php?t=45651&highlight=commands]("http://ubuntuforums.org/showthread.php?t=45651&highlight=commands")

---

### Post by spacedogg on 2006-01-01
[QUOTE=kaamos]Hello!


Ndiswrapper is included in the ubuntu cd. So make sure the cd is your drive, open synaptic, search for "ndiswrapper" and choose it to be installed. Click apply and synaptic will install the package from the cd.

You still need the windows .inf file though.

```
cd foo
```
this changes to the directory "**foo**".
```
cd ..
```
This changes one directory down the tree. So if you are in **/home/username/foo** you end up in **/home/username**
```
cd
```
Changes to the home directory. That is** /home/username**


Someone will certainly come up with a good link.. Before that, google is your friend.

Hope this helps and welcome to ubuntu. :)[/QUOTE]

Thanks for the help! Well I'm trying to install the most current version of ndiswrapper, which is ndiswrapper. I saw that Synaptic had 1.1 so I figured that it would be better to install the newest version. 

I have a folder on my "desktop" named ndiswrapper-1.7 which I extracted from the .tar.gz file that was on my USB key. I just need to know how to go about getting to that directory in a terminal window. cd desktop doesn't work. I think the current directory is nathan@ubuntu:~$ at least that's what is before the cursor is sitting next too. 

I also have the .inf file as well. I knew that I'd need that from the googling that I did. 

I do the command ls which only lists Desktop under it. Is that my current directory? 

The instructions say to log in as root, but can I just precede sudo with any commmand for it to work as the Super User?

---

### Post by Gimbo on 2006-01-01
With the cd command, ~ is a shortcut to /home/user, where user is your username. So the way to get to your Desktop folder is:

```
cd ~/Desktop
```

---

### Post by phido on 2006-01-01
You are in your /home/user directory and the command for Desktop ist cd **D**esktop (unix is case sensitive).
Sudo works fine for Super User.

And a nice introducing to the shell can be found here [http://linuxcommand.org/]("http://linuxcommand.org/")

h2h

---

### Post by kaamos on 2006-01-01
Linux commads are case sensitive. So "cd desktop" is different from "cd Desktop", and the latter is what you are probably looking for.

However, ndiswrapper is a kernel module which means that in order for you to be able to compile it you need the to have kernel headers installed. And also ubuntu 5.10 for some reason ships with a different compiler than by default is needed to compile the kernel module. This is very quickly fixed by installing a few packages *if* you have internet access.. But in this case I recommed that you install the ndiswrapper version from the cd. If that does not work, you can then uninstall that and install the 1.7 version.

This is not really as difficult as it sounds, you just chose a hard way to start. :) Wireless is at the moment a bit tricky in linux since the support from hardware vendows is quite nonexistant. There are wifi-cards that work out of the box, but for most cards this is not the case yet.
> The instructions say to log in as root, but can I just precede sudo with any commmand for it to work as the Super User?
Yes, sudo does the same thing. If you for some reason need to log in as root, you can use "sudo su".

---

### Post by TeeAhr1 on 2006-01-01
[QUOTE=spacedogg]Question: Is there a website that has Linux commands for the command window?[/QUOTE]
Got something better for you.  Bet you didn't know that Linux comes with a user guide, did you?  It's time for you to meet the *man*!

In the terminal, *man foo* will show you the manual page for the command *foo*.  Try it out with *man man*.  The Gnome help interface also includes the man pages, but I find it faster to look through the terminal.

Then there are *man*'s lesser-known yet mighty cousins, help, info, apropos, and whatis.  One at a time:

*foo --help* will display a brief help summary for the command *foo*.  This is very useful when you know what a command does, and just need to see the list of arguements.

*info foo* will bring up the info page for *foo*.  This is like *man* on steroids, great for when the man page doesn't provide the info you're looking for on a command.

*apropos foo*.  Oh, behold the wonder of *apropos*.  All the manpages have brief descriptions of what the command does.  *apropos foo* will search these descriptions for instances of the keyword *foo* and return a list of matches.  To see, for instance, all manpages relating to the word wireless, enter *apropos wireless*.

*whatis foo* is very similar to apropos, but rather than search the descriptions, it searches the manpage names.  *whatis foo* will find all instances of foo in all manpage titles.  (thanks to phido for the gentle nudge ;))  Question: Okay, now I think I know what it does, but I don't totally understand the function.  What's this for?  Can someone post an example of an appropriate use for whatis?

---

### Post by phido on 2006-01-01
> *whatis*  I don't know exactly what whatis does, but I'm sure someone here does... 
man whatis
whatis man ;)

---

### Post by TeeAhr1 on 2006-01-01
Smartass ;)   Previous post updated.

---

### Post by Mustard on 2006-01-01
Here is a HOW TO on compiling the latest ndiswrapper that I just noticed ..

[http://www.ubuntuforums.org/showthread.php?t=104539](http://www.ubuntuforums.org/showthread.php?t=104539)

---

### Post by spacedogg on 2006-01-01
I installed the ndis version form the disk. Figured what do things the hard way just coming out the gate. 

Now I need to figure out how to use ndiswrapper to load the .inf file for my card. These a few post I've found that deal with this, so off to reading. 

Thanks again for all the help, it's very nice to be well received like this.

---

### Post by Madpilot on 2006-01-02
Just to continue the threadjacking about man & apropos - according to "info man", adding the "-k" switch to *man* is the same as using *apropos* - so *man -k foo* is identical to *apropos foo*.

Likewise, *man -f foo* = *whatis foo*.

The wiki has a good basic CLI page: [https://wiki.ubuntu.com/BasicCommands](https://wiki.ubuntu.com/BasicCommands)

(Which I've just updated to include the apropos/man/whatis info from this thread - thanks!)

---

### Post by Mustard on 2006-01-02
An ndiswrapper HOW TO...

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

---

