---
title: "Im about to give up"
date: 2008-09-22
forum: Apple Hardware Users
---

### Post by 3vilgenius on 2008-09-22
Ok, im about to give up on installing ubuntu server edition on my Old Mac G4,

Can someone please direct me to a guide specifically for a Mac G4 Digital Audio, or write 1 for me, as i love linux more then windos or OS X but cant seem to get the install right.

Also i wish to use it as a webserver and a file server

PLEASE HELP

Note: its PPC

From a nearly bald 3vilgenius,

p.s. Ive been pulling my hair out trying to get it to work

---

### Post by 3rdalbum on 2008-09-22
1. Are you using the PowerPC version of Ubuntu?

2. Ubuntu Server Edition does not have a GUI.

3. I don't believe there are any HOWTOs on what you're asking; it's a bit of a specialty area. At what point are you having trouble?

---

### Post by 3vilgenius on 2008-09-22
Sorry for sounding so demanding just getting frustrated, umm im using the Ubuntu ppc Server edition hardy heron 8.04

and i no its a speciality area that why asking if someone could write a guide for a newbie

Thanks From 3vilgenius

---

### Post by tiresia on 2008-09-22
Can you please be more specific? How did you download and burn you Installer CD?
If it is OK, you should be able to start just holding down C Key at start up.

---

### Post by 3vilgenius on 2008-09-22
Burnt the image using nero, and was able to boot on the mac

but i have no idea what setting and everything to do in the install and havent been able to install 8.04 but 7.04 worked and installed fine, but as i said before no idea what setting to pick, i just chose what ever and hoped for the best

the guides i did find werent for PPC and they were rather technical with lots of jargon

i really need something dead simple.

its mainly for file and web server

---

### Post by 3rdalbum on 2008-09-22
What went wrong in the install stage? What symptoms does your installed system display? Usually if you just choose the defaults during the installation, everything works fine.

There is an "expert" mode of installation. Press Tab at the Yaboot screen to see what to type in to get the expert mode. It gives you more options, and you might be able to figure out what to change to get things working properly.

---

### Post by mkvnmtr on 2008-09-22
Last night you told me that you had got an installation of the server 8.04. I think that is command line only. If you are not prepared for that it will be hard for you to proceed. I have no experience with the server edition but these other people do. You need to explain exactly what you have and where you are at so they can help you with the commands to proceed. It's pocible the first thing you want to do if you are not ready for the command lin is install a desktop. This stuff is really kind of easy there is just so much of it it's hard to remember and have at your fingertips.

---

### Post by 3vilgenius on 2008-09-22
Ok first problem is that every tutorial i have found has this as the startup screen, but whenever I install it does not have this screen

[IMG]http://linux.hostcurry.com/wp-content/uploads/2007/10/installfeistyfawn-large_001.png[/IMG]

Also was wondering is it possible to install the normal Ubuntu PPC not the server edition but still make it a server?

---

### Post by tiresia on 2008-09-22
You won't find that screen in the PPC Installer.
There are two ways to install s Desktop Ubuntu on a PPC.
1. Live CD (you can have a first impression how Ubuntu is)
2. Alternate CD (there is no 'desktop')
Anyway, if you don't have experience with Linux, you should install starting with the Live CD. You can download it following this Link (you should also the whole thrade)

What do you want to do with a server? Do you want to use it just for a Local Network? If so, you can just install the Desktop Version - you can install afterwards all the software you need - and it will be easier to get a first experience with Linux

---

### Post by 3vilgenius on 2008-09-22
i wish to setup it up as a Web server and File Server (file server just for lan)

umm yeah im thinking that unless i have a gui im going to struggle to much to get it going

---

### Post by tiresia on 2008-09-22
If you need a simple Web Server, where you have a simple Web-Site, you need just to install Apache. But you should read a bit more about it. If you have a Dynamic-IP, you can use a daemon (ddclient) to update you IP to a service like DynDNS.

For the File Server, all you need is a protocol Samba (you can use also Netatalk if you have another old Mac; anyway OSX can access Samba Protocol) 

So, go ahead, and install Ubuntu Hardy (8.04) 
When you are finished, you can install the software you need (it will take few minutes - but you should read more how to configure it according to your need)

---

### Post by 3vilgenius on 2008-09-22
OMG you are a god send, thankyou so much :D

---

