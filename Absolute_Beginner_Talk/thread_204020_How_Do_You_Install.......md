---
title: "How Do You Install......"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by Dragonclaws11 on 2006-06-26
If I wanted to Install a computer game that I got at a store, how would I do it?  I have Diablo II and I can't figure out how to install it.  HELP ](*,) :-# :-k :confused: :( 8-[ :-({|= :roll:

---

### Post by T700 on 2006-06-26
Does the box say it will run on Linux?  If not, you might try something like WINE that provides a way to run some/most Windows programs under Linux.

Paul

---

### Post by Dragonclaws11 on 2006-06-26
How do I install WINE?  I'm doing this as a summer school project and I have built my own computer.  We have ubuntu 5.10.

---

### Post by Brunellus on 2006-06-26
most "shrink wrapped" software you get at the store is for Windows.  It may (but usually won't) run on Linux.  

That said, it is may be possible to run Diablo II on Ubuntu via WINE:

[http://appdb.winehq.org/appview.php?versionId=49](http://appdb.winehq.org/appview.php?versionId=49)

What you would need to do is install and configure whe WINE emulator:

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Then, put the CD in the drive, navigate to it in Natilus, right click on the install program on the CD (usually called SETUP.EXE), and it should attempt to install.

---

### Post by Dragonclaws11 on 2006-06-27
I'm Still Confused
How do I do this?
Do I have to order a disk because I don't have time for that...

---

### Post by Brunellus on 2006-06-27
is the computer you're working with connected to the internet?

---

### Post by Dragonclaws11 on 2006-06-27
I am in a classroom to where I can hook it up.  I did but it wont let me on firefox...
:confused:

---

### Post by Brunellus on 2006-06-27
[QUOTE=Dragonclaws11]I am in a classroom to where I can hook it up.  I did but it wont let me on firefox...
:confused:[/QUOTE]
what error are you getting?

---

### Post by T700 on 2006-06-27
To save you time, here are the summary points.

1.  **Most computer games you purchase at the store will not run on Linux, as they are designed for Windows.**

2.  It is sometimes possible to use a program called WINE to "trick" them into running on Linux.

3.  You can install WINE via the internet by using apt-get or one of the graphical installers or even compiling it yourself.

Paul

---

### Post by Dragonclaws11 on 2006-06-27
When I go to [www.ubuntu.com](www.ubuntu.com) it says that it can't find it.  My teacher told me to download Mozilla to a CD then download it to my PC so I'm trying that now.

---

### Post by Brunellus on 2006-06-27
[QUOTE=Dragonclaws11]When I go to [www.ubuntu.com](www.ubuntu.com) it says that it can't find it.  My teacher told me to download Mozilla to a CD then download it to my PC so I'm trying that now.[/QUOTE]
your teacher is apparently not aware that you're running a non-Windows operating system, and his instructions are therefore unhelpful.

Your problem is that your computer is not finding the network.  How is it connected to the network, physically?

---

### Post by Dragonclaws11 on 2006-06-27
It didn't work

---

### Post by Brunellus on 2006-06-27
[QUOTE=Dragonclaws11]It didn't work[/QUOTE]
WHAT didn't work?

is the computer PHYSICALLY connected to a network? If so, is it through a modem or through an ethernet card?

You will need network access to download the WINE program that will make your Windows software work.

---

### Post by avtolle on 2006-06-27
I suspect that since he is at school, his access to the internet is probably blocked, or, at best, extremely limited. Thus, he won't be able to access the web unless his teacher permits it. I would suggest he talk with the teacher so the teacher knows he isn't going to the web to visit restricted sites, etc., and then, if the teacher grants access, he follow the assistance set forth in the preceding posts.

---

### Post by Brunellus on 2006-06-27
[QUOTE=avtolle]I suspect that since he is at school, his access to the internet is probably blocked, or, at best, extremely limited. Thus, he won't be able to access the web unless his teacher permits it. I would suggest he talk with the teacher so the teacher knows he isn't going to the web to visit restricted sites, etc., and then, if the teacher grants access, he follow the assistance set forth in the preceding posts.[/QUOTE]
it would appear that the teacher isn't even aware of any restriction....

---

### Post by Dragonclaws11 on 2006-06-27
[QUOTE=avtolle]I suspect that since he is at school, his access to the internet is probably blocked, or, at best, extremely limited. Thus, he won't be able to access the web unless his teacher permits it. I would suggest he talk with the teacher so the teacher knows he isn't going to the web to visit restricted sites, etc., and then, if the teacher grants access, he follow the assistance set forth in the preceding posts.[/QUOTE]


I'm a SHE...lol...and I'm logged in under my teacher so I'm not limited at all.

---

### Post by Brunellus on 2006-06-27
that's the key step.   how is internet access restricted?  your ubuntu box is obviously not logging into some sort of authentication system that the windows ones do.

---

### Post by Dragonclaws11 on 2006-06-27
the internet access isn't restricted because I'm under the teacher's name and it's summer school.

By the way, my names Candy

I'm hooked up on a modem card

---

### Post by Brunellus on 2006-06-27
[QUOTE=Dragonclaws11]the internet access isn't restricted because I'm under the teacher's name and it's summer school.

By the way, my names Candy

I'm hooked up on a modem card[/QUOTE]
it dials?

---

### Post by avtolle on 2006-06-27
Candy, sorry about that. :) Could the problem be that there is a general blocking program that your teacher cannot get past? (My wife works in a middle school, and she has issues with the firewall/blocks all the time, due to the way the web access and permissions are configured.) Seriously, is this broadband/dial up? It looks like people with more knowledge than I are helping, so I'll go away. Best of luck.

---

### Post by Brunellus on 2006-06-27
[QUOTE=avtolle]Candy, sorry about that. :)[/QUOTE]
honest error.  and in English, where the gender is in doubt, it is still grammatically proper to default to the masculine.

---

### Post by Dragonclaws11 on 2006-06-27
no...:confused:

---

### Post by Dragonclaws11 on 2006-06-27
[QUOTE=avtolle]Candy, sorry about that. :) Could the problem be that there is a general blocking program that your teacher cannot get past? (My wife works in a middle school, and she has issues with the firewall/blocks all the time, due to the way the web access and permissions are configured.) Seriously, is this broadband/dial up? It looks like people with more knowledge than I are helping, so I'll go away. Best of luck.[/QUOTE]

I think I'm computer illerterate...lol...oh, apology accepted.  But I don't think there are any firewall/blocks in the way.  My teacher is a computer whiz, just not with ubuntu products...

---

### Post by Dragonclaws11 on 2006-06-27
so...what would be the best way to get the internet working...it says the mozilla browser is not available...how do I get it w/o internet?
:mad:

---

### Post by sir_cheats_a_lot on 2006-06-27
What we need to know is:
  are you using a Ethernet card (NIC / LAN card as some call them) or a 56K modem?
chances are the school does have a firewall, and run through a proxy server.  i know mine does.  because it is a school it's safe to assume they have T1 or some other broadband.
if your school has a tech guy you'll need to get the proper settings from him or the Administrator of your computer lab, if you have one, if you don't have a tech.

   After you get those settings: write them down somewhere, because those settings will likely screw with you home ISP setting, so when you are home you'll probably have to remove those settings, and put them back in when ever you need to use it on the school network.
To get WINE just open Synaptic Package Manager. it's under System > Administraition.    you might have to add Multiverse- and Universe repositories.

hope that cleared some things up.

---

