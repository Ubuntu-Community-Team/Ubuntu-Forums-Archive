---
title: "X Window System Problem??"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Stevo0687 on 2007-04-04
I have tried installing Ubuntu 6.10.  I had 6.06LTS running but un-installed it before installing XP and Vista.  So now I am trying to install Ubuntu also.  I have a few friends that have done it so thats not the problem.  I know it can be done.

My problem is I get an error when I try to install from the CD.  I believe I had this error with 6.06 but I could just run the live graphical safe mode and install it from that and everything seemed to work.  This time it doesn't seem to be working like that.  

Here is the message:



X Window System Version 7.1.1
Release Date: 12 May 2006
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux ubuntu 2.6.17-10-generic #2 smp Fri
Oct 13 18:45:35 UTC 2006 i868
           Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
           to make sure you have the latest version
Module Loader present
Markers: (--) probed, (**) from config file (==) default setting
(WW) warning, (EE) error, (NI) not implemented, (??) unknown
(==) Log file: "/var/log/xorg.O.log", Time: Wed Apr 4 17:15:34 2007
(==) Using config file: "/etc/x11/xorg.conf"





I went to http:wiki.x.org but was lost and didn't know how to use it to help me.  Does anyone know what the problem is?  How do I get the latest version.  The latest version of what? lol  Thanks in advance.

---

### Post by dbbolton on 2007-04-04
did you check the md5 sum on the iso before burning it ?

---

### Post by LaurelLynn on 2007-04-04
Dear Stevo0687,

The first question is do you really need to upgrade to 6.10?

6.06LTS is a long term support distro so it will still be updated for some time. I tried 6.10 for a new machine and went back to Dapper because no modem (a pathetic need I know but it´s all I got). I´ve read of several others having hardware problems with Edgy (rumour has it the source is really a debian update bundled in, but who knows with rumours).

If you have to move up, you might consider trying to upgrade from Dapper (this is from the ¨Linux Cookbook¨ under ¨Upgrading a Debian System¨ so don´t blame my, I haven´t tried it)

Reinstall Dapper(6.06LTS) then:

#apt-get update
#apt-get -u upgrade
#apt-get -u dist-upgrade

The book claims this will work...in several hours.

I would look around the forum first though I believe I saw specific Dapper->Edgy upgrade instruction somewhere.

Hope that helps,  Laurel Lynn

---

### Post by Stevo0687 on 2007-04-04
> **dbbolton said:**
> did you check the md5 sum on the iso before burning it ?

Nope, what that? lol


And LL.  I do not need to use 6.10.  If 6.06 is fairly good then I don't mind trying that again.  I just got the impression that I should go with the 6.10, but I don't have to.   And I can always upgrade later can't I?  I mean even if I have to reinstall the whole thing and can't just upgrade, I have my files on a shared partition so thats not a big deal.  All I'd have to worry about is setting everything in Ubuntu up again.  Not a big deal I don't think.  

So unless someone has another idea maybe I'll just try 6.06LTS again.  Any suggestions?

---

### Post by LaurelLynn on 2007-04-05
Dear Stevo,

Still running Dapper is like a windows user who is still running XP instead of going out and buying a new Vista box (nobody recommends upgrading to Vista). I just read this morning  Dvorak advising XP users to wait till Vista SP1.

Dapper still has a few years of life in it.  I will no doubt upgrade in sometime next year...when all the bugs are out. I´ve done years of PC repair work and everyone thinks they ¨should¨ upgrade long before they really need to.  My advice is upgrade when you find something your missing out on and gotta have.

Laurel Lynn

---

