---
title: "Installing and Configuring A Linux Server"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by RavUn on 2007-08-07
I'm wanting to setup a 6.06 server on an old PC to mess around with and learn various stuff.  I've burned the .iso image and went through installing the LAMP server a few times but it seems like something has gone wrong each time I've tried.  I somehow managed to get to the point of partitioning the hard drive the first time and I put in swap space at the end and partitioned the entire hard drive so I got rid of windows (woohoo!).  But, something went wrong right after that and the installation could not complete.  I realized that I had skipped over loading the installer components and the CD did not pass the integrity check.

I reburned the image and have been going through it a few more times and each time it seems to stop right as it's loading the installer components.  The CD-ROM is mounted and read successfully and it starts loading everything and once it gets to around 97% it just kicks me to the installer main menu and it will not let me do anything else.  I try to load installer components and it kicks me back.  I try to move on and it says I have to complete something else first.  I've tried re-burning the CD a few times but it does not help.

Could it be possible that the .iso I downloaded is corrupt and that's preventing it from installing?

Or,
Is it because I do not have enough RAM?  I only have 48 MB of RAM and I was told I could run the LAMP server on there but it may not be enough RAM for the installer.  Someone was entertaining the idea of setting up swap space before installing so it has more memory to pull from, but neither of us knew how to do that.

I'm not very familiar with linux and this is my first time trying so I'm just wondering if anyone could help.  I've used the desktop version through a virtual appliance and I would like to setup my current PC to dual-boot until I finally get tired of my windows programs... but first I wanted to experiment with this old computer I found lying around.

Also, if anyone knows of good documentation for setting up everything AFTER installing the LAMP server then that would be greatly appreciated.  I've been searching and I mainly find bits and pieces and nothing tells you how to get to that point and where to go afterwards... it just says how to install and do basic configurations.  Since it's all CLI I'm wondering how easy it is to learn to get where you want to go if you don't know where you are starting....


Any help would be appreciated.  I'm really anxious to get this up and running so I can break something else.

---

### Post by tgm4883 on 2007-08-07
check your downloaded iso against its md5sum

---

### Post by RavUn on 2007-08-07
yea I did that and it matched up.  Does that mean the whole download is perfect then or does that only compare one important part?  If the .iso is fine then there's something screwy goin on... possibly not enough memory to continue....?  I'm guessing though.

---

### Post by dca on 2007-08-07
I'm out, the lowest ram count I ever loaded 606LTS server ed had 128MB.

---

### Post by Jimmyfj on 2007-08-07
The issues you mention is related to memory - System require min. 64 MB RAM to install:

[http://linux.about.com/od/ubusrv_doc/a/ubusg07t02.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg07t02.htm)

---

### Post by RavUn on 2007-08-07
Bunch of hooplah!  I figured it was the memory but just did not want to believe it.  I assumed that if it had enough RAM to run Windows it could run a CLI-only setup.  

I think I'll buy a little bit of RAM this weekend and give it another go.

Thank you for the help.

Anyone have any suggestions regarding this?

> Also, if anyone knows of good documentation for setting up everything AFTER installing the LAMP server then that would be greatly appreciated. I've been searching and I mainly find bits and pieces and nothing tells you how to get to that point and where to go afterwards... it just says how to install and do basic configurations. Since it's all CLI I'm wondering how easy it is to learn to get where you want to go if you don't know where you are starting....


Until I get the PC setup I think I will mess with configuring a server on a VM so I can become a little familiar.  I'm still scared of CLI... but I must press on.

---

### Post by Viruk on 2007-08-08
Have you tried the alternate CD for systems with low ram?

See [http://releases.ubuntu.com/6.06.1/](http://releases.ubuntu.com/6.06.1/) and look at the alternate CD information, the following information is taken from that page:

> Alternate install CDThe alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

creating pre-configured OEM systems; 
setting up automated deployments; 
upgrading from older installations without network access; 
LVM and/or RAID partitioning; 
installing GRUB to a location other than the Master Boot Record; 
installs on systems with less than about 192MB of RAM. 

There are three images available, each for a different type of computer:

From what I can see about your system you will want the i386 version. 

I installed an alternate CD of 6.06 around this time last year and managed to get it to work on an old test machine with 64meg RAM, although once I had finished testing I did a fresh install for the application I wanted to run on to better hardware.

If your just testing with this install and unfamiliar with the command line I would reccomend documenting everything you do, this will make it easier to re-do the set up later on, easier to ask for help (and remember which answers work for you) and theres the argument that writing things down helps you remember them. I use a wiki for documenting systems rather than pen and paper... 

Try that and let us know how you get on.

---

### Post by RavUn on 2007-08-08
Ok cool.  I really want to learn to use the CLI.  I'm slowly picking it up and I am just doing everything on a virtual machine until I get my old PC setup with more memory.

The main problem is I really have no clue what I'm doing.  I really just want to setup a server to test PHP and learn SQL but don't know what to do once I have those setup.  So, I'm just spending most of my time doing lots of searches.  Most places say how to set them up and I don't know where to go from there.

I've started documenting things a little at a time.  Once I do it I usually remember how to do it again though.  I should document more so it helps with questions though.  Hopefully I'll stumble across a tutorial someone wrote of the step-by-step process they took to install and configure a server and then add pages and information to it and making it secure and available online.

I'll be posting more on my findings for sure, and if I figure everything out I can do the step-by-step tutorial for newcomers.

---

### Post by tgm4883 on 2007-08-08
> **Viruk said:**
> Have you tried the alternate CD for systems with low ram?

See [http://releases.ubuntu.com/6.06.1/](http://releases.ubuntu.com/6.06.1/) and look at the alternate CD information, the following information is taken from that page:



From what I can see about your system you will want the i386 version. 

I installed an alternate CD of 6.06 around this time last year and managed to get it to work on an old test machine with 64meg RAM, although once I had finished testing I did a fresh install for the application I wanted to run on to better hardware.

If your just testing with this install and unfamiliar with the command line I would reccomend documenting everything you do, this will make it easier to re-do the set up later on, easier to ask for help (and remember which answers work for you) and theres the argument that writing things down helps you remember them. I use a wiki for documenting systems rather than pen and paper... 

Try that and let us know how you get on.

The alternate CD is not going to help him.  The alternate CD only works vs the LIVE cd because your using the text based installer.  He is using the Server install CD which is a text based installer too.

---

### Post by RavUn on 2007-08-08
So, I have a 512 MB PC133 and 128 MB PC133 in my desktop PC and I have 32 MB PC66 and 16 MB PC 66 in my old machine that I'm trying to turn into a server.  Is it possible to mix PC133 with PC66?

---

### Post by Viruk on 2007-08-09
You can mix them but its not worth it imo - if that was my kit I'd settle for the 512 + 128 and not using the 32 or 16 meg modules

If you did use them all the faster ram will be capped at the speed of the slower ram and with the size of the slower modules they won't give you an increase in peformance that will compensate for the the performance hit on the large modules.

What is it that you want to do with the server once its set up? That will impact what sort of guide you use. 

For now you could start with [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06), [http://www.howtoforge.com/ubuntu_debian_lamp_server](http://www.howtoforge.com/ubuntu_debian_lamp_server)  or [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

If you want to look at things after the basic lamp install you could look at something like [http://www.howtoforge.com/suhosin_php_debian_etch_ubuntu](http://www.howtoforge.com/suhosin_php_debian_etch_ubuntu)

If you know what you want to do there is probably a guide out there for it. 

I usually start with a guide like the ones listed above, but re-write it as I go, changing details for the specifics of my setup (a well documented task is easy to delegate ;) ) and making notes of the new things I learn and covering problems that came up that weren't covered in the original guide.

---

### Post by RavUn on 2007-08-09
As luck would have it, my dad stumbled across 2 128 cards at work and they said he could have them so I guess that solves that.  Now I get to do everything I've done over again and see how much I've really learned.

The things I want to try to do are:
1) host a website
2) learn PHP (I don't think I need a server to learn but I would like one so I can learn server-side commands)
3) figure out what the hell I can do with SQL... mySQL... whatever it is.
4) create a mail server so I can stop using hotmail.

I found a link at work that has TONS of information and it looks like it touches on each of those.  It also explains many of the general commands that most other places only refer to but do not say what they are.  I will post the link when I find it at work so people can know.

I've been browsing around howtoforge also.  I've found a lot of good stuff but some of it I don't know what it's meaning or saying.  It says to setup blah blah and I don't know what blah blah is but it may be something I need.

---

### Post by Viruk on 2007-08-10
There are also quite a lot of articles at [http://www.ubuntugeek.com/](http://www.ubuntugeek.com/) that may help you. 

The first things I set up when I install ubuntu server are:
ssh server so I can connect remotely
Webmin - for easy web based management 

I would reccomend both of those tools, but you may want to look at something like phpmyadmin instead...

Once I have done the initial setup I tend to run ubuntu servers with only power and a network lead connected as everything else can happen remotely.

---

