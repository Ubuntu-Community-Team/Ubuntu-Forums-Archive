---
title: "Ubuntu freezes"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by Lone_f on 2006-04-16
Hi.
It's the first time I've tried Ubuntu and I have a problem. It freezes (I still can move the mouse cursor though).
At first I thought I'd try the Live CD (from ShipIt) and everything went smooth until the graphical interface starts loading (Nautilus, Update Notifier, etc). The system freezes at one of these steps: 1) loading Nautilus; 2) loading Update Notifier; 3) loading the bars at the top and bottom of the screen (sometimes an icon or several load before the freeze); 4) I click; 5) I double- or right-click on something; 6) I click on a menu item.
I lost patience to try more and I installed Ubuntu on my PC. The problem persisted. Furthermore Ubuntu didn't even go past 3) :(
Any suggestions what I should do to get at least to TRY the OS?

My PC is quite old, BTW (P3 866MHz, GeForce2 MX 400, 384MB RAM)

---

### Post by bscbrit on 2006-04-16
Can you start it in recovery mode?  When the initial menu comes up you should be able to choose the normal start or recovery start.  If recovery works (and it will leave you at a command line - no graphics - simply type 'reboot'.  If it now doesn't start again I would suggest that there is something in your hardware that ubuntu doesn't like.  However, once we know this we can start to look for what it is :D

---

### Post by Lone_f on 2006-04-16
I guess that really is the problem. Now I don't even get to login, the system leaves me with a black box in a white background. :(

---

### Post by bscbrit on 2006-04-16
I don't suppose it is a dual-boot machine and you could confirm the hardware is fully serviceable, could you?

---

### Post by Lone_f on 2006-04-16
In fact it IS a dual-boot machine and everything works fine with Windows XP.

---

### Post by bscbrit on 2006-04-16
Well, if you cannot  log in, even in recovery mode, then the only options are to try to use a live disk to carry out the repair, or to re-install.  But the live disk that you have also exhibits the same problems - which I suppose should have given you a clue before you installed it, but I would also have gone ahead despite that - so there is not much point in trying that.  It would appear that your hardware is simply incompatible with Ubuntu.

What else can you try?  Well there are lots of linux distros and they all behave differently.  I had to put quite a bit of effort into setting up my wireless network using ubuntu, but under Mepis it just loaded and worked from the box.  Each distro has its strengths and weaknesses.  All I can suggest is that you try another distro until you find one that you can live with.

Sorry that, on this occasion, I couldn't help get you to a working solution.  Good Luck.

---

### Post by bscbrit on 2006-04-16
You could always keep your fingers crossed and try a new install of Ubuntu.  Accept defaults wherever offered.  But I wouldn't hold out too much hope that it will work.

---

### Post by Bloch on 2006-04-16
Lone_f said:  My PC is quite old, BTW (P3 866MHz, GeForce2 MX 400, 384MB RAM)

That's not old. A lot of people on these forums are big into computers and tell you about their 3.8GHz pentiums. I was kind of scared to install ubuntu on my system, because everyone seemed to have better hardware and talk about a 1.5GHz as being low-level, but I have

P3 800MHz, built-in graphics, 256 RAM

and it works fine, 15-20 second to start OpenOffice, but it works great once it's started, and everything else is fine.

---

### Post by bscbrit on 2006-04-16
Bloch - yes, I agree, but it would seem that some part of his hardware does not like Ubuntu.  I'm not blaming the age of his computer rather than an unidentified item that will not let him get booted enough to try to sort the problem out.

I've given my contribution.  The live disk exhibits the same problem so is unusable.  Another distro might work.  But there is little to be lost (other than time) from trying another install.

I've also got a 200MHz PII running ubuntu server - age is certainly not a problem for the software!

---

### Post by Mustard on 2006-04-16
If the system could get to a command line somewhere rather than freezing then it might be possible to get it running.  When I first read this thread I was wondering whether using XFCE might be a good idea.  He/she could do a server install and try installing xubuntu-desktop from the command line after the server install.  The lockup seems to occur when the graphical portion of the startup occurs, so I would suspect it could be fixed through some editing of the xorg.conf too.  Mind you, I would probably bang my head against the wall for three or four days trying to get it to run, but others might not necessarily have the time or inclination to do the same. :)

---

### Post by bscbrit on 2006-04-17
Mustard - Yes, and that was my first plan.  But when the system failed to boot into recovery mode, and the only live disk exhibited the same problem, then I decided that perhaps Lone_f wanted a working computer more than I needed to try to solve the problem.  I suspect that we would both enjoy trying to fix it, if only for the challenge, but I cannot really expect Lone_f to support my (unusual) desires :-D ](*,)

---

### Post by Lone_f on 2006-04-17
I *would* like to take up this challenge and make Ubuntu work :)
It'd be interesting to have some experience in Linux. And I have some spare time, too :D

---

### Post by bscbrit on 2006-04-17
I have a few evenings spare this week before I must go travelling and I will be offline for about 7 weeks.

A few questions.  Do you have broadband? (It might be useful to download another distro live disk if you do not already have one).

Do you have any other live disks?

Do you have any valuable data on the disk that we are going to try to get Ubuntu working? (If yes - BACK IT UP!).

Have you got a sense of humour?  (This is absolutely vital - no-one should struggle with distro installations unless they have a sense of humour)

Are you prepared to accept the lessons learned even if we do not eventually succeed?  (I'm not trying to sound negative but every experience teaches me something - even those that I don't want to go through again....! )

---

### Post by Lone_f on 2006-04-17
I have a 256kbps broadband, so I guess I could download some distros, but I need some advice which ones I should try out.

I have another HDD but it's pretty much filled up (less than 2GB not contiguous free space). And even less if i back up some things. Or I just might burn them on CDs.

Sense of humour - present ;)

And yeah, I won't get mad and won't bang my head against the wall. Partially because failure ain't The End and partially because heads bleed, and walls don't :D

---

### Post by bscbrit on 2006-04-17
Before we do a complete re-install, I would like you to try once again to get into recovery mode.  So as the initial menu shows on the screen - not the graphical menu - you should be able to select your current kernel and current kernel+recovery mode.  It's the latter that we need.  If there is a menu display immediately the computer restarts you might have to press esc a few times to get to it.  As this will eventually lead you to a dumb commandline as root there is no graphical display to start and hopefully we will skip the hardware problem for the time being.  Let me know how you get on.  If there is anything that you are unsure of, please ask.

---

### Post by Lone_f on 2006-04-17
OK, that works. What now?

---

### Post by bscbrit on 2006-04-17
OK. The problem might have been fixed by a more recent update and, rather than spend a long time trying to fix a bug, we might find that everything is now working with the latest version.  So, do you have a broadband connection on your Ubuntu computer.  One way of finding out is simply to try 

ping -c 5 [www.ubuntuforums.org](www.ubuntuforums.org)

and see if you get a connection.  If you don't then we can either try and configure one, or we can simply move ahead and try to solve the problem.

---

### Post by Lone_f on 2006-04-17
Well, it doesn't work. I think that's because I've got an PPPoE connection and I've got to use a user name and a password.
I use a modem to connect and it is plugged into an USB port.

---

### Post by bscbrit on 2006-04-17
Now that is a pity.  

First decision - do you want to try to get the modem working with your ubuntu computer, or would you rather get it to boot first?

---

### Post by Lone_f on 2006-04-17
Maybe we should try to set up the connection to see if there's an update that could fix my problem.

---

### Post by bscbrit on 2006-04-17
Having asked the question - I immediately regretted asking it.  Although the modem can be configured from the commandline (in fact just about everything can!) I haven't configured PPPoE before and it would be a case of the blind leading the blind, so to speak.  And it will be considerably easier to achieve with at least some graphical tools to assist us.  First lesson learned - bscbrit sometimes talks rubbish!

  So, unless you are determined to continue, what I would suggest is we do a complete minimal re-install (as suggested by Mustard a few posts back).  If you agree, then reboot the computer with the CD or DVD in place.  When you get to the initial installation screen (where the first time you simply pressed the enter key) then on this occasion type

server

followed by the enter key.

This will install essential software but absolutely no graphical interface.  It doesn't take too long because it also installs only a minimum subset of applications.  Effectively, it will get you back to where you are now but without the burden of all of the other software.

When you have got to that stage, you will need to install a minimal graphical interface called XFCE, which is known on your installation disk as xfce4.  To do this you enter the following command (having logged onto your computer as a simple user):

sudo apt-get install xfce4

Let me know how you get on - or even if you agree with this course of action!

---

### Post by Lone_f on 2006-04-17
> First lesson learned - bscbrit sometimes talks rubbish!
I'd like to have this kind of self-criticism ;)

Of course I agree, I'm into "adventures" like these :)

---

### Post by Lone_f on 2006-04-17
Well, I installed the minimalistic Ubuntu, I typed in the command, the system asked me to type my password and
```
E: Couldn't find package xfce4
```
was what I got.

---

### Post by bscbrit on 2006-04-17
Ok install 'xubuntu' - which does the same thing.

---

### Post by Lone_f on 2006-04-17
Same thing :/

---

### Post by bscbrit on 2006-04-17
I've just looked back at Mustard's post - he suggests xubuntu-desktop,  I've checked again, and it exists in my repos.

---

### Post by Lone_f on 2006-04-17
The system doesn't find that, either. I'm really confused right now.

---

### Post by bscbrit on 2006-04-17
Well it seems that xubuntu is not on your CD.  We have several options (and confusion is not really one of them, so don't bother about it...)

1.  Try to install Gnome again and find out what is causing the graphics problem (and hopefully fix it).

2.  Download a full xubuntu CD and do an install from that.

3.  We go back to trying to get the modem working so you can download the files needed for xubuntu.

If you have a strong preference (or a 3-sided coin that you can toss) let me know which way to go please.


(Going offline for a while for a meal.)

---

### Post by Lone_f on 2006-04-17
I think that fixing GNOME would be the best choice right now, because I would download the CD no less than 6 hours and not able to do anything about it at that time. And I feel that setting up a PPPoE connection can be a pain, and it wouldn't guarantee a solution.

---

### Post by bscbrit on 2006-04-17
Right then - off we go.

sudo apt-get install ubuntu-desktop

Let me know what happens.  If you find that you cannot start the GUI, reboot into recovery mode and take a copy of /etc/X11/xorg.conf.  We will need to refer to that and it is probably easier if you have it in front of you when you are on the Windows machine. (I am assuming that you can transfer files between Ubuntu and the Windows partitions on your computer even if it involves using a floppy or usb memory drive.)

We will also be looking at the /var/log directory to see if we can see what is causing the problem.

---

### Post by Lone_f on 2006-04-17
Well, after the Ubuntu desktop install, I couldn't figure out how to copy files, so I decided to "startx". It left me with a weird-grey screen and an "X" for the cursor. I restarted my PC and voila - GNOME is perfectly running. I noticed that it is in lower resolution than it tried to launch after a default install, so I guess that my graphic card couldn't handle the default high one.
Thank you for your help and patience, bscbrit :)
I swear, I'd kiss you if you were a girl ;)

---

### Post by bscbrit on 2006-04-17
First - great news.

What screen resolution have you got, and what do you think you should be able to get?

Your thanks are more than enough - save the kisses for someone else!

EDIT:  I kept checking the page waiting for your response before I realised that, now that you have a working ubuntu you will not be looking at the web page on your windows machine.  You're quite right - enjoy ubuntu!  I'll check back tomorrow and we can try to improve the screen resolution and then get you online.  Cheers!

An easy way to get a copy of your xorg.conf:

cat /etc/X11/xorg.conf > ~/xorg.conf.txt

This will put a copy of the xorg.conf into a text file (xorg.conf.txt) in your home directory (~ is a shortcut for /home/[username] and it works quite literally, just type the ~ character).  Simply clicking on the text file in your home directory will open it in your default editor - usually gedit).  You can then print it, or save it (Save As) somewhere else e.g. on a mounted floppy or whatever.  If this still sounds like gibberish, I will explain tomorrow.

---

### Post by Lone_f on 2006-04-17
Now I've got 1024x768 and I think I don't need more - my Windows resolution is the same for almost 5 years and I'm fully satisfied.
But now I have a problem of setting up my modem - as I've already mentioned, it's a PPPoE connection and the modem is plugged into an USB port. Let's hope I'll find something useful in this wonderful (:)) forum.

---

### Post by bscbrit on 2006-04-17
If you are still online (our responses seemed to get out of sync...) goto System -> Administration -> Networking and see if your modem is recognised.  It might just be waiting for you to activate it.  If it doesn't work, we can look at this tomorrow evening.

Goodnight.

---

### Post by Lone_f on 2006-04-17
It's not recognised. Oh well, I'll do some searching and hopefully I'll find a solution.

---

### Post by bscbrit on 2006-04-17
[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

might start you in the right direction.

---

