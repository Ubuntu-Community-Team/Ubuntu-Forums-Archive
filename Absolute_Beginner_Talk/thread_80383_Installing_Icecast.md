---
title: "Installing Icecast"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by DJ-Power on 2005-10-22
Hi, I am am absolute newbie to all this (have only been running linux for  weeks) and I have managed to get most everything I want to do with the basics up and running. Now my problem is Icecast. Because it is not in the add programs section I downloaded the tar,gz version of Icecast from their site. Now I am stuck:confused: 
How do I get this installed on my ubuntu system. I tried what it says in the readme and it doesnt work. Any one out there done this before? I would think the procedure must be the same for any tar.gz intstall so it would be really useful for me to know. I love this OS and really really want to get to grips with it so I can finally kiss goodbye to windows forever :razz: 
Heres hoping
DJP

---

### Post by Iandefor on 2005-10-22
Open a terminal and type in ```
sudo aptitude install icecast2
```
Tell me if that works. Good luck in kicking the Big M!

---

### Post by DJ-Power on 2005-10-22
Thanks for the reply. I did as you said and this is what i got.
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

I am not sure if that means it set up or not and how do i actually run it?
Rgds DJP

---

### Post by Xian on 2005-10-22
Refresh your package source list:

```
$ sudo aptitude update
```

Then try the installation again.
Here are the results on my system:

```
$ sudo aptitude install icecast2
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be automatically installed:
  ices2
The following NEW packages will be installed:
  icecast2 ices2
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 232kB of archives. After unpacking 819kB will be used.
Do you want to continue? [Y/n/?]
```

---

### Post by DJ-Power on 2005-10-22
I just tried what you said but I got the same result. I am wondering if maybe I have got icecast installed somehow with all the different ways of trying but if so i cant work out how to run the icecast program.
Rgds DJP

---

### Post by Xian on 2005-10-22
[QUOTE=DJ-Power]I just tried what you said but I got the same result. I am wondering if maybe I have got icecast installed somehow with all the different ways of trying but if so i cant work out how to run the icecast program.[/QUOTE]
Okay, check to see if you have it installed:

```
$ sudo apt-cache policy icecast2
icecast2:
  Installed: 2.2.0-2
  Candidate: 2.2.0-2
  Version table:
 *** 2.2.0-2 0
        500 http://us.archive.ubuntu.com breezy/universe Packages
        100 /var/lib/dpkg/status
```

---

### Post by DJ-Power on 2005-10-22
icecast2:
  Installed: 2.2.0-2
  Candidate: 2.2.0-2
  Version table:
 *** 2.2.0-2 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages
        100 /var/lib/dpkg/status

Yes indeed somehow I have got it installed it would seem. Now how the heck do i make it run? Jeeze I wish my brain didnt hurt lol.
Rgds DJP

---

### Post by Iandefor on 2005-10-22
[QUOTE=DJ-Power]icecast2:
  Installed: 2.2.0-2
  Candidate: 2.2.0-2
  Version table:
 *** 2.2.0-2 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages
        100 /var/lib/dpkg/status

Yes indeed somehow I have got it installed it would seem. Now how the heck do i make it run? Jeeze I wish my brain didnt hurt lol.
Rgds DJP[/QUOTE]

Wow. type in icecast2 and see if that spits out a usage statement. If it doesn't, you don't have it installed yet. BTW, the command to make it run seems to be "icecast2 -b"

---

### Post by WillySpanks on 2007-02-07
I can't figure out how to install icecast.  When I type:

sudo apt-get install icecast2

This is what happens:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package icecast2


I'm running Dapper Drake.

Why isn't this as simple for me as it is for others?

---

