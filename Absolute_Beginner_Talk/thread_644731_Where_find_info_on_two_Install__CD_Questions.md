---
title: "Where find info on two Install / CD Questions"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by tmcdlive on 2007-12-19
Am brand new to Ubuntu and have the proverbial dumb questions(2 of them) to ask about Installation.... actually I figure that information is available somewhere if someone can give me a web-address for the answers because I can not find it but figure it must be there somewhere.

FYI - Hardware --- PC devoted to Linux - bought one of the Everex gOS PC machines and absolutely hate the gOS Distro that it comes with.  I tried Ubuntu on a Live-CD and fell in love with Ubuntu.


Question A: ---  I have the CD booted up and is working ... when I shutdown, am I safe in assuming the program will save the information and adjustments I tweaked on a file on the machine's hard-drive?  


Question B ---  I notice that both the boot up choices and on the desktop show  selections for "installing" Ubuntu ... I want to find out what will happen if I select one of those.  

I would like Ubuntu on the hard drive so I can use Ubuntu or get back into gOS if I need to for some reason and free up the CD (and boot up faster).  Where will I find something to read (instructions) that will explain?  I need the "KISS" principle on this one.  I don't want want to "press the button" without having some idea of what I am about to do when I do it.

Thanks for any help ... and have a great holiday season to everyone.

---

### Post by hyper_ch on 2007-12-19
Well, I assume you have the live CD. When you start that, it will boot into Ubuntu Desktop but everything is loaded from the CD (makes it slow). When you power down, all your changes go to nirvana (or as we geeks prefer to say to  /dev/null)

As long as you don't mount and of your harddisks during the live session and alter them, nothing will be done on your system.

Once you booted up the Live CD, it has an icon on the Desktop where you can to perform the actual installation! Have a look here:  [http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon)

In order to install ubuntu you'll first need to free up some of your diskspace. in gOS you should have a partitioner somewhere. Use that to make existing partitions smaller and free that space. Do not partition it... just leave it unallocated!

During the installation process then of Ubuntu, you'll be asked where you want to install it. Select the "USE LARGEST CONTINOUUSE EMPTY SPACE" or something like that. DO NOT USE THE "USE ENTIRE DISK" option. That one will erase everything!!!

If you don't see the largest continouuse emtpy space entry, make a screen shot and post it here.

---

### Post by machosos on 2007-12-19
Don't mean to overtake your thread or anything but I had a few questions that kind of is linked to this...if i click on the manual partition part for step four in the next page do i just click on "New partition table" to keep my windows XP and be able to dual boot?

Thanks everyone

---

### Post by hyper_ch on 2007-12-19
Well, depends on how you have setup your system before.... you will need to create new partitions for linux and eventually resize the windows one.

---

### Post by tmcdlive on 2007-12-20
hyper_ch,  Thanks for the advice ... it sounds great ... I will try it.

To Everyone ... have a Wonderful Holiday Season !

---

### Post by tmcdlive on 2007-12-22
Hyper CH ... I am replying to your suggestions shown here... the reply is after this quote:
------------------------------------------------------------------------------------------

> **hyper_ch said:**
> Well, I assume you have the live CD. When you start that, it will boot into Ubuntu Desktop but everything is loaded from the CD (makes it slow). When you power down, all your changes go to nirvana (or as we geeks prefer to say to  /dev/null)

As long as you don't mount and of your harddisks during the live session and alter them, nothing will be done on your system.

Once you booted up the Live CD, it has an icon on the Desktop where you can to perform the actual installation! Have a look here:  [http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon)

In order to install ubuntu you'll first need to free up some of your diskspace. in gOS you should have a partitioner somewhere. Use that to make existing partitions smaller and free that space. Do not partition it... just leave it unallocated!

During the installation process then of Ubuntu, you'll be asked where you want to install it. Select the "USE LARGEST CONTINOUUSE EMPTY SPACE" or something like that. DO NOT USE THE "USE ENTIRE DISK" option. That one will erase everything!!!

If you don't see the largest continouuse emtpy space entry, make a screen shot and post it here.


-----------------------------------------------------------------------------------------------
Reply:

Installing is going nicely under your suggestions but I want to double check something you said to be very careful about ... "USE LARGEST CONTINUOUS SPACE".

I am posting/attaching a Picture of the partition screen here ... I got to a screen that wants to partition the hard-drive.  it is 80 gig...  1.25 gig is Partition 2 and the rest is all one big partition (Partition 1).  The Total free space not used by files in Partition 1 is just over 69 Gig.  

You should find a screen shot attached called ... screenshot-install page 4 of 7.png

It is WORDED slightly different than what you suggested to watch for and is out of sequence from the help screens you recommended, so I figured I should check before I mess up.

Question ... What do I select?  

I suspect the first line about guided resize.

Question ... if yes, should I let the program use the 53.7 Gig that it suggests?  Or would I change the slider to all of the drive so it is more in line with your original instructions?

What the program suggests would leave roughly 16 gig unused In what I presume would be called Partition 3 or 4 or some something like that
.

Question ... would I then just say yes to all further questions / suggestions the program makes?  

A Later screen in the tutorial you suggested mentions a swap partition in the picture in step 7 of 7.


One last question ... is there a way to avoid using a password?  This machine is in my office at home and no one has access to it but me.

Thanks for your help ... Have a wonderful Holiday Season ... ENJOY IT!!!!!

Best regards,
TMCDLIVE

---

### Post by hyper_ch on 2007-12-22
That's the right option with the resize.

there is no way for no password, however you can make auto-login...

---

### Post by barbedsaber on 2007-12-22
just a tip, whenever you install an opperating system, partion a hard drive, or do anything significant, you really should make backups (nag nag nag) :lolflag:Also, if it all works succesfully, can you please mark the trhead as solved, you do this by clicking on thread tools and shosing mark thread as solved.

---

### Post by tmcdlive on 2007-12-22
> **hyper_ch said:**
> That's the right option with the resize.

there is no way for no password, however you can make auto-login...


Hyper_CH  ...  Thanks ...

A)  If I understand correctly,  I should change the partition it wants to make and move it from the 37 Gig (about half) to the full amount left 69 Gig or so.

B)  Thanks for the tip about Auto Log-in ... I have not run across it yet but will find it and set it up.

Thanks much!

---

### Post by hyper_ch on 2007-12-22
no, currently the whole 70 gigs are used by windows... and you resize it so that windows only uses 37 gigs afterwards and linux the rest.... before you actually do that, make sure you have backups and defrag your windows drive 2-3 times

---

### Post by tmcdlive on 2007-12-22
> **hyper_ch said:**
> no, currently the whole 70 gigs are used by windows... and you resize it so that windows only uses 37 gigs afterwards and linux the rest.... before you actually do that, make sure you have backups and defrag your windows drive 2-3 times

As a reminder ... this PC does not have Windows on it.  It is a brand-new Everex PC  that has gOS Linux and gOS is a disaster because I can not get it working.  Ubuntu is easy to work with.   I do not like gOS so I am adding Ubuntu because I like it better.  

     A)  There is no Windows Software on it at all ... It is totally devoted to Linux.
     B) It is also brand new and nothing is on the hard-drive except the gOS software.

I do remember seeing anything in gOS like a defrag program but will look again, though if I do find it I might not be able to get it to work. gOS is a pain.

I am hoping/assuming that when it boots up it will give me a choice so I can go into Ubuntu directly off the hard-drive.

---

### Post by tmcdlive on 2007-12-23
DID THE INSTALL  ...  Results are that the machine does NOT boot in to Ubuntu from hard-drive.

It does boot in Ubuntu via the Live-CD.

It does boot into the Original Operating system on this PC --  gOS Linux Distro -- remember this is a Linux machine (made by Everex) and does not have windows on it.  I am "replacing" the gOS on it.

Does not Boot into Ubuntu from the Hard Drive.

Install went smoothly and pretty quick  ..  the one quirk was that there was no ending message saying finished ... the sliding bar "installation" screen finished and cleared off the desktop ...  and we were back to the Live-CD system. 

I waited about 15 minutes and absolutely nothing was going on.  No activity on Hard-drive nor on the CD.  So using the instructions on the "Howtoforge" instruction page I booted it with the results mentioned above.

Question ... Any ideas on what to do?

Thanks much for any help.

---

