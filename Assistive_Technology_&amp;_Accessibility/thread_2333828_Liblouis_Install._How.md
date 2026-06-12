---
title: "Liblouis Install. How?"
date: 2016-08-13
forum: Assistive Technology &amp; Accessibility
---

### Post by birdman1959 on 2016-08-13
Hello, 
I have tried to find an answer to this for a week before posting here. I have come up with nothing, so that is why I post here.
I would only ask if you are going to ridicule me or tell me that has been posted about many times over, please reconsider.

My issue is, I cannot get Liblouis Braille translation software on my machine, a Sytem76 Kudu with Ubuntu 14.04.
I run this command:

```
sudo apt-get update
sudo apt-get install liblouis-data

```
And then, get this:

```
lem@lem-Kudu:~$ sudo apt-get update
[sudo] password for lem: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [95.7 kB]   
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]    
Hit:4 [http://ppa.launchpad.net/system76-dev/stable/ubuntu](http://ppa.launchpad.net/system76-dev/stable/ubuntu) xenial InRelease     
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [364 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [359 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [314 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [310 kB]
Fetched 1,537 kB in 1s (1,016 kB/s)                      
Reading package lists... Done
lem@lem-Kudu:~$ sudo apt-get install liblouis-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  liblouis-bin
0 upgraded, 1 newly installed, 0 to remove and 45 not upgraded.
Need to get 23.2 kB of archives.
After this operation, 122 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 liblouis-bin amd64 2.6.4-2 [23.2 kB]
Fetched 23.2 kB in 0s (108 kB/s)       
Selecting previously unselected package liblouis-bin.
(Reading database ... 186443 files and directories currently installed.)
Preparing to unpack .../liblouis-bin_2.6.4-2_amd64.deb ...
Unpacking liblouis-bin (2.6.4-2) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up liblouis-bin (2.6.4-2) ...
lem@lem-Kudu:~$ 

```
What do I do after that? When I run a search to try to find out where whatever I
just downloaded, went, nothing comes up. The search function says nothing with
 "Liblouis" is on my machine despite the what the terminal says . . . 
So, in short, I want to get this liblouis braille translation software on my machine
but cannot figure out what I am doing or even looking for. As a new Linux user, this
and similar software situations have been very frustrating. There is no contact info 
on the Liblouis page. I would be eternally grateful if someone might provide some 
information about this designed for a person who has virtually no knowledge of this 
stuff.  Thanks in advance!

---

### Post by steeldriver on 2016-08-13
Hello and welcome to the forums

I have no experience with liblouis, but I think if you are expecting it to provide an actual translation application you may be disappointed - it looks like it basically a library package for people wishing to develop their own translation applications.

According to the [Liblouis User’s and Programmer’s Manual]("http://liblouis.org/documentation/liblouis.html#Who-is-this-manual-for"):

> 
This manual is probably not for people who are looking for some turn-key braille translation software.


Based on the [liblouis-bin filelist]("http://packages.ubuntu.com/xenial/amd64/liblouis-bin/filelist") the only executable programs it seems to provide are

```

/usr/bin/lou_allround
/usr/bin/lou_checkhyphens
/usr/bin/lou_checktable
/usr/bin/lou_debug
/usr/bin/lou_translate

```

which appear to be low-level utilities

---

### Post by birdman1959 on 2016-08-13
> **steeldriver said:**
> Hello and welcome to the forums

I have no experience with liblouis, but I think if you are expecting it to provide an actual translation application you may be disappointed - it looks like it basically a library package for people wishing to develop their own translation applications.

According to the [Liblouis User&#8217;s and Programmer&#8217;s Manual]("http://liblouis.org/documentation/liblouis.html#Who-is-this-manual-for"):



Based on the [liblouis-bin filelist]("http://packages.ubuntu.com/xenial/amd64/liblouis-bin/filelist") the only executable programs it seems to provide are

```

/usr/bin/lou_allround
/usr/bin/lou_checkhyphens
/usr/bin/lou_checktable
/usr/bin/lou_debug
/usr/bin/lou_translate

```

which appear to be low-level utilities


Hello Steeldriver,
Thank you very much for your response. Maybe I deserve some of the ridicule I was worried about getting?
Most people who do what I do, use Windows and software devoted to Windows, so thats where the majority
of the knowldgebase is. When I do what research I can on Linux, In the small circle of people who do what I
 am *trying* to do, the Liblouis software is mentioned regularly.
When I go to the page, this is the heading:

[SIZE=3][I]"Liblouis*The Liblouis software suite provides an open-source braille translator, back-translator and formatter for a large number of languages and braille codes. It is a set of libraries designed for usein any of a number 
of applications, both free and commercial. It is written in C so that it does not require a runtime environment and hence can be used in applications written in high-level languages such as Java and Python."[/I][/SIZE]

I wrongly interprited this as meaning it would be a turn-key piece of software. So, back to the drawing board.
I am trying to create tactile artwork for braille embossers using LibreOffice and LibreDraw. It is proving to be quite a challenge.
What I do at my job, but only using the aforementioned Microsoft setup, I am trying to do from home using Linux/Ubuntu as a
complete Linux noob. I am determined to make it work despite overwhelming frustration.

Again, thank you very much for your civility and knowledgeable response and I think I am going to give up on trying to find a Turn-key
 piece of software and concentrate instead on just loading a braille font into LibreOffice and go from there . . . 
Regards,
LM from KY

---

### Post by steeldriver on 2016-08-13
Does anything here help? 

[http://odt2braille.sourceforge.net/](http://odt2braille.sourceforge.net/)

Regards

---

### Post by birdman1959 on 2016-08-13
Hello Steeldriver, 
As I check my notes, that was a site I visited early on and I think I passed them by because it appeared
they only supported OpenOffice which I believe has no continuing development or something like that . . . 
But, that was over a week ago. Upon revisiting, they have contact info and want to build a database of who 
is using their work. So, I think I am  going to contact them and tell them what I am trying to do and see if
they can offer any suggestions. 
Again, I really appreciate your help! I will update this thread when I achieve what I am trying to, in the
rare occurrence someone else might be trying to do what I am.
Regards

---

### Post by howefield on 2016-08-14
I know nothing of the the subject but would suggest reaching out to Jonathan Nadeau who is responsible for the [Sonar linux distribution]("http://sonargnulinux.com/"). A distribution which is developed for individuals with accessibility needs with assistive technology., if he can't help himself perhaps at least help point you in the right direction.

Also does this thread help.. [http://stackoverflow.com/questions/29224414/getting-liblouis-to-run-and-translate-on-a-raspberry-pi](http://stackoverflow.com/questions/29224414/getting-liblouis-to-run-and-translate-on-a-raspberry-pi) ?

---

