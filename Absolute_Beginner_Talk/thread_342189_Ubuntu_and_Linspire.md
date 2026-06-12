---
title: "Ubuntu and Linspire"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by olddoser on 2007-01-19
So I have played with the live CD and am getting in the mind set to install Dapper.  But I have a question.  My IP(Juno) has software on their web site "Juno for Linspire" should this work with Ubuntu-Dapper?:confused: 

Thanks for any commets.

---

### Post by teaker1s on 2007-01-19
Okay I'll explain as I understand it. Linspire starts Debian with KDE and then linspire alter it as they wish. Now ubuntu is Debian which has been customised to ubuntu.



So the package may install perfectly or may cause problems-unless anyone has tried it then it's unknown

---

### Post by olddoser on 2007-01-19
Thanks tecker1s
Any suggestions on installing?

Has any one tried it.

---

### Post by teaker1s on 2007-01-19
you could either download package double click and package manager will appear and ask to install or use synaptic and add a cdrom source and install. I'm not sure what steps you could take to limit the risk. If I was to install it I would check for any broken packages before reboot and also make sure I knew the exact name of the package so I could remove it in recovery console if there was a problem.

Maybe someone will advise you more than i can

---

### Post by Sef on 2007-01-19
It may or may not work.   Linspire is based on Debian, but it is not the same as Debian.  The same applies to Ubuntu.  If you do want to try it, I would back up all my files and be prepared to reinstall Ubuntu in case you needed to reinstall.  A foreign package could break your system or cause problems that would necessitate a reinstall.

> you could either download package double click and package manager will appear and ask to install

This will only work with deb packages.  

> use synaptic and add a cdrom source and install.

This will work only if thepackage is in the repositories or on the cd.

---

### Post by olddoser on 2007-01-20
Since this is a new install guess the thing to do is try it, if things go wrong just clear and reinstall Ubuntu.

Also being a nOOb I don't think I know how to check for broken package.  Any one?

Thanks for comments sorry for the delay but been away.

---

### Post by Workinman57 on 2007-02-05
I found the Juno.deb file sometime ago. I installed with the Debian package installer (got from add and remove programs in Ubuntu 6.10). It installed to root/home and a few other places. It doesnt "run" when I click on the Icon but after going online via hard wired nic The Icon change to look like the blue and white Juno lunch Icon I have on my Windows desktop. New at this. Not sure if I have to use a dialer and I am not sure my modem is even loaded :-( Think it is as it shows a modem in hardware display. I am using a Dell 840 Laptop. Enabled "root" and tried from there also. Think the Juno software may only transmit to juno after a dialer is used to connect. Juno Likes there advertizing.

---

### Post by Darklighter137 on 2007-02-05
Friend, if you are on dial-up,  I believe you need to compile drivers for your modem, unless that is what the juno.deb is for.

---

### Post by Workinman57 on 2007-02-06
I see a medem in the device manager. also my wireless is listed. The wireless card is a 1450 PCI onboard. Shows up as a 2100 intel. But the drive apperas to be the same from the reading I have done to date. Modem is another story. I am sure you are correct as to compiling drivers. But Before I do that I am trying to verify that what Ubuntu has loaded doesnt work. I have found out I need to load Jave to run Juno and that it appears the Juno.deb files are just that. A dailer along with the app to run the juno required advertizing. Before I tost what Ubuntu installed I just want to be sure it doesnt work as far as drivers. I have never complied a driver. I will post all the links and info I have as soon as I can locate all the links and doco I have found on Net. I am in a Linux class at school and hope to get the instructor to help me verify a few things. Laptop in hand. He is savy "hacker" works for beer, too.

---

### Post by paker on 2007-02-21
I am a newbie setting up my friend's computer. Please help me what I need to do. So far I have installed Ubuntu 6.10 Edgy 32 bit. I also installed Java through Automatix. I am going to buy an external serial modem. Do I still need juno.deb? Thanks.

By the way, my friend has juno account, but I don't. Where can I get juno.deb?

---

### Post by yanqui on 2007-02-21
Is the modem a hardware modem or a winmodem?  That makes a difference as well; there are some programs written to allow linux distros to use a winmodem, but as I haven't tried any (yet) I can't vouch for their efficacy.

---

### Post by olddoser on 2007-02-21
Hi paker
Can't commet about Edgy as I have Dapper installed, with that said here is what I did with Juno.
The deb file that is discussed above is Juno for Linspire available at juno.com.  You will have to look around but it is there.  I loaded it on Dapper and no joy.  Mayby you can push the right buttons and make it work.

I did get access to Juno connecting a serial modem (winmodem was lost cause) then thru
system/administrator/networking set up with autodetect, my user name (including @juno.com) password, and local phone number (from windows machine) activated which caused it to dial and I was on the net when I started firefox.  Currently I have to connect from networking as the tray icon for modem doesn't seem to work well.
So I'm on the net thru juno even tho Juno said "must use our software", go figure.

Goog luck with Edgy.

---

### Post by Workinman57 on 2007-02-25
[http://my.juno.com/s/download](http://my.juno.com/s/download) is the link to Juno for Linspire	Version 1.0 | File Size 1.61MB | Release Date: 11/25/2003
Juno is now available for Linspire! This file contains everything you need to connect to the Internet on your Linux computer running the Linspire desktop. The Juno software downloads in seconds and fits on a floppy disk so you can keep a backup copy or install it on a friend's computer.

IMPORTANT: You may not distribute this proprietary software for commercial use or for any other distribution program without the written consent of Juno.For more information regarding distribution policies, please click here to visit the affiliates section of our Web site.

Can unpack and install juno.deb with GDebi package installer which can be added from add and remove progams

you must have java installed. You can find it in add and remove programs if you enable 3rd party software search in System>Administration>Software Sources at the toolbar.  

Installs luncher  in root home desktop. Has to be run as root (sudo) .  
I have not writing script to run from icon on user desktop yet I run juno in a terminal 

sudo /opt/juclient/runclient.sh  this lunch's dailer program. 

 I have to run sudo killall NetworkManager
Or I cannot connect via modem.

I used help from forums to load my winmodem first by the way.

---

