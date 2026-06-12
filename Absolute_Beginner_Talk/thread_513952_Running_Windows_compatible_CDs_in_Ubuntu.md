---
title: "Running Windows compatible CDs in Ubuntu?"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by chatterjee on 2007-07-31
Some CDs are designed for Windows,and unfortunately the number is not pretty small.Isn't it possible to run Windows compatible CDs in Ubuntu through some emulators?If yes,it'll be very nice of you to tell me how it happens?

Thanks in advance!

---

### Post by razeshkale on 2007-07-31
Before you post any Thread ,please search through Forum
Anyway dont forget this NEXT time

For windows compatible programme you can RUN most of the programmes using WINE
but not all(remember this)

you can search with wine for ubuntu
Cheers

---

### Post by chatterjee on 2007-07-31
Thanks for your reply,razesh...

BTW,I searched the web before posting it but didn't find the whether I can run "windows compatible **[COLOR="Red"]'CDs'[/COLOR]**" on Ubuntu.That's the reason I've posted the thread....

---

### Post by anewguy on 2007-07-31
You can also go to a virtual machine and actually run Windows within Linux - thereby allowing you to run your "Windows CDs".  2 of the most popular are VirtualBox and VMWare.  I personally prefer VMWare-Server.  Both are free.  VMWare-Server requires a registration number but again the registration is free.  If you want to try either of these, you can either post back here, or try a search in this forum for "Windows virtual machine" and things like that.

Don't worry about the search you tried not helping you.  Some people get tired of what they consider the "same old questions" coming up on this forum, but the truth is that it can sometimes be hard to know what to search for to begin with.  If things are already covered somewhere else you will probably be given links to those posts.

Remember, it's an absolute beginner's forum, so don't be afraid to ask any questions you want to.  Everyone is here to help people completely new to Linux and Ubuntu as well as those with a little more exposure but still not "experts" by any means.  A lot of us have been learning, and as we do we try to help others who post a question like we had.:)

---

### Post by Outrunner on 2007-07-31
Can you be more specific about what you're trying to do? Are you trying to install something? If so, what? Can you not acces the CD?

---

### Post by chatterjee on 2007-07-31
Thank you for you replies buddies.

@anewguy...
  I don't want to keep Windows in my machine forever,when I've got a taste to Ubuntu Fiesty,such a mervellous piece of OS.And I think I need to keep windows to use VMware.I just want to play the CDs which are designed for Windows.
 
  And about asking questions,I believe one must do some 'home work' before posting.But one should ask one's teacher if he fails to solve the problem individually.:D It's really nice of you to talk with a beginner with such a kind voice...thanks...:)

@Outrunner..

   I'm not trying to install s/ws but I'm trying to run the CDs made for Windows.I could have ignored them but the number is large...almost every CD I come accross is built for Windows.

---

### Post by thefoolisme on 2007-07-31
"I'm not trying to install s/ws but I'm trying to run the CDs made for Windows.I could have ignored them but the number is large...almost every CD I come across is built for Windows."

OK, I'm confused.  You're not trying to install software.  What's on the CDs?  Are you talking about music CDs, or the extra stuff on music CDs, or what?  Maybe we're missing the point of your question.

---

### Post by chatterjee on 2007-07-31
May be confusing,but the thing is that some magazines provide CDs and DVDs which are 'designed' for windows even though they may contain Linux softwares.The problem is this... when I pop the CD/DVD in the drive it says :[COLOR="Red"]**_"Invalid mount option when attempting to mount volume:Chip july 07"_**[/COLOR].I can't even explore the CD for contents let go of installing softwares.

PS:I can use other CDs like audio CDs,othe data CDs etc.

---

### Post by chatterjee on 2007-08-01
Anybody else to help:(?

---

### Post by Benbow on 2007-08-01
"Before you post any Thread ,please search through Forum
Anyway dont forget this NEXT time"

It would be more pleasant for everyone if the few people who suffer from an apparent attitude problem would consider the effect that their reply has on other people. The forum already takes questioners into a search for possible answers, which is excellent, and after all, if you consider a question unnecessary just do not answer it - someone else will (fortunately).

It is a slight problem with cd/dvd's on windows based mags, it will be interesting if someone comes up with a solution. I suppose one answer would be to only buy linux magazines!!

---

### Post by ghanu on 2007-08-01
Hi,

 I have had no problems mounting the CD's of above mentiond mag. Try mounting the CD's using terminal. The error could be because it specifies a .exe to run on insertion ( as it is wid windows ) 

sudo mount -t iso9660 -o ro /dev/cdrom /mnt/

Hope this helps. Reply

---

### Post by chatterjee on 2007-08-01
No,it's not working gives an error:

> mount: special device /dev/dvdrom does not exist

---

### Post by chatterjee on 2007-08-01
Installed wine,but it is of no help regarding this issue.See the screenshot....

---

### Post by ghanu on 2007-08-01
U should have done this

sudo mount /dev/dvd /mnt/

---

### Post by chatterjee on 2007-08-01
> mount: wrong fs type, bad option, bad superblock on /dev/dvd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


What should I do?Anybody with help?:(

---

### Post by candtalan on 2007-08-01
Hi chatterjee
windows cds run in windows machines when you put them in because of two things I think - 
1) they are recognised and connected (mounted) automatically, and importantly, 
2) they also have a windows program such as autorun or similar, which is automatically started after the CD is connected (mounted).
The mounting can happen automatically in ubuntu in many circumstances, however, it is not very likely that you will get the autorun to work easily or at all in linux (ubuntu).

If you arrange that your machine simulates a  complete window machine (sort of what vmware does) (vm is virtual machine) then the vm will respond as a windows machine will do (but slower).

Wine is a program which uses some special directories to pretend they are windows directories, and some windows programs, often rather simple structured programs (in their programming) can be made to run in linux (ubuntu). Sometimes this is not possible.

The attractive nature of windows CDs is part of the well marketed lock in of windows ecosystem. So unfortunately I suggest that some thingswill simply not work.
As people move from windows to ubuntu then things will change perhaps.

---

### Post by e_james on 2007-08-02
???? Most of the time I am running Windows but I rebooted into ubuntu 7.04 and grabbed 1 CD and 2 DVDs from magazines to hand and they all did exactly what I thought they would do -- automount,  browse folders and access linux compatible files (.txt, .bmp etc.). I could even read the contents of a .iso file. Is there some sort of hardware / driver compatibility issue here?

---

### Post by Frak on 2007-08-02
Either via Windows Emulation in VMware or Virtualbox, or your can try WINE, and take a look at [this guide]("http://ubuntuforums.org/showthread.php?t=497332"). It may seem a little confusing at first, but thats the sacrafice to make Windows stuff work in Linux.
Though, we are here to help if you need it.

---

### Post by Frak on 2007-08-02
> **e_james said:**
> ???? Most of the time I am running Windows but I rebooted into ubuntu 7.04 and grabbed 1 CD and 2 DVDs from magazines to hand and they all did exactly what I thought they would do -- automount,  browse folders and access linux compatible files (.txt, .bmp etc.). I could even read the contents of a .iso file. Is there some sort of hardware / driver compatibility issue here?
One, I want to make it clear, Linux drivers and Windows drivers are two **very** different things.
Windows drivers are .inf files that are pretty easy to install, yet...
Linux drivers usually follow the pattern of
```
./configure
make
make install
```
Two, no this isn't a hardware/driver issue. Windows CD/DVD's run on Windows, Linux via compatability.
Linux CD/DVD's were made with Linux in mind, and should run perfectly with open formats.
If you mean running DVD movies, you have a libdvdcss problem, i.e. its not installed.
Ask if you need help with this.

---

### Post by chatterjee on 2007-08-03
Thank you all for your replies pals.
The thing is that other can run the CD/DVD in their Linux machine without problem.So it is not that it can't be run in Ubuntu coz a SuSe machine has run it on my brother's office(don't know what configuration of hardware they use).I can't also run the flash based CDs.They give the same error.The problem *may" be due to that(pls don't be biased friends for this ignorant fellow).Pls ask any information that you need.

@Frak,I think VMware needs a Windows disk of course,but I don't want to back to Windows again:D.Please don't mind...please...I couldn't find time to go through the Wine tutorial,due to extreme pressure of my studies:(.

Awaiting replies...

---

### Post by e_james on 2007-08-03
If I may suggest it. Could we take one step at a time. If I understand the situation correctly from post #8, some CDs/DVDs can't be mounted. You get an error message. Can you give a couple of examples of ones that don't work and ones that do (i.e. name the magazine)? Do the same discs work in Windows and fail in Ubuntu on the same PC in the same drive? Maybe you can't do that test.

---

### Post by chatterjee on 2007-08-03
I've deleted the XP partition and now I'm completely on Ubuntu.But CDs ran on XP,when I had it.

---

### Post by sandeep108 on 2007-08-03
I think it may mostly be a flash problem since most Chip mag CDs are based on flash. Do you have flash working on Ubuntu?

---

### Post by chatterjee on 2007-08-03
Can you please check out this link:
[http://www.thinkdigit.com/forum/showthread.php?t=64510](http://www.thinkdigit.com/forum/showthread.php?t=64510)

---

