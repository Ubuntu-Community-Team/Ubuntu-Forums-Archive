---
title: "Installation Basics"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by sergean2 on 2006-11-28
Being new to Ubuntu (about a week) I am having a problem installing a package.  Without the gory details I have narrowed it down to this.  I am trying to install libartsc0 and when I do I get the error message, "Error: Dependancy is not satisfiable:lib6".  I assume this message means that the installer is looking for the lib6 which is installed.  What am I missing?](*,) 

Please bear in mind that I am not connected to the internet (bad experience with viruses, worms and all the creepy crawlies on the internet) so I don't have that automatic download feature but have downloaded the files from work (I let them deal with the creepy crawlies)and taken them home on the flash drive.

Any suggestions to help out would be greatly appreciated.
Mike

---

### Post by turbojugend_gr on 2006-11-28
Linux is free f viruses (extremely rare to see an infected Linux system), and mlware and stuf stimply can't harm Linux. So you can use your internet connection if there's one.

If not, your message means that synaptic can't install lib6, which is a dependency for the package you are trying to install. You need to download that package and transfer it to your computer too.

---

### Post by wpshooter on 2006-11-28
Get that computer hooked to preferably your high-speed DSL or cable modem provider.  You will work yourself to death trying to keep your Ubuntu system up-to-date by shuttling updates from work.  You have extremely little to worry about with this system becoming corrupted.

---

### Post by sergean2 on 2006-11-28
> **wpshooter said:**
> Get that computer hooked to preferably your high-speed DSL or cable modem provider.  You will work yourself to death trying to keep your Ubuntu system up-to-date by shuttling updates from work.  You have extremely little to worry about with this system becoming corrupted.

As far as the library is concerned I have lib6 installed already that is the perplexing thing about this.


I appreciate what you are saying and that Linux is a more stable system but on top of the virus problem, I simply do not think that having the convience of the internet in my home is something I want.  I am deeply disturbed that there are many software packages, including Ubuntu, that can go into my system see what I have installed and make changes to my system.  I simply do not want anything/anybody, whether well intentioned or not, to have that capability.  This is my choice and if I have to do a little extra work then so be it.

---

### Post by lamego on 2006-11-28
That problem means you are installing the wrong library version.
The library you have tried to installs depends on a libc6 version different from the one you have installed.

---

### Post by wpshooter on 2006-11-28
I think you are being overly concerned.

Indeed, you are going to find that Ubuntu/Linux is SO SECURE, that even you as the user are going to have difficulties getting into certain things in the system and getting certain tasks accomplished might less someone from the outside world that does not have your user ID and password to be able to get into them.

I believe that you need to do some more reading about the security that is built into Linux and particularily Ubuntu.  This is NOT Microsoft or Internet Explorer.

---

### Post by sergean2 on 2006-11-29
I realize that this is not Microsoft which is why I am trying to get this to work for me.  Most of my computer work is done developing Access databases and I want to be able to run it in Ubuntu.  The program I am trying to install is WINE and am having some problems.  Quite frankly I would just as soon never use another Microsoft product again.  Having been involved with computers since 1980 I am acutely aware of the contribtuions the Microsoft Mafia has made to the computing world but they are now too big and too powerful for me and instead of giving me what I want in a product, I am forced to use what they say is good for me.

As far as the internet is concerned, I can really give you all the superfical reasons for not having it or recite the reasons to have it, but the bottom line is this.  In my humble opinion, and it is just my opinion only, what I get from the internet does not justify having:

1) the cost of an ISP
2) the headache of another program (Internet Explorer or Firefox) to deal with 
3)the threat, however minimal, of invasion of my home computer and the cost to minimize this threat.

I will point out here that a product is only useful if it improves the prodctivity of the user of that product and up to this point in time I am unable to do what I need to do with Linux so all the safety and security of which you talk about is moot point, I am still forced to use Windows.

---

### Post by Sef on 2006-11-29
> I will point out here that a product is only useful if it improves the prodctivity of the user of that product and up to this point in time I am unable to do what I need to do with Linux so all the safety and security of which you talk about is moot point, I am still forced to use Windows.


Yes that is true.  However, Ubuntu is designed to work with the internet.  You can work without it, but it is much more difficult without the internet.  Now for working with out the internet, you would want something more like Debian which has 15 discs with a full set, so you don't need the net to download anything.  Note: Debian is not as easy to install as Ubuntu.

---

### Post by Bachstelze on 2006-11-29
> **Sef said:**
> you would want something more like Debian which has 15 discs with a full set, so you don't need the net to download anything.  Note: Debian is not as easy to install as Ubuntu.

Etch has 21 :) And the only difference I noticed with Ubuntu is that I had to manually install drivers for my NICs, quite a change from Woody :D Some people also find it lighter because it istalls much less stuff by defaut - in Etch, you only have a very basic GNOME.

---

### Post by turbojugend_gr on 2006-11-29
You have 3 choices:

1. Get over it, understand how things are with Ubuntu (extremely safe), and get hold of it's power (you need internet to follow almost all how-to's around, including wine's)

2. Learn and use OpenOffice.org Database (OO.org access like program) which can save your files in M$ Office formats too.

3. Install another distro, SuSE (both novell and OpenSuSE, Debian, Red Hat, or I don't know whatever else provides wine, in it's cds/dvds.

---

### Post by sergean2 on 2006-11-29
I just read that post about "Is Ubuntu for you".  I was well written and very useful.  I do remember though that one of the statements in this post was "Have an open mind" which seems to be lacking here.  I have never stated that I am opposed to the internet, use it all the time at work, nor have I said that my decisions don't have consequences, meaning I will have to work harder at understanding this than most.  I asked a question, if you do not want to help somebody with a very genuine interest in using and understanding this program but has a different view of things than you then shake your head and move on to the next thread.  We all start at different places here.

As far as Open Office Database, I have looked into it and like the program very much.  I use it at home for my personal projects.  However, the techincal issue is that none of my clients have this program and usually have other databases in Access.  It really doesn't make much sense to the client to have to get this program they are unfamiliar with just because I dislike Microsoft.  I work within the confines of their system not the other way around.

Bottom line is I like Ubuntu, and I may reverse my thoughts on connection to the internet once I get more familiar with it.  However, I cannot get familiar with it if I cannot use it and that is all I am trying to accomplish here. I just want to use the program.

---

### Post by turbojugend_gr on 2006-11-29
BY my first suggestion I wasn't at all trying to imply you are narrow minded, I just meant that ubuntu (not just the oss, the community itself) is internet  needy, you need a connection to the net to accomplish things, I could point a how-to get office on Linux, but that needs internet access to follow it, I don't know if you get what I mean, ubuntu is targeting users with internet (broadband mostly), that is why it only has one disk, it supposes you can fetch things from the web. Ubuntu targets these users, cause it is sure they will be perfectly satisfied with the level of security provided.

The above explains why I suggested using OO.org (which is there by default), or a another distro that has almost all packages in it's disks.

---

### Post by scc4fun on 2006-11-29
> **sergean2 said:**
> Being new to Ubuntu (about a week) I am having a problem installing a package.  Without the gory details I have narrowed it down to this.  I am trying to install libartsc0 and when I do I get the error message, "Error: Dependancy is not satisfiable:lib6".  I assume this message means that the installer is looking for the lib6 which is installed.  What am I missing?](*,) 

Please bear in mind that I am not connected to the internet (bad experience with viruses, worms and all the creepy crawlies on the internet) so I don't have that automatic download feature but have downloaded the files from work (I let them deal with the creepy crawlies)and taken them home on the flash drive.

Any suggestions to help out would be greatly appreciated.
Mike
You need the libc6 according to the [package]("http://packages.ubuntulinux.org/dapper/libs/libartsc0") site, and it must be version 2.3.4-1 or higher. The package in Dapper repos appears to be version 2.3.6-0ubuntu20. It is about 4,480 KB.

---

### Post by sergean2 on 2006-12-01
I downloaded version libc6_2.3.6-0ubuntu20_i386.deb and intalled it again just to make sure that it was not corrupted.  I then tried to install the libartsc0 packaga and still was recieving the same error message.  This is all very frustrating.

---

