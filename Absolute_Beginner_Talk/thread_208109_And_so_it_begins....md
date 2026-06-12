---
title: "And so it begins..."
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by Satine03 on 2006-07-03
I am trying to learn to use Ubuntu as it will be more helpful for me as a furture engineer but, I have only managed to get it installed on my computer. I am running but Ubuntu and XP on my computer at this time. I am haveing a problem with Ubuntu, I am unable to get a GUI interface to come up on Ubuntu. I can switch between ALT F1-F6 with no problem but cannot get any GUI part to  come up. I have tried to find something online to help me but I think I have just got too much new info running around and need some help gettin it all straight. I read something about ALT F7 but that did not work for me. Any advice would be appreciated. Thanks in advance.

---

### Post by Apple 101 on 2006-07-03
Did you perform a server installation, a desktop installation, or an alternate installation?

---

### Post by Buffalo Soldier on 2006-07-03
Hi Satine, 

Welcome to Ubuntu and GNU/Linux. First of all, do you mind sharing some info on your computer specs? That could help a lot in troubleshooting any problems.

Secondly, which ISO did you choose? Is it the *ubuntu-6.06-alternate-i386.iso*? or the *ubuntu-6.06-server-i386.iso*?

The *server* installation methods does not install any GUI. But all is no lost, you can still install a GUI, assuming you can cannot the the net. If you are connected to the net, just perfom this two commands:[list]
[*] sudo apt-get update
[*] sudo apt-get install ubuntu-desktop
[/list]

---

### Post by nanotube on 2006-07-03
check out the third link in my sig (the faq), you will find your problem of "i just see the black screen and no desktop" described and addressed there.

---

### Post by az on 2006-07-03
[QUOTE=Satine03], I am unable to get a GUI interface to come up on Ubuntu. [/QUOTE]
What happens when you log in and run

sudo apt-get install ubuntu-desktop
?

---

### Post by Satine03 on 2006-07-03
First I want to thank everyone for the, more than expediant, help. I did in fact install the server version on accident. Now I have a new problem. I ran the two lines you said to first I did:

      sudo apt-get update

I got prompted for my password, as expected, then I got a bunch of changes scrolling across my screen. Then I did:

      sudo apt-get install ubuntu-desktop

Again I got prompted for my password, as expected, and a bunch more scrolling with a few yes or no questions. Then it began to do what looked like it was loading stuff from a site and after a few seconds asked me for a disk. This is exactly what it said:

      Media change: please insert the disk labled
      'Ubuntu - Server 6.06 _Dapper Drake_ - Release i386 (20060531)'
      in the drive '/cdrom/' and press enter

I figured out that it wants a disc, a CD to be exact, from this message. The problem is I don't have a CD with that lable. The CD I loaded Ubuntu from was one that I downloaded the image of from [http://www.ubuntu.com/download](http://www.ubuntu.com/download) and named "Ubuntu Linux." I am assuming this is the disk the program wants but every time I insert it I get the same msg:

      Media change: please insert the disk labled
      'Ubuntu - Server 6.06 _Dapper Drake_ - Release i386 (20060531)'
      in the drive '/cdrom/' and press enter

I finally got the program to load all the information from the "sudo apt-get install ubuntu-desktop" cmd and now all I get is:

      Media change: please insert the disk labled
      'Ubuntu - Server 6.06 _Dapper Drake_ - Release i386 (20060531)'
      in the drive '/cdrom/' and press enter

and then after I put the disk in I see:

      79% [Working]

then that goes away and it is back to:

      Media change: please insert the disk labled
      'Ubuntu - Server 6.06 _Dapper Drake_ - Release i386 (20060531)'
      in the drive '/cdrom/' and press enter

To answer the question about computer set up the computer I am trying this on is an older one and I don't remember all the specs but here is what I know.

Processor is a Pentium around 2.2 ish
1G ram
80G HD (Partitioned into 30g for windows and 50 for Ubuntu)
1 CD R/W drive and 1 DVD drive
    - Which I should note I can only seem to find my CD drive when I am in Ubuntu. IThe CD drive is set as my primary boot drive and I don't know if that is why it is the only one it sees or not. I was going to try to get Ubuntu to read the disk from my DVD drive, becuase like I said this computer is old and I wanted to verify it was not the CD drive itself that has the problem, but could not seem to make that work.

Thanks again for your help.

---

### Post by givré on 2006-07-03
I think you should do your installation only from the ubuntu mirrors.
To do that, comment the line about your cdrom in /etc/apt/source.list:
```
sudo nano /etc/apt/source.list
```
on top, you should see some reference about your CD .Comment it (or them) with # at the beginning of the line, close nano with ctrl-X and type yes.
then update the source and install ubuntu-desktop
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by Satine03 on 2006-07-03
When I open /ect/apt/source.list to comment out the CD part of that file it opens as a new file. I forgot to put I tried that last night when I was messing around with the CD and DVD drive.

---

### Post by givré on 2006-07-03
[QUOTE=Satine03]When I open /ect/apt/source.list to comment out the CD part of that file it opens as a new file. I forgot to put I tried that last night when I was messing around with the CD and DVD drive.[/QUOTE]
sorry guy 8) i made a mistake, it's ```
sudo nano /etc/apt/sources.list
```

---

