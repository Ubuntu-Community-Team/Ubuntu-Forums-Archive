---
title: "Installing in wrong partition!"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by johnnymo87 on 2006-01-11
I have this problem during installation of Ubuntu Breezy 5.10. It has to do with where all my packages are installing.

I manually edit my partition table during installation so that it looks like this:
[I]
#1 primary 5.0 GB    ext3     /            [bootable]
#5 logical  14.0 GB   ext3     /home
#6 logical    1.6 GB   swap    swap
[/I]

When I am on part 2 of the installation (CD ejected, now installing packages), I reach 57% before an error message tells me I have run out of room.

I believe that the applications are installing to my swap partition instead of my / partition because I have tried smaller sizes of swap, and the package installation is proportionally less finished, and I have tried larger swap sizes (3GB!), and had all the packages install.

How do I fix this?

---

### Post by sjh on 2006-01-11
[QUOTE=johnnymo87]
I manually edit my partition table during installation so that it looks like this:
[I]
#1 primary 5.0 GB    ext3     /            [bootable]
#5 logical  14.0 GB   ext3     /home
#6 logical    1.6 GB   swap    swap
[/I]

[/QUOTE]


Just a guess but 5.0 GB may not be big enough for a full install.  My primary partition is over 7 GB and most of my data is on another HD.  I'd bump up the primary partition just to see if it works.

Good Luck
SJH

---

### Post by benplaut on 2006-01-12
you actually might not have enough swap. try putting in a gb from your /home

---

### Post by johnnymo87 on 2006-01-12
[QUOTE=benplaut]Just a guess but 5.0 GB may not be big enough for a full install. My primary partition is over 7 GB and most of my data is on another HD. I'd bump up the primary partition just to see if it works.
[/QUOTE]
I have tried / with more than 5 GB, since on all my tries, previous to this one, I have not seperated / from /home (thus I have tried up to 14 GB for /). So I think that's not what's causing this problem. 

But I have tried varying the size of my swap partition, which has given varying proportional results in the percent of packages it installs before running out of space. So I believe for some reason it uses my [1.6 GB] swap space to download the standard ubuntu 5.10 applications. 

Thanks for the advice though, I'll bump up the size of my / partition so I can avoid future problems. :)

My goal is to figure out how to get the applications to install to my / partition during the installation so that I can devout less of my tiny harddrive to the swap partition. Even moreso now that I need to peel 2 GB off my /home partition and add it to my / partition. *Any idea how to get the applications to install to the right place?*

P.S. Am I right in assuming that any file I put on my computer after I get it working will go in the /home partition, and no other? I can't start saving files to the / or swap partitions just because I'm running low space in the /home partition, right? I'm a newb to Linux and I don't understand all the theory behind what's going on with partitions.

---

### Post by johnnymo87 on 2006-01-12
[QUOTE=benplaut]you actually might not have enough swap. try putting in a gb from your /home[/QUOTE]

Wait, now I'm confused. I thought that swap was some type of magical partition that acts just like RAM (Seriously. I have no idea what swap really is). So stuff actually gets stored there permenantly?

---

### Post by benplaut on 2006-01-12
[QUOTE=johnnymo87]Wait, now I'm confused. I thought that swap some type of magical partition that acts just like RAM. So stuff actually gets stored there permenantly?[/QUOTE]

no, but the second stage of the installer may just go kaplutz (gaplutz for gnome :rolleyes: ) if it doesn't have enough.

What've you got to lose :cool:

---

### Post by johnnymo87 on 2006-01-12
[QUOTE=benplaut]What've you got to lose :cool:[/QUOTE]
Nothing. I guess I'm just being too picky with those extra 2 GB I have to throw into swap.

Thanks. :)

---

### Post by jorn on 2006-01-12
Just curious. How much RAM have you got on your pc?
A swap file is some space on your harddrive used when you go out of RAM.
Linux uses generally more RAM than windows, and for god performance the right amount of it is nessesary.
Regards -Jorn

---

### Post by chrism7 on 2006-01-12
I installed fine with 128mb ram and a ~600mb swap file.  I have 14 gb on  / (no separate home partition though).  Being a beginner myself, I have no suggestions though as to why it didn't work for you, just giving my (extremely limited) experience.
Chris

---

### Post by johnnymo87 on 2006-01-12
[QUOTE=jorn]Just curious. How much RAM have you got on your pc?
A swap file is some space on your harddrive used when you go out of RAM.
Linux uses generally more RAM than windows, and for god performance the right amount of it is nessesary.
Regards -Jorn[/QUOTE]

I have 320 MB of RAM, and 3 GB of swap space. After trying to reinstall again, I'm wondering if I'm wrong about swap space affecting how many packages install (Details: It kept stopping on 57% (Ubuntu desktop), even with 3 GB of swap). So what do you recommend for swap space?

---

### Post by wyohermit on 2006-01-12
I don't really have any idea what is causing your problem.  However for a point of reference, I had no problem doing a Breezy install (later upgraded to Dapper) on the following configuration.
6.1g drive
    1.6g /
    1.0g home
    2.8g usr
      .7g swap
with 256mb ram

---

### Post by johnnymo87 on 2006-01-12
[QUOTE=wyohermit]I don't really have any idea what is causing your problem.  However for a point of reference, I had no problem doing a Breezy install (later upgraded to Dapper) on the following configuration.
6.1g drive
    1.6g /
    1.0g home
    2.8g usr
      .7g swap
with 256mb ram[/QUOTE]

Interesting. What is the 'usr' partition for?

I have the definition from [http://www.tldp.org/HOWTO/Partition/requirements.html#AEN493](http://www.tldp.org/HOWTO/Partition/requirements.html#AEN493) , but I don't know what it means. Here's it's definition:
[I]
/usr
This is where most executable binaries go. In addition, the kernel source tree goes here, and much documentation.
[/I]

What does that mean?

---

### Post by jorn on 2006-01-12
Have you tried to let the installer choose the partitioning for you?
And see what happens. Or have you done this already.
Jorn

---

### Post by wyohermit on 2006-01-12
The best analogy that I can think of right off is, it's like your program files dirrectory on a windows system.  The executeable binaries of any applications go here.  I am always trying new programs out, so that is why I have a relatively large partition for this. All of my data, mail and music are on another drive that can be shared wth my "stable" breezy version.

---

### Post by diggs on 2006-01-12
What you should try is bumping your swap down to 1 gig, the linux partition up 10gigs and formatting the 10 gig partition. should work. If it makes you feel any better I had the same problems on my laptop with dual boot, I think it was just the installer being gay. It works now, after a good 20 tries :S

---

### Post by johnnymo87 on 2006-01-12
[QUOTE=jorn]Have you tried to let the installer choose the partitioning for you?
And see what happens. Or have you done this already.
Jorn[/QUOTE]

Tried it.



Well, I think I found a way to work around the problem. I just finished the package installation manually with synaptic. I only have one problem, and it's related to where the package installation stopped. 

When I install, package installation stops at 57% on ubuntu desktop. When I finish it up with synaptic, all packages install except for one, which comes out broken. I tried "fix broken packages" under Edit in synaptic, but when I apply the changes and try to reinstall the package, it just breaks again.

The file is *ttf-arphic-bsmi00lp_2.10-6_all.deb*

Here's the error in the terminal:
```
Preconfiguring packages ...
(Reading database ... 59486 files and directories currently installed.)
Unpacking ttf-arphic-bsmi00lp (from .../ttf-arphic-bsmi00lp_2.10-6_all.deb) ...dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/ttf-arphic-bsmi00lp_2.10-6_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/fonts/truetype/arphic/bsmi00lp.ttf')
Errors were encountered while processing:
 /var/cache/apt/archives/ttf-arphic-bsmi00lp_2.10-6_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What should I do to resolve this?

Edit: Nevermind! I used my newly developed terminal skills to find the corrupted package, delete it, redownload it, and install it. I know am 100% installed. :)

---

