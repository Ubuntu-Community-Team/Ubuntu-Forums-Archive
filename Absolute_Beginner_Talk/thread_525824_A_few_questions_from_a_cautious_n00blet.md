---
title: "A few questions from a cautious n00blet"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by Sucker Punch on 2007-08-14
Over the past little while, I've become increasingly curious about trying this whole "Linux" thing out.   With all the great press Ubuntu has been getting, I figured this would be the best place to start.

I've got a couple very simple reasons for trying the switch.

1. I'm just interested in how it works.
2. I'm studying for a degree in computer science.   With Linux becoming more and more popular in professional applications, I figure it can't hurt to familiarize myself with it.   There's no such thing as too much knowledge, right?

I do have a couple stumbling blocks.   I am not familiar in the slightest with Linux at al,l let alone Ubuntu.   I've never used a system running it before.   When I was a kid, the old man was some kind of computer expert, so command prompts don't intimidate me, but a decade of Windows isn't going to help me much here.    I do have a second desktop, so I'm not too concerned about trying Ubuntu.   If things go to hell, I can use that to get help, or I could always just reinstall XP.

I've looked around a little, but haven't found answers to a couple questions (likely because its probably common knowledge for anyone at all familiar with Linux based systems).

1. How concerned do I have to be with drivers?   I'd be installing this on a Toshiba notebook with Intel hardware.   Will I have difficulty getting my DVD burner, wireless NIC, video adapter, etc working?

2. How much support is there for windows based applications?   I use this mostly for school (internet, word processing, a little programming in Java/C), but I do have a couple games.   I understand that specifics would likely be necessary for this kind of question, but should I go into this expecting to be completely Windows-less?

I'm sure I'll have more questions as I get a little deeper into this, but I mainly just want to make sure that I'll be able to run all the basics when I swap it over.

Thanks for any insight.

---

### Post by bren on 2007-08-14
re your questions

1) most of it maybe all will just work.    people here will help you get any bits that don't going.   all the kit you mention is in general very well supported

2) there are two approaches here
a) dual boot -easy to set up via the standard installler
b) VMware - run an emulator of XP within Linux (haven't managed to do this myself yet but many do....)

i've only been a ubuntu user for a short time but am very impressed and only go back to   xp v rarely now....

bren

---

### Post by jrusso2 on 2007-08-14
The main problems with laptops seems to be the wireless.  If you know the mfg of the wireless chipset you can look and see if it is supported natively.  Atheros and Intel based are two of the easier and most common to get working.  You can also use ndiswrapper to get other types of wireless working.

As far as support for windows apps you need to run it either in a virtual machine like vmare or virtual box or you can try your luck with WINE which is an api layer that will run some windows applications.

---

### Post by PCFascist on 2007-08-14
Information on how well Linux will play with your laptop is here:
[http://www.linux-laptop.net/](http://www.linux-laptop.net/)

Information on how well Wine will run your Windows programs is here: 
[http://appdb.winehq.org/](http://appdb.winehq.org/)

If it is really important to run windows programs you could always buy crossover from [http://www.codeweavers.com/](http://www.codeweavers.com/)
I think it is a good price.

You could also install VM Ware so you could run your windows OS of choice in the virtual machine.

---

### Post by Blutack on 2007-08-14
1)  Dvd burners always work, video adapter...Intel, yes, Nvidia, yes, ATI, maybe not accelerated, anything weird google it.  But pretty much anything will give you a gui, if you wanted accelerated desktop effects - the compiz stuff everyone goes on about - an Intel or Nvidia are your best bet.  Ethernet probably ok, wireless NIC massively dependant on model - some out of the box, others a bit more tricky.

2)  You can't run windows apps on linux easily, although many can be used though wine
[http://www.winehq.org/](http://www.winehq.org/) (also applies to games).  However, OpenOffice works with office files (.doc,.xml), and can make pdf's.  Programmming you are spoilt for choice.

Best thing to do is just download it, try the live cd and if you like it install it.

---

### Post by Sucker Punch on 2007-08-14
Wow, that was quick. :)

Thanks a lot guys, I appreciate the help.   Now I just have to wait 2 hours for the thing to download.

EDIT: Thought of something else.

I read somewhere here that Lexmark printers are iffy at best when running Linux.   As I said, I do have another desktop that will stay with XP.

How difficult is it to set up filesharing between computers on a network when one is running Windows and one is running Linux?   I figure transferring anything I need printed (or whatever I need XP for) over to the other computer then dealing with it there would get past any issues.

But are there any major stumbling blocks with doing that?

---

### Post by bren on 2007-08-14
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

use samba to connect windows and ubuntu (although ubuntu can see windows network by default, samba is needed for the other way around .... i think...)

bren

---

### Post by Sucker Punch on 2007-08-14
> **bren said:**
> [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

use samba to connect windows and ubuntu (although ubuntu can see windows network by default, samba is needed for the other way around .... i think...)

bren

Awesome.   So far so good.   From what I've read from the links you guys have provided for me, it seems most of the hardware should function (relatively) easily with Ubuntu.

Thanks again.

---

### Post by Sucker Punch on 2007-08-14
Just wanted to thank everyone.   I've got Ubuntu installed, everything (including internet) went perfectly.

And strangely, despite all the scary things said about linux, this was a lot faster and easier to install than Windows.

---

### Post by buzzmandt on 2007-08-14
welcome to linux  :)
and ubuntu

---

### Post by bren on 2007-08-14
> a lot faster and easier .... than Windows.

you had better get used to it!

bren

---

### Post by kevinlyfellow on 2007-08-14
> **Sucker Punch said:**
> Just wanted to thank everyone.   I've got Ubuntu installed, everything (including internet) went perfectly.

And strangely, despite all the scary things said about linux, this was a lot faster and easier to install than Windows.

And that's why you hear linux users shouting the word FUD!!! all the time.  :-)  Enjoy linux

---

