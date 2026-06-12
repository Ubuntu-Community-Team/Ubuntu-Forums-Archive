---
title: "iSight, Kopete, and 7.10"
date: 2007-11-22
forum: Apple Intel Users
---

### Post by trevelyn on 2007-11-22
I can see myself in the camera in Kopete, but none of my friends can send me a video conference invite, and theres no option in Kopete at all for one from my side.  Do i have to Open certain ports in my router for this to even be an option?  I have Kopete, iSight, and 7.10 Gutsy.  Also, I am using Kopete (which seems to be a KDE thang) in Gnome.  Is there another alternative that would emulate iChat maybe for Gnome?  Thanks! Everything else is running perfectly! xD 7.10 r0x!

---

### Post by Grey Box on 2007-11-22
Kopete is the only option you have at the moment for AIM. It is not NAT friendly and it is said you have to forward ports (I found some info [- here -]("http://wiki.kde.org/tiki-index.php?page=Kopete%20Webcam%20Support")), specifically:

> Detailed listing of ports to forward for MSN
Microsoft provides this info in the following link: [http://support.microsoft.com/kb/324214/en-us](http://support.microsoft.com/kb/324214/en-us)
Service TCP ports UDP ports

[LIST]
[*]Incoming voice (computer to computer) 6901 6901
[*]Voice (computer to phone) 6801, 6901, 2001-2120
[*]File transfer (receiving a file) 6891-6900
[*]Note In the "File transfer" cell, 10 ports are opened (ports 6891 through 6900 inclusive) so that you can perform 10 file transfer operations at a time. If you open only one of these ports, you can only transfer one file at a time.
[/LIST]


Having said that, it's rather fiddly and I have to say I'm a bit disappointed with video chat in Linux so far. I tend to log out and go into OS X and use iChat still, despite how much OS X is starting to irritate me.

---

### Post by Levo75 on 2007-11-22
It all works for me in aMSN.

---

### Post by trevelyn on 2007-11-23
yeah, youre right i got the video working okay, but i am going back to leopard thanks anyways.  The reason why its either "one or the other" is becuase my HDD is extremely small (60GB) and i was constanly erasing stuff.  Now each time i log into Gnome i have set the check the "enable mouse keys" under keyboard accesability for the right click, and i installed my second wifi card and the first one disappeared and the suspend only wakes up %70 of the time.  too risky, i gave it a few days and worked hard on it.  thanks for your help!

---

### Post by Grey Box on 2007-11-23
As they say, Mac hardware is not the ideal for a Linux system at this stage. I was given my macbook as a gift (otherwise I'd never have bought one!) and I gave OS X a good try, but trying to do serious work on it has proven to be quite a drag. It feels slower and I found some things are definitely less efficient, like website development. My wife's old Dell notebook outperforms it anyway.

But for social interaction and basic at-home stuff like loading photos off the camera and chatting to family (and going mobile, where battery life is important), I am keeping my OS X partition alive - nothing beats iChat at the moment.

---

### Post by trevelyn on 2007-11-23
> **Grey Box said:**
> As they say, Mac hardware is not the ideal for a Linux system at this stage. I was given my macbook as a gift (otherwise I'd never have bought one!) and I gave OS X a good try, but trying to do serious work on it has proven to be quite a drag. It feels slower and I found some things are definitely less efficient, like website development. My wife's old Dell notebook outperforms it anyway.

But for social interaction and basic at-home stuff like loading photos off the camera and chatting to family (and going mobile, where battery life is important), I am keeping my OS X partition alive - nothing beats iChat at the moment.


YES you are exactly right, and my dear friend Denielle talked me out of going back to OS X.  And i cleared a bunch of things up already!  can someone PLEASE in the 7.10 Gutsy install note that YOU CANNOT use the same AppleVideoUSB folder twice! It simply does NOT work.  I had to go with a full install on the drive since the drive is so small!  So I had to reinstall OSX and then REPLACE the Driver on my external drive!! Yeah, THAT solved the problem, and actually, i had to test it and did this TWICE! IT IS DEFINITE that you cannot use the same AppleVideoUSB driver 2 times or more!  I will repost it in the iSight thread, I think that would solve a bunch of errors that i see people posting that i witnessed myself during the 5+ installs. - trev

---

