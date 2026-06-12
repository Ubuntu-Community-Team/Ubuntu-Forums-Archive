---
title: "Setting up Ubuntu/kubuntu for a small school"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by Athanasius on 2006-03-13
I am no IT so I need some help.

Basically, I am the computer guy (a Franciscan Friar, actually), at our very small high school.  We have five computers that our students are using and I want to have ubuntu/kubuntu installed on the computers.  I am able to install the program just fine and cruise the forums for troubleshooting info.  

What I am looking for is a certain configuration of ubuntu so that the students can use any of the five computers as work stations and all of their OpenOffice files to be saved and retreived to one central harddrive.  We do not have any special server equipment; we have five Sempron desktops, all with network cards, a router with a cable modem and that is all.  I have my own computer but  it is cental to the operation of our monastery and I am not ready to migrate to Linux on that.

Please help me because I am tired of the students figuring our all the loopholes in M$.

---

### Post by Sef on 2006-03-13
Take a look at edubuntu.  It is designed for schools.

[https://wiki.ubuntu.com/EdubuntuWiki?action=show&redirect=EduBuntu]("https://wiki.ubuntu.com/EdubuntuWiki?action=show&redirect=EduBuntu")

---

### Post by Athanasius on 2006-03-13
I am having trouble with edubuntu and I would like to learn ubuntu/kubuntu better.  There must be a way to do what I want in ubuntu, right?

---

### Post by bjweeks on 2006-03-13
[QUOTE=Athanasius]I am having trouble with edubuntu and I would like to learn ubuntu/kubuntu better.  There must be a way to do what I want in ubuntu, right?[/QUOTE]

Edubuntu is the way to go  for ease of use.

---

### Post by meborc on 2006-03-13
well... for learning more about edubuntu:

[http://www.edubuntu.com/](http://www.edubuntu.com/)
[https://wiki.edubuntu.org/](https://wiki.edubuntu.org/)

and edubuntu/ubuntu/kubuntu are closely related, so if you have problems with edubuntu, you will probably face the same problems in the other ones...

although yout two first sentences make me think :-| > I am no IT so I need some help. >=< Basically, I am the computer guy 

---

### Post by Sef on 2006-03-13
> I am having trouble with edubuntu

What problems are you having with edubuntu?

contact info:

[https://wiki.ubuntu.com/EdubuntuWiki?action=show&redirect=EduBuntu]("https://wiki.ubuntu.com/EdubuntuWiki?action=show&redirect=EduBuntu")

---

### Post by jjf on 2006-03-13
Hi, Athanasius.  I'm in a similar situation as the merely semi-knowledgeable "computer guy" for our small private school.  I've installed Edubuntu on our computers, but mainly for its software.  I don't use the server/thin client model that it is built for.  I think if that is what you wanted to do, Edubuntu would be the easiest way.

Still, I wonder if it would be possible, with only 5 computers, to achieve similar results just with networking in Ubuntu.  Have you tried setting up the students' home directories so that they reside on the hard drive of your server computer?  Under the System > Users menu, you can change the path to a user's home directory.  I know very little about networking protocols, but my first guess would be something like this:

ssh://server_name/home/student1

---

### Post by Brunellus on 2006-03-13
[QUOTE=Athanasius]I am no IT so I need some help.

Basically, I am the computer guy (a Franciscan Friar, actually), at our very small high school.  We have five computers that our students are using and I want to have ubuntu/kubuntu installed on the computers.  I am able to install the program just fine and cruise the forums for troubleshooting info.  

What I am looking for is a certain configuration of ubuntu so that the students can use any of the five computers as work stations and all of their OpenOffice files to be saved and retreived to one central harddrive.  We do not have any special server equipment; we have five Sempron desktops, all with network cards, a router with a cable modem and that is all.  I have my own computer but  it is cental to the operation of our monastery and I am not ready to migrate to Linux on that.

Please help me because I am tired of the students figuring our all the loopholes in M$.[/QUOTE]
I'm going to echo everybody else's sentiments, here and ask what problems you were experiencing with edubuntu.  Your situation is what edubuntu was designed for (and getting all the other bits and pieces together separately is a pain).  

The alternative (which would be tiresome) would be to set up a shared directory on one computer, and then give each user a separate user account on each separate workstation.  

Good luck, brother.

---

### Post by Athanasius on 2006-03-13
I tried the dapper flight 4 and I am totally confused by all the server configuring that has to be done at the beginning.  When I finally get everything installed the internet doesn't work.. I think it might have something to do with the proxy, I have never dealt with that before.  How do I make it work?

---

### Post by Brunellus on 2006-03-13
[QUOTE=Athanasius]I tried the dapper flight 4 and I am totally confused by all the server configuring that has to be done at the beginning.  When I finally get everything installed the internet doesn't work.. I think it might have something to do with the proxy, I have never dealt with that before.  How do I make it work?[/QUOTE]
Dapper isn't stable yet, so it should probably not be used for production use (which is what you aim to use it for).    (I know there are going to be dozens of guys who run Dapper who will say it's OK for them, but still, better safe...)

A dumb question:  can your clients boot from the network?  if not, you may need to either make boot disks for them, or get a hold of network cards that allow network booting.

---

### Post by Athanasius on 2006-03-13
I do not know what network booting is.  It sounds good though.

I am confused with all the network information that it wants.  Will edubundu allow the students to save to a central location?  

Also, what is meant by "thin client".

---

