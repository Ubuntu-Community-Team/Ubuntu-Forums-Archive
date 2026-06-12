---
title: "[SOLVED] Problem installing Ubuntu and Xubuntu (not a live cd problem)"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2007-08-02
Im having serious problems with installing Ubuntu & Xubuntu.

**_"When i try to use Ubuntu when i use the graphics version,after it has loaded the brown screen and i few minutes have passed and the sound plays it says in an alert window: _**

"There was an errpr starting GNOME Settings Daemo.

Some things, such as themes, sounds, or background settings ay not work correctly.

The last error message was:

Did not receive a reply> Possible causess include: the remote applicaion did not send a reply, the message bus security policy blocked the reply, the replytimeout expired, or the network connection was borken

GNOME will still try to restart the Settings Daemon next time you log in." At this point the computer freezes for a minimum of an hour (longest i waited)


**_When i select start ubunut in safe graphics mode i gt the error:_**"Failed to start the X server (your graphical interface). It is likely that is not set up correctly. Would You like to view the server output to diagnose the problem?"

Click yes gives me:
"x Window System Version 7.2.0
Release Date:22 January 2007
XProtocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Currrent Operating System:Linux ubuntu 2/6/20-15-generic #2 SMP Sun apr 15 07:35:31 UTC 2007 i686
Build Date: 04 April 2007
        Before reprting problems,check [http://wiki.x.org](http://wiki.x.org) to make sure that   you have the latest version.
Modu Loader Present:
.................

Fatal server error:
Caught Signal 11. Server aborting


**_When i use the alternative disc after i select install using text based installer(top option) i get the error:_**
"[	31.020320] crc error
[	31.032738] Kernel panic - not synicing: VFS: Unable to mount root fs on unknown-block(10,1)
[	31.032794]"

_**When installing Xubuntu in the live cd i get the error of:**_

I can do the whole install proccedure but when i click start it stops on 15% checking file structure and stays their (i have left it for over an hour on 2 occasions)

The problem is not with the cds as they work in another computer i have fine and install without any problems.

_**The laptop i am using has:**_
256 mb of RAM
1.5Mhz Proccessor speed
need anything else let me know
I currently have NO OS on the machine

I dont want to burn a Xubuntu alternative cd unless someone is quite sure (not just suggesting as a quick answer) that the alternative Xubuntu will work as the Ubuntu alteranative did not work, As im gonig throught disc real fast.

I will be checking this forum regulary and i can also use msn if anyone is willing to help me reslove this problem step by step.

Need any more information just ask and i will to by best to give you answers. I apologise for any slight typing errors.

Thanks in advance 
Saj

---

### Post by ugm6hr on 2007-08-02
I'm no expert - but things running through my mind...

Are you sure the hard drive is OK?  If you know the manufcaturer - you should be able to get a diagnostic CD from their website (I know Hitachi have a good one).  Otherwise this is supposed to be good: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Possibly an issue with your Graphics card - what type is it?

Did you try Xubuntu LiveCD in Safe Graphics mode?

---

### Post by ev5unleash1 on 2007-08-02
You may want to try diffrent CDs. You could check to make sure this type of system is supported.

Like
Intel based 32-Bit
64-Bit
Sun

Ubuntu DOES NOT SUPPORT POWER PCs on Macs

Try some other types of CDs for each type of PC.

---

### Post by saj0577 on 2007-08-02
> **ugm6hr said:**
> I'm no expert - but things running through my mind...

Are you sure the hard drive is OK?  If you know the manufcaturer - you should be able to get a diagnostic CD from their website (I know Hitachi have a good one).  Otherwise this is supposed to be good: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Possibly an issue with your Graphics card - what type is it?

Did you try Xubuntu LiveCD in Safe Graphics mode?

yeha i did try with safe graphics modei have spent the last 7 hours diagnosing it and it is my hardware without a doubt i am going to try fedora and if it works and i will investigate why Ubuntu and Xubuntu and so on do not work i shall share it with the development team.:)

Saj

---

### Post by Paul133 on 2007-08-02
Sorry to hear about all those problems. Good luck finding a Linux distro that works!

---

### Post by saj0577 on 2007-08-03
> **Paul133 said:**
> Sorry to hear about all those problems. Good luck finding a Linux distro that works!

Thanks
saj

---

### Post by saj0577 on 2007-08-03
Hiya,

Even bigger problem now i got half way thru installing Fedor and it crashed and now when it boots up any disc that is not a linux distro will not start the boot disk (xp not work) and it frezzes i cant boot the linux because my HDD will not work with linux (after alot of analysis). Has anyone had this problem before where they cant reinstall XP after trying to install linux distros id so please help me. The computer is unusable, and i need it.

Saj

---

### Post by ugm6hr on 2007-08-03
Did you try a diagnostic on the HD?  I suspect that the problem has nothing to do with linux, and your HD is just starting to fail.

I would suggest that you boot a linux live CD that works, and try to backup everything on the HD that it will allow you to (to an external storage device e.g. USB disk etc).

Then run a diagnostic utility (as recommended previously) on the HD.  That will confirm (or refute) the problem.

---

### Post by saj0577 on 2007-08-03
> **ugm6hr said:**
> Did you try a diagnostic on the HD?  I suspect that the problem has nothing to do with linux, and your HD is just starting to fail.

I would suggest that you boot a linux live CD that works, and try to backup everything on the HD that it will allow you to (to an external storage device e.g. USB disk etc).

Then run a diagnostic utility (as recommended previously) on the HD.  That will confirm (or refute) the problem.

Yeah trying trun a disc but now with Linux distro discs it crashes after loading the kernel. and xp discs it does nothing. I think the HDD is unusable forever just hoping for some hope somewhere as i cant just go to the shop and buy a new laptop.

Saj

---

### Post by saj0577 on 2007-08-03
Anyway to delete all HDD partions without booting up anything?

Saj

---

### Post by ugm6hr on 2007-08-03
> **saj0577 said:**
> Anyway to delete all HDD partions without booting up anything?


Don't think so.  It does sound like your HD has died.  What is unusual is that you can't boot from a CD...

Maybe try removing the HD from the laptop, and then try booting from a LiveCD, just to check that the HD isn't interfering somehow.  If that works - then at least you just need a new HD.

---

### Post by saj0577 on 2007-08-03
Hiya fixed my own problem so for future reference. Im not sure fi their is somewhere that a mod can put this.

If you cant run any boot discs apart from Linux boot disk. Install Ubuntu 6.06 Server on your computer. Then once it is installed restart and put the XP boot disc in and it will work.

Simple but works if anyone needs any help just PM me and il do my best to help.

Saj Here to help

*Could a mod please close this thread thanks*

---

