---
title: "Wireless Internet"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by calichickaz on 2006-02-25
Hey Everyone,

I am not that computer savy, I do know the normal applications though. I had a computer donated to my family and it has this operating software on it. I am trying to make it so that it can connect to my wireless DSL. I have a Linksys USB connector and am wondering how to install it on the computer. 

Thank you for any help that you have :)

---

### Post by veruus on 2006-02-25
Wireless DSL?

Do you mean that you have a DSL modem and a router with a built in wireless access point?

What model of USB wireless adapter do you have?  Can you give us the numbers on the back of it?

---

### Post by seismic on 2006-02-25
Hi, I hope I'm not hijacking this thread but calichickaz an me seem to be in the same spot wireless-wise. So maybe you might save some time and deal with both of us at once.
I have the Samsung SWL-2300U wireless adapter which ubuntu can see but does not recognise as a networking device. just a "unknown USB device".
So, what next?
thanks in advance and again, sorry calichickaz for barging in

---

### Post by DrCrock on 2006-02-25
Any room for another?

I have a linksys wireless usb adapter, wusb54g hooked up to wrt54g router.  To date ive been unsuccessful with accessing the internet through a couple of linux distro's being suse 9.1 and even knoppix live cd.  ive downloaded ubuntu but wondered if you could advise how to get this working.  Ive read some information regarding ndiswrapper, is this an application that needs to be used in order for the drivers to work on linux?  Thanks

---

### Post by dralaroc on 2006-02-25
Yup I am stuck too.  I will patiently wait in line.

---

### Post by calichickaz on 2006-02-25
I have Yahoo! SBC DSL. I am using a Linksys Wireless-G USB Network Adapter, 2.4 GHz, 802.11g. 

Model- WUSB54G ver 4
S/N- MEQ20ES24880
MAC- 001217735B09

when I plug it in, it comes up on the screen that it's there, but it doesn't give me anymore than that

---

### Post by DrCrock on 2006-02-25
Yep thats the same model as mine, im still trying to work it out ive d/l ndiswrapper which i believe wraps round the windows drivers and gets it going.  If i sus it out i will let you know.  Likewise if you guys figure it out could you keep us updated.  Thanks

---

### Post by AndyCooll on 2006-02-25
Setting up wireless can be tricky. First of all you need to find out which chipset your wireless card uses. 

Ndiswrapper works by "wrapping" around the windows drivers. However, it may be that you can use native Linux drivers and avoid using ndiswrapper altogether.

A couple of places you might like to start are here:
[WifiDocs]("https://wiki.ubuntu.com/WifiDocs")
[rt2x00 drivers]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads")

---

### Post by thetruth on 2006-07-18
Hi

I am not an expert but this is how i set up my router
first thing first

terminal----> lspci 
if you see wireless then it will work if not than i stop right here as i do not know. procede

Code:
Sudo gedit /etc/network/interfaces
you will get a text editor screen
keep these lines
------------------------
auto lo
iface lo inet loopback
------------------------


 save and exit

 go to  systems----->  admin----> synaptic package manager
Install network manager
configure it by activating wireless
then click on  little mouse on the top right handside
you must see a signal and clcick on it you will be asked to input Password 
do that and hopefuly it will work. you may have to click on connection properties and change eth0 if you have a wired network 
Good luck

---

