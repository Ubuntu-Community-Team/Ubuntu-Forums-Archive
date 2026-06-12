---
title: "Could you guys reccomend a linux or unix book?"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by pettybone on 2007-03-13
To be honest with you guys, I am not getting the documentation that unbuntu has provided. I am an extreem windows power user who knows how to edit my registry, make batch files, and msi files. There is no real reason for me to come to linux except I want to gain a better understanding of operating systemss in general. 

On unbuntu I am just not getting anything, not one bit. Every bit of documentation that is provided assummes that I know what I am doing. I don't know where to type in these commands that every tells me. To type in the commands I need to type gconf -editor but where do I type that in. What is the difference between a konsole and a terminal.  Why is this not in the add/remove programs [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/apt.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/apt.html)  "
 To update the local list of packages, enter in a Terminal: 

sudo apt-get update

To install all available updates:

sudo apt-get upgrade

To install a package:

sudo apt-get install package

To remove a package:

sudo apt-get remove package

To list other apt commands and options:

apt-get help". Where do I run that after it is installed?

Where is there a basic desktop configuration document? I thought If I try and install a windows theme I might be able to procced a little further. I went here "lxp.sourceforge.net/download.html. I installed it but it didn't list it self under theme which I thought the auto install was self relient and was supposed to do that for me.

I just don't see how the "A comprehensive guide to using Ubuntu in a desktop environment."
is formatted for a beginer. Things that I come accross that I am needing are how to use KWLAN, how to change my resolution, how to make my machine act more like a windows, and  how to use to begining forums when they are made for someone who understands what they are doing already.

Maybe I am just ranting and the things I am saying are completly wrong but I don't seem to find any explinations on the ubuntu forum that prove me wrong. I am left at buying a book to find explanations on what is what and why these things do what they do(command wise).
Please help. I don't want to give up. I need direction from a book I guess and hope someone can give me offer some recommendations.

Sorry for my rant, I just seem to be going in circles.

thanks,
petty:confused: :confused: :confused:


PS: I understand the networking basics and when I use kwlan tha acronyms aren't matching up with what is on my router. I found a link to set up my wifi but that too didn't help me.

---

### Post by jrusso2 on 2007-03-13
This one is supposed to be good for the new user

[http://www.amazon.com/Moving-Ubuntu-Linux-Marcel-Gagn%C3%A9/dp/032142722X](http://www.amazon.com/Moving-Ubuntu-Linux-Marcel-Gagn%C3%A9/dp/032142722X)

Jeanette

---

### Post by hrp2171 on 2007-03-13
pettybone, that is exactly how I felt at the beginning with Linux.  At first, I had to deal with the "RTFM" crowd.  Then, once I found [www.tldp.org](www.tldp.org), it was outdated information that would not even relate to what I was trying to accomplish.  I still read through some of the HOWTOs, though.  That's where I ran into the "Check also this HOWTO" links.  So from then on, it was about jumping from document source to document source.  All along trying to piece together a solution or anwser to my question.  That was about 10 years ago.  The crosslinking amongst HOWTOs, walk-thrus and tutorials has gotten worse.  And now it's essential part of forums, too. :confused: 

The best thing to do is read generic HOWTOs or tutorials about a single subject.  For example, I've read lots of HOWTOs on bash related topics.  They were a lot of help and it should still apply to today's graphical Linux desktops(i.e. Ubuntu, Fedora, etc).  Lastly, thank goodness for [www.google.com/linux](www.google.com/linux) ! :)

---

### Post by kolinab on 2007-03-13
Hey pettybone,

There are some simple, clear pages at [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) that helped me out a lot when I was starting out. I had the same problems as you; I was a Windows power user from days gone by, but when people said things like 'Just type gksudo gedit /etc/blahblah' I was lost. Type it where?! haha

The terminal can be accessed through Applications . . . Accessories . . . Terminal. One thing I do right away to make the terminal more accessible is to make a Launcher (think shortcut) on my panel (think toolbar). Right click an empty space on the top panel, and click 'Add to Panel.' Then select 'Application Launcher,' and find the icon for Terminal under Accessories. This way the terminal is only a click away. To be honest, I really don't end up using the terminal all that often, but it's nice to have sometimes.

Try these help links as well if you haven't already:

[http://www.ubuntu.com/community](http://www.ubuntu.com/community)

[https://help.ubuntu.com/](https://help.ubuntu.com/)

Keep asking your particular (and general!) questions here - this is where I learn the most!

Good luck,

K

---

### Post by pettybone on 2007-03-13
Wanted to thank you guys for the support. I plan on trying both the link you gave me and the book jeanette said to try. ](*,) If anyone has tried this book and think I should choose something else please let me know. Going to buy something off amazon tomorrow.

---

### Post by kolinab on 2007-03-13
I also have a copy here on my computer of 'The Official Ubuntu Book.' I can't remember where I downloaded it from. It's about an 11mb file. Let me know and I'd be happy to send it to you.

---

### Post by 2muchtq on 2007-03-13
I'd be up for you sending that to me.  I also am lost....  I've searched most of my problems and figured them out... but still am lost.




Thank You
Mark

---

### Post by 2muchtq on 2007-03-13
Kolin, Thanks for the help!

I think I may be able to get the .chm to work.

---

### Post by 2muchtq on 2007-03-13
CHM Viewer installed and working perfectly.


Thanks again.



Side note.  Is there a difference between synaptic and add/remove programs??

---

### Post by kolinab on 2007-03-13
No problem, happy to help.

```

sudo aptitude install gnochm

```

sould work to install the chm viewer.

Man, I need to get a hobby or something. oh wait. . .  :)

---

### Post by kolinab on 2007-03-13
ha, looks like we simulposted.

I've never looked at add/remove programs before. It looks prettier. Looks like it explains a little more. I had kind of forgotten it was there. Kind of a little easier I guess to search for a program to do a particular task. When I'm looking for something and I know what it's called, I always just search for it in synaptic. And sometimes if I already know what it's called I just install it from the terminal. That gives me a real kick. haha

---

