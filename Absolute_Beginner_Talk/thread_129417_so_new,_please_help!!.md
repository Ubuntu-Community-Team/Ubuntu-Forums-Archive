---
title: "so new, please help!!"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by chrluc on 2006-02-13
Hello all!
I have been lurking here for some time, and I cant seem to find the answers. havn't been using linux long... started out w/mandrake 10 then mandriva 2006and was told to switch to Ubuntu and I like it. Please keep in mind that all this has happened over the last 2 1/2 weeks. Still a novice. I have two problems first is the internet. I have comcast @ home and have read every post on comcast settings and have had no luck getting it to work (have also called comcast 4 times and have been told they dont support "it" at all) So no internet! No problem right... but every post i read on how to install programs is always thru the internet. I beleive they are called "repositories". I have downloaded several _.dep files to cd (on windows) and put the cd in the ubuntu system and all i get is "archive type not supported". The file I need is mplayer, so I tried the source thing and... ha ha we won't even go there. so many problems, the gcc is wrong and what is gkt2. What do I do?
please help... and forgive me, I'm shure I sound like a complete moron to most of you.
thanks

---

### Post by merlyn on 2006-02-13
Hi and welcome to Ubuntu, and Linux in general. :D

Firstly, what type of internet connection do you have, dialup, ADSL . . .

Also any info on the type of modem that you have could also be of help, internal / external, usb / ethernet . . .

This type of information will make it easier for others to assist you, as it will provide a means to weed out the source of the problem.

Sorry that I cannot offer more help to you on that one, as yet anyway.

Once you get your internet connection working there is a very useful tool included in Ubuntu for installing software called Synaptic. It manages dependencies, (required packages), very well indeed.

There is also a very useful little tool known as Gdebi, that makes it much easier to install downloaded .debs

In the meantime, and this can get messy . . .

With regard to installing packages the files that you actually need are .deb(s), forgive me for being pedantic, but then again it may simply have been a typing error on your part. 

A useful site to search for ubuntu .deb(s) is the Ubuntu Packages page, [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

Here you can search for the package you desire by name and according to the version of Ubuntu you are running. 

A list all the dependencies, and reccommended files, (and appropriate versions), required, will also be provided, with links.

As mentioned this can get a little messy, especially if further dependencies are required.

Doing things manually, as described above, though is not ideal.

Rest assured though that help will be forthcoming, the Ubuntu community are really helpful. In my experience the most helpful I have come across.

Sorry once again that I am unable to help you with your internet problem, to date.

Cheers.

---

### Post by Zerocool10482 on 2006-02-13
This will show what to do. But will a deb file make sure you have it in your home folder ok.

[https://wiki.ubuntu.com/InstallingSoftware](https://wiki.ubuntu.com/InstallingSoftware)

PS. Do you have DSL or Cable. Because you should be able to connect to the internet. But if you have DSL your screwed. Oh and if you have any other problems. Try the wiki. 

[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

Good luck. I'm a newbie to but can direct you in the right area ok. Keep trying ok.

---

### Post by Bartender on 2006-02-13
zero -
I'm a neophyte but thought that as long as the connection to the computer was via Ethernet cable DSL was as easy to get going as cable.  Is this not so?  Please explain!  I've been babbling on to other newbs telling them they were in fat city w/ either method.

---

### Post by abu-fatu on 2006-02-13
hi from an absolute begginer i have dsl and i was able to go on the internet with out any problem

---

### Post by shamrock_uk on 2006-02-13
[QUOTE=Bartender]zero -
I'm a neophyte but thought that as long as the connection to the computer was via Ethernet cable DSL was as easy to get going as cable.  Is this not so?  Please explain!  I've been babbling on to other newbs telling them they were in fat city w/ either method.[/QUOTE]
DSL works just fine with Linux. 

It's the modem you'll be having problems with, which is why it's so important for you to give us details like the manufacturer and model number...

Welcome to the forums. :)

---

### Post by russrex on 2006-02-14
I'm new to Ubuntu myself. Just a few days. I have Comcast also and have no problems with it at all...I would look elsewhere for the problem....cable modem.....nic card...etc.

Good luck

P.S You might want to try the live CD to see if it detects your network

---

### Post by mips on 2006-02-14
Brand & Model of DSL/Cable device ???

Post output of windows/dos  **ipconfig /all**  command here.

---

### Post by darf681 on 2006-02-14
Also, are you connecting your DSL modem to the computer, or to a router?  If you don't have a router, I would suggest picking one up, not only does it make your connection difficulties easier (configure the router to connect through your DSL modem, and then just point your PC @ the gateway on the router - no drivers or anything required and works for any OS), but most also provide a firewall against incoming traffic.

---

### Post by chrluc on 2006-02-14
thanks for all the response, I was told to go w/Ubuntu because of the great support this distro has... and so far I'm impressed. Well first the internet is cable and the modem is a moto surfboard the nic pcmcia card is a xircom RBEM56G-100 but to tell you the truth I dont know if is is working well w/ubuntu. And it is connected to the modem w an ethernet cable. As far as the file of mplayer I downloaded (.deb, it was a typo) I pulled it off the cd and transfered it to "home", was logged in as root and I still get an error. This is the 4th, different deb file (from different sources) and all give the same error.

---

### Post by David Corrales on 2006-02-14
The errors you're getting with the MPlayer .deb file are because you're lacking dependencies on your system. I'd work on getting internet up and working because apt-get will make your experience a lot easier.

---

### Post by mips on 2006-02-14
First try and get the ethernet working.

Start here:
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

Let us know where you get stuck and post the output of your commands here.

Might also want to post output of lspci, dmesg here.

---

