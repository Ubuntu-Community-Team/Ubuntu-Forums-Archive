---
title: "Newbie to Linux setting up a server"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by amazon3d on 2007-08-04
I've been dealing with Windows since 3.1 so moving to another OS is a long awaited/frightening experience.  
I want to set up a PC to act as a Network server.   
I want the server to host Files.
I want it to host an internal website.
Also is it possible to have a server hose applications (such as school programs etc.)  so that they don't have to be installed on the machine you want to use the software on?  

I haven't used any "server" edition software so I'm kinda new to that side, I've used Ventrilo & Team Speak to run VOIP off a desktop but I haven't gotten to the fileserver/appserver point yet.  I have a hard time reading extensive writings so if anyone has multimedia that would make my learning process much much quicker :)

Any help is very much appreciated!

Best Regards,
Amazon3d

---

### Post by Brunellus on 2007-08-04
Understand one thing about Linux and servers: 

when *nix users talk about "servers," we usually mean computers without keyboards and without monitors, which are administered remotely over ssh.  Very efficient, but a bit scary for people who haven't seen a command line ever.

You *could* run services off a regular "desktop" install, of course, which is more warm and fuzzy and GUI.  

Given your needs, you should probably investigate Edubuntu.

---

### Post by SirGrant on 2007-08-04
> **amazon3d said:**
> I've been dealing with Windows since 3.1 so moving to another OS is a long awaited/frightening experience.  
I want to set up a PC to act as a Network server.   
I want the server to host Files.
I want it to host an internal website.
Also is it possible to have a server hose applications (such as school programs etc.)  so that they don't have to be installed on the machine you want to use the software on?  



1 - For the network/file server you want to use a program called SAMBA 
2 - To host a website (external/internal) use a program called Apache
3 - Not so sure but if it's linux programs try edubuntu

Also yeah be aware brunellus is right most people consider servers keyboard/mouse/monitorless boxes that you connect to remotely over command line with no actual graphics.  This saves resources from being wasted on drawing the screen so all the energy can go into serving.

What I would suggjest if you are serious about this is try a GUI install and try to install samba and apache with that using the terminal and get familiar with it.  There are plenty of guides on how to do it.  Also look up the commands as you go so you learn what you are doing.  Then if all goes well try reinstalling with the server version and then doing it that way.

---

### Post by amazon3d on 2007-08-06
The last part is perhaps one of the most important questions. Is it possible to use a server to host a program such as photoshop, Adobe GoLive, or something less complex such as school information logging software?  As in not having to install the software on each machine but having it globally available threw the server?

---

### Post by amazon3d on 2007-08-06
Also Im having a hard time understanding the Thin client and server concept,  How do you install thin clients &  a server?

---

### Post by proalan on 2007-08-06
An explanation about thin clients at [http://en.wikipedia.org/wiki/Thin_client](http://en.wikipedia.org/wiki/Thin_client)

Unless you expect heavy traffic load serving many computers or require really fast performance a normal desktop install of ubuntu or edubuntu will work just as well. 

the xserver deals with the graphical side of linux and if it is installed on the server you can log into that server remotely and have it appear as your local desktop.

---

### Post by amazon3d on 2007-08-12
I just purchased a Dell Power Edge 1550.  I realize now that I don't think I will be able to get MS SBS 2k3 for the $88 that I thought (for an NPO)  I think I may end up using Ubuntu or edu for it.  Is there a way I can find out if the hardware will be compatible?

2x Pent. III 1ghz
2gb ram (4x 512mb)
2x 36gb SCSI Hdds
(2x 10/100 E-net ports)

Also looking for a low cost compatible 1000mb NIC for it.

I realized it after I had done alot of research that I there was a small clause that might not allow me to get MS SBS so I want to have a backup plan.   

I will need to run a very very secure server, it will have student records on it.   It will be used for record storage and maby thin client serving?

---

### Post by steveneddy on 2007-08-12
You could experiment with regular Ubuntu by installing Apache Web server, Samba for file sharing and VNC for remote access. 

```
Also is it possible to have a server hose applications (such as school programs etc.) 
so that they don't have to be installed on the machine you want to use the software on?

```


I don't know about that one but I know it can be done. Just keep asking the right people.

I have a web server, VNC server, Samba server and music server on one machine and it runs very nice. I run it headless (without monitor, mouse and keyboard) access it through VNC and it streams music through out the house, serves our files to every PC in the house and hosts a small web page for work purposes and file sharing capabilities for myself and colleagues. 

After I buy a couple of extra large hard drives at the end of the year, I will run the server edition of Ubuntu and ditch my Dapper Ubuntu install.

We also partition up the HD's of the other PC's in the house and everyone hosts some files for everyone else, so actually, all the machines are Samba servers and clients at the same time.

---

### Post by amazon3d on 2007-08-13
Well after doing some digging for a 1550 manual threw google I found that it supports 6-36gb HDDs.  Now does that mean I cannot add a 174gb SCSI or would those be old numbers?

---

