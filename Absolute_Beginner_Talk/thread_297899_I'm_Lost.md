---
title: "I'm Lost"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by lylesiemens on 2006-11-11
](*,) I'm very new here and have a great grasp og Windows XP and MAC, but not Linux. Like trying to install Gparted, how do you do it step by step for dummies like me. It's on my desktop and have opened it, now what??? Everything I download for Ubuntu does not open or run without an error. Everything is an error. I have tried to use terminal for copy-paste jobs but nothing happens. I have no idea if my ATI Radeon 9250 PCI Pro even works on here because I can't configure it at all. I can't access my D drive at all it is locked and opens with nothing. Ubuntu is on my C drive and my D drive just has old Window files like songs and videos not XP itself. I want XP too, I have tried using VMware. How does it work, it gives me no options to do anything. I tried Win4lin and get an error when opened saying that it's not configured properly, I cut and pasted everything that I was instructed to do in terminal. I don't want to give up yet. My gamepad does not configure after my second install of Umbuntu. Help please help with the basics, if any one has any answers or can offer any help for anything I mentioned, PLEASE HELP!!](*,) :confused:

---

### Post by digby on 2006-11-11
Woah!  Slow down!  That's a lot of problems to solve at once!  We'll be very glad to help you, but let's tackle these issues one at a time for the sake of our sanity! :mrgreen:

I'll tackle the first thing you mentioned here, then after that's fixed, just tell us what's next and we'll get you through that.

There are several ways to install software in ubuntu.  You can find an excellent guide about using the command line to install things [here.]("http://www.psychocats.net/ubuntu/installingsoftware.php")

If you aren't quite sure about using the command line, there is a graphical tool to do the same thing called synaptic.  You can find it by looking under the System Menu > Administration > Synaptic Package Manager.

Searching through that for gparted will make it very simple to install. 

Did that all make sense?  If so, what's next?

---

### Post by d3v1ant_0n3 on 2006-11-11
First off...calm down, breathe deeply. I know what you're feeling, it's scary and confusing as hell at first, and so alien. More so if you're proficient with other OS's, because they all do things differently.

A good place to start (and many of your answers can be found here too) is [HERE](http://www.psychocats.net/ubuntu/index) -Lots of good howtos and explanations.

For gparted, copy and paste the following into the terminal:
sudo aptitude update
sudo aptitude install gparted

That's 2 commands, one after the other


The first one will update your repositories (the list of software you can download and install). The second command will download and install Gparted for you.

You shouldn't need to hunt down and install software from the web- That's what the repos are for. If you look in your menu, there should be an 'Add/Remove' option. This will allow you to search through all the programs you can install, and install them:D  A more advanced version can be found in System>Administration>Synaptic Package Manager.

I hope this has been of some help!

Good luck!


*edit* digby, stop answering things more concisely and faster than me dammit:p

---

### Post by taurus on 2006-11-11
Try to break up your questions in an easy way for others to follow!!!

For gparted:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

For mounting Windows:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by digby on 2006-11-11
> **d3v1ant_0n3 said:**
> digby, stop answering things more concisely and faster than me dammit:p

Haha!  Maybe we should request some sort of ticket system... when you try to reply to someone you get a message along the lines of, "Someone is already with this one.  Get your own thread!"

:mrgreen:

---

### Post by podunk on 2006-11-11
Welcome! I see you met the mascot already! ---> ](*,)   :)

This is a very good page:
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

This is a very basic starters guide to Linux:
[http://tldp.org/LDP/intro-linux/html/index.html](http://tldp.org/LDP/intro-linux/html/index.html)

A quick read will answer a lot of your questions, there are practice exercises at the end of each section, but if you Skip those for now and come back to it later it is a quick read.

Some of the stuff you want to do is a little advanced. Why don't you get to enjoy your computer? Install all the updates, find a radio station or 2, get your movie player going, a few games, stuff like that. Then branch out to the harder stuff.

---

### Post by lylesiemens on 2006-11-11
FM radio doesn't even work and yes I used add/remove program, I get the Could not open device "/dev/radio0" !

Check your Settings and make sure that no other
program is using /dev/radio0.
Make also sure that you have read-access to it. error 
So where can I find Gparted after it's installed? I used terminal

---

### Post by taurus on 2006-11-11
```
sudo aptitude install gparted
```

---

### Post by digby on 2006-11-11
> **lylesiemens said:**
> FM radio doesn't even work and yes I used add/remove program, I get the Could not open device "/dev/radio0" !

Check your Settings and make sure that no other
program is using /dev/radio0.
Make also sure that you have read-access to it. error 
So where can I find Gparted after it's installed? I used terminal

After it's installed, gparted will be in /usr/bin which is in your path, so you can start it at anytime with 'sudo gparted'

Sorry, but I don't know a thing about radio in linux.

---

### Post by lylesiemens on 2006-11-11
So how do I get sudo gparted to run now, it seems installed but where can I find it to run it?

---

### Post by d3v1ant_0n3 on 2006-11-11
> **lylesiemens said:**
> So how do I get sudo gparted to run now, it seems installed but where can I find it to run it?

System>Administration>GNOME Partition Editor

---

### Post by lylesiemens on 2006-11-12
OK I have Gparted running but it won't let me resize the hard drive it is greyed out no matter what. Can I install windows on the extra partition if I can get it working?

---

### Post by taurus on 2006-11-12
If you want to resize your harddrive, you need to run gparted from the LiveCD!!!

---

### Post by digby on 2006-11-12
You can't resize a partition while it is mounted (active).  Will what you are doing affect the size of one of your linux partitions?

---

### Post by lylesiemens on 2006-11-12
I can't boot from the live cd, I get an error that the graphics are not configured properly or something to that effect. It's a blue screen](*,)

---

### Post by digby on 2006-11-12
This [live cd]("http://gparted.sourceforge.net/livecd.php") might work for you... it's designed specifically for disk management tasks and is very small.

---

### Post by lylesiemens on 2006-11-12
Can I access my D drive in any way, it appears locked out and won't open.

---

### Post by lylesiemens on 2006-11-12
Is there any way to access my D drive, it appears locked. I know where it is but won't open, I get an error.

---

### Post by bulldog on 2006-11-12
> **lylesiemens said:**
> Is there any way to access my D drive, it appears locked. I know where it is but won't open, I get an error.


I hate to say this,really I do,but maybe it's better to reconsider if you want Ubuntu.

---

### Post by lylesiemens on 2006-11-12
So I take it I can't open media in my D drive. My 320 gig usb drive opens easy and can play and see everything on it. My D drive was just my second internal hard drive.:confused:

---

### Post by digby on 2006-11-12
What is your D drive called in linux?  it should be something like /dev/hdb or something along those lines.

---

