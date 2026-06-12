---
title: "Problems running Xubuntu Desktop CD"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by paulohy on 2007-06-18
Hi, my name is Paul, I'm from Brazil.
I'm having some problems with Xubuntu, so I posted it on Ubuntu forum in Portuguese.
Since they didn't help me so much I decided to post my problem here. So, sorry if my English is not so clear.
;)


I want to install Xubuntu on an old slow computer that I have (128Mb RAM - 20Gb HD, about 10Gb free - 850MHz)
So, I downloaded the Xubuntu 7.04 desktop CD iso and burnt it on a CD.
I boot the computer and the black screen with the Xubuntu menu appeared.
First I selected 'check for errors' or something-like-that. There were no errors on the CD.
Then I chose the "Run or install Xubuntu" option. It went to that loading screen (black background, Xubuntu logo above the blue loading bar).
When the bar is load, the mouse cursor appears (responding to the mouse movement) and the background changes to blue
Till then I think it's pretty much what it's supposed to be, but the problem is that it doesn't happen anything after that! I left the computer for about 2 hours and the same blue screen was still there!

Is there anyone who can help me?

---

### Post by st33med on 2007-06-18
You mean no taskbars or Icons??? Weird. 

Try Safe Graphics Mode when you get on the Cd.

---

### Post by paulohy on 2007-06-18
In safe graphics mode the same thing happens...

---

### Post by RedSquirrel on 2007-06-18
I would try the Alternate install CD (not the Desktop CD).

---

### Post by paulohy on 2007-06-18
Yeah, I've heard about this Alternate CD...

The problem is that I'm not so sure I want to install Linux on this computer. I just wanted to try it to see if it works well, but if I use the Alternate CD, I won't have this option, I would have to install it.
I think I'm gonna have to buy some RAM for this computer...

But thank you anyway...
:)

---

### Post by st33med on 2007-06-18
Trust us [hypnotize]*you will enjoy it!*[/hypnotize]

---

### Post by RedSquirrel on 2007-06-18
> **paulohy said:**
> Yeah, I've heard about this Alternate CD...

The problem is that I'm not so sure I want to install Linux on this computer. I just wanted to try it to see if it works well, but if I use the Alternate CD, I won't have this option, I would have to install it.
I think I'm gonna have to buy some RAM for this computer...

But thank you anyway...
:)

No problem. It's just that your RAM is right on the border of being able to run the Xubuntu LiveCD (Desktop), and you would need to have 192 MB to install using that Desktop CD.

Here are the system requirements:

[http://www.xubuntu.org/get#requirements](http://www.xubuntu.org/get#requirements)

You might want to look at DSL also. That should run in RAM, but bear in mind that it uses the Fluxbox window manager which may be a little different from what you're used to...

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

Have fun! :D


EDIT: Of course, adding more RAM would help if it's not too much trouble. ;)

---

### Post by jamesbousman on 2007-06-19
The only way that I was able to install Ubuntu on my HP Laptop was to install Xubuntu first and then install Ubuntu on top of it.

However I do not know anything about anything. I was just hacking at it and that is what worked for me.

---

### Post by Haus Neuerburg on 2007-06-23
Hi paulohy,
did you ever try to download a new iso-image and burn a new cd? Because my computer has 128MB RAM only, too and the live CD worked fine (well, given the time you needed to see a command or mouse-click fulfilled ;-)). At least I could check what xubuntu might be like and what it looks like. I did not manage to install from it-due lack of RAM, but after I had decided I wanted xubuntu I took the alternate cd for the installing and that worked fine. I have 4 GB HDD and only 128MB RAM, but almost everything is fine now (I'm an absolutely newbie still)
Well, maybe you've solved your problem already?
Rgds Haus Neuerburg from Germany
P.S. I experienced the same in the German forum: no real answers to questions, all I read was: this is not Windows, why do you have Linux if you can't handle it?!
Ooops, forgot, installed Dapper not Feisty...maybe you try that?

---

### Post by egroeg85 on 2007-06-28
I'm having the same problem.  Computer is getting pretty old. It has I think 256MB RAM.  Pentium II.  Boots Windows XP fine.  Boots Puppy Linux fine.  Unfortunately, Puppy is still too complicated for my mother (who owns this computer).  Xubuntu seems to be loading great, but it gets to the blue screen, loads no icons or bars, and stops there.  The CD drive keeps working as if its trying to load something else, but after maybe 20 minutes the screen just goes black and it stays that way.  I know the CD is fine because I loaded it on another computer.  It just seems strange to me because it makes it through the load screen fine, and it loads x fine, but then it stops there.  

-Seth G.

---

### Post by Outrunner on 2007-06-28
Hey, I have an idea, which I *assume* will work(it should, in theory). Basically, download the Gparted LiveCD from my signature and burn it to a disk - it's only about 60 MBs, shouldn't take long. Now, what you should do is boot into the Gparted LiveCD and resize one of your partitions so that 1 GB of space remain unallocated. Then turn this 1 GB (format) to 'swap'. Basically, this is extra RAM in hard drive form, I guess you could say... Hopefully, when you boot into the Xubuntu LiveCD again it will detect this swap partition and use it. You would need to create this anyway, if you want to install Xubuntu, so it's not a waste of space - just thought I'd let you know.

EDIT: VERY IMPORTANT!! First, defragment the partition you are going to resize(you don't want to lose any data, after all). Do it at least twice

---

