---
title: "Belkin wireless G MIMO troubs - first post"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by bmann11 on 2008-04-16
hello,
This is my first post in this forum, so hello to all.

After running a live cd for  a few days, I put 7.10 on the hard drive this morning.  This is my first foray in the Linux, it would be fair to call me a super-noob, although I'm digging on the Linux.

Anyway, my first trouble comes is not being able to connect to my wireless.  I have a  Belkin wireless G Plus MIMO router and a Dell TrueMobile 1300 WLAN PCI Card running on a Dell Latitude D600 with a 1.6 pentium.  I've been trying to figure this out for a few days with no luck.  Any help is appreciated.  Thanks.

---

### Post by nicedude on 2008-04-17
Ok bmann11, I am not a linux expert by any means either but I can help you do what you need to do in order to get your dell wifi card working on 7.10 Ubuntu. Your card has a Broadcom brand chipset (my laptop wifi card is made by atheros and my install is different so im not totally familiar with the method you will be using but I can still help you I ). Linux support for your Truemobile 1300 wifi card is accomplished with a linux program called Ndiswrapper which after you get it installed, it will allow you to install and use the standard windows XP wireless driver from dell for your card within Linux. Ndiswrapper is available to install from ubuntu's synaptic package manager (think super add remove programs system tool)  start by going to the top menu bar and clicking on system -- then click --> Administration --then --> select "Synaptic Package Manager" as it loads it will ask you for your password so type that in --> now that you have Synaptic package manager open click on settings in top bar - then click -> Repositories , this will bring up a window called Software Sources and in the first tab called Ubuntu Software put checks next to all the different ubuntu sources if they are not checked already ( ie. main universe metaverse restricted source) now close software sources window and click on reload in the synaptic toolbar ( any new software sources you just added will now be added to your Ubuntu's software catalog ) After that is complete click on the search button on Toolbar, now in the search box there are 2 fields you can enter stuff -- in the one called "look in" select name ( not name and description just name) then type "ndis" without the quotes in the box called search -- now click the small search button to begin the search. You should get the 3 software names  listed at bottom of this post, select each one by clicking the small white box next to each of them and selecting mark for installation, now as you select these three things it will tell you with some of them that it needs to install additional things just say ok by clicking "mark" on any windows saying this that pop up (see Linux is smart enough to figure out what it needs to function and figures it out for you) after marking the 3 things for install and any others it says it needs, click the green check mark that says Apply on the synaptic toolbar. After all those finish installing you will need to run the one you just installed called ndisgtk as root to do this copy this without the quotes "sudo ndisgtk" and paste it into a terminal window. (ie. applications --> accessories --> terminal ) once you paste that command hit enter and it will ask you for your password again since we are running that as root, Once started ndisgtk should open a small GUI Window and have a button that says "Install" before you click install you need to paste the following ftp web link in your web browser to get the XP Wifi Driver for your specific card from dell's ftp site --> [http://ftp.us.dell.com/network/R94827.EXE](http://ftp.us.dell.com/network/R94827.EXE)   When you paste it and click to go there it will just popup with download box, just click "save file". once this is done you click that install button in ndisgtk and point it to the driver file we just got from Dell (it should be on your desktop or in your home directory), at this point it should walk you through the last few clicks and once its done you should reboot your PC and you should have wifi card working on your Ubuntu laptop :-)   you can verify that it is working by opening a terminal and typing " iwconfig " with no quotes, this command will show you any wifi devices running on your PC.  If you followed all that and got it to show up then dance around some at this point. As far as for configuring your Belkin router it should be a piece of cake compared to installing that wifi card, if you can't get the router and laptop to network together or the above steps didn't work  for you, then you can PM me and I will try to help you.


The 3 things to check with Synaptic Package Manager
ndisgtk
ndiswrapper-common              
ndiswrapper-utils-1.9

---

