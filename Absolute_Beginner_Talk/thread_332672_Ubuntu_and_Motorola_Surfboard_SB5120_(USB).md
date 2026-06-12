---
title: "Ubuntu and Motorola Surfboard SB5120 (USB)"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by RKCole on 2007-01-06
Hello, everyone.

I've been searching on this topic for awhile now and I have not been too successful in finding an answer (or maybe my searching skills are not really up to par).

I have a Motorola SurfBoard SB5120 modem with an Internet connection via USB.  I used to use an Ethernet connection, but I recently purchased an Xbox 360 and I use Windows' Internet Connection Sharing to access Xbox Live (so I had to use the USB connection feature for my PC's Internet connection as I cannot afford a router at this time).  This is all fine in Windows, but I'm not sure how to get Ubuntu to see the USB Internet connection.  Is this possible?  And if so, how can this be done?

Thanks, everyone for any help and suggestions.

Take care.

---

### Post by RKCole on 2007-01-11
Sorry guys...I don't typically like to bump messages (as I know it can quickly become somewhat of an annoyance), but I must do so for this one.

I still have not figured this one out on my own...I don't know what I'm missing as Ubuntu sees the modem itself, but it does not see the USB Internet connection.

Thanks for any help provided.

Take care, everyone.

---

### Post by luvinit on 2007-01-12
I think the only thing you can do is a general search to see if a driver exists for it.  You can't avoid this problem as long as it is the norm for hardware manufacturers not to be interested. I have a surfboard sb5100, but it had dual connections so I can put in the network card. I believe that is the case for you according to this

[http://www.linuxquestions.org/questions/showthread.php?t=297790](http://www.linuxquestions.org/questions/showthread.php?t=297790)

---

### Post by Zzl1xndd on 2007-01-12
As far as i  know there is no driver for any of the SB5100 series. Honestly your best bet it to just get a router.

---

### Post by RKCole on 2007-01-12
Thanks for the input.

I found this:
[http://broadband.motorola.com/consumers/products/sb5120/](http://broadband.motorola.com/consumers/products/sb5120/)

It says that it works with Linux under the System Requirements, so I am not going to give up hope yet.  

Worst Case Scenario: I'll write them and see what happens.  

If I get this working, I'll post back.  Otherwise I am just going to get a router.  Any recommendations?  I would need something cheap yet effective as my budget is rather limited, unfortunately.

Thanks again, everyone.

Take care.

---

### Post by klause81 on 2007-05-21
I finally manage to put it working on Ubuntu 7.04 :o

I only found real stuff about it in a polish (I think...) page: [http://forum.ubuntu.pl/viewtopic.php?p=128463](http://forum.ubuntu.pl/viewtopic.php?p=128463)

Here is the steps:

1. these modules must be loaded (add to /etc/modules to automatic load on boot):
cdc_ether
usbnet
uhci_hcd
rndis_host

2. add the attached file to /etc/udev/rules.d (here is the secret). Obs: remove ".txt" extension from the file name, its name must be only "99-motorola.rules"

3. add the line bellow to /etc/modprobe.d/arch/i386:
alias eth1 usbnet

4. add the lines bellow to /etc/network/interfaces
auto eth1
iface eth1 inet dhcp

just to make sure: unplug usb cable, turn off and turn on the modem, plug usb cable again.

Keywords: linux surfboard sb5120 sbv5120 usb ubuntu

---

### Post by RKCole on 2007-05-24
Thank you for this, klause81.

I moved in February, and now I have a wireless USB Dongle and a wireless router.  We plan to move again soon ( :( ) because of some problems in thsi area, so it may be that when I get Internet access again a SURFBoard modem will be present again.

Thanks for ereplying ot this.

Take care.

---

### Post by sr_nathan on 2007-10-15
i really thank you klause81.

:):popcorn:

this is why im with ubuntu!!!

---

### Post by nolan273 on 2007-10-18
Is the /etc/modules folder the same as /etc/modutils?  i cant' find the former folder on the drive anywhere?  Or do I need to create the 'modules folder

---

### Post by SamiDelovely on 2007-10-21
like the guy before me, i don't know where any of these files are, and besides. I need a step by step procedure on how to do EVERYThing. my ubuntu is the 7.0 one.

---

### Post by Yuzem on 2007-10-23
It does not work on Gutsy.
Any ideas?

---

### Post by Yuzem on 2007-11-01
Sorry to insist but:
Does anyone know how to make  this work in Gutsy?
I am using Feisty just because of this. :(

---

### Post by [ARB1D3_[00L3R on 2008-03-18
klause81 - worked like a charm!!! Thx!!!

Just for the others having problems, here is the step-by-step.

1) Check your "root" password. 
Go to "System" of your main menu, then to "Administration" > "Users and Groups". 
Select "root" in the menu and select "Properties". 
Check the box "Set password by hand" and create a password. Write it down.

2) Make sure you are "root".
, by going to "System" of your main menu and goto "Administration" > "Login Window"
-select the "Security" tab at the top and check the box "Allow Local System Administration" 
WARNING!!! Change this back as soon as your done with all of the steps!!!
Reboot and enter "root" as the user name and enter your password.
You are now in "root". Congratulations.

3) Set up your system.
A.  Open the FOLDER named "etc" in your "File System" and open the TEXT FILE "modules".
-Place your cursor at the end of the last line of text and hit {ENTER}.
-Paste the following:

cdc_ether
usbnet
uhci_hcd
rndis_host

-don't hit {ENTER} after "rndis_host", just save it.

B.  Open the FOLDER "etc/udev/rules.d" and place the file "99-motorolla.rules.txt"
- Right click the file, click "Properties", and change the name to "99-motorolla.rules" without the ".txt" extension.

C. Open the FILE "i386" in the FOLDER "etc/modprobe.d/arch/" and paste the text:

alias eth1 usbnet

-remember how you did this before? Same rules apply. No {ENTER} at the end.

D. Open the FILE "interfaces" in the FOLDER "etc/network" and paste the text:

auto eth1
iface eth1 inet dhcp

E. Reboot and CHANGE THOSE SECURITY SETTINGS BACK!!!( remember #2)

CONGRATS!!! You get a cookie!!!:lolflag:

Possible things you must do:
-You may have to unplug/reboot/replug your modem. I didn't, just reboot.

Didn't work? I found this on the web. Not mine, so I take no resposibility.

In step #2, replace the following;

cdc_ether
usbnet
uhci_hcd
rndis_host

-with the following

CDCEther
usb-ohci
usbcore

- I HAVE NOT TRIED THIS!!!

Additional gem:
Having trouble with your wireless keyboard? Hold the down arrow key while booting. 
Works on Labtec as well as others.

Thanks again klause81, yer the best!!!

Greg Mansheim

---

### Post by v.s on 2008-04-29
Hi, I'm new to Ubuntu and seem to have the same problem as these guys:
[http://ubuntuforums.org/showthread.php?t=766069](http://ubuntuforums.org/showthread.php?t=766069)

Does anyone know if this will work on Hardy Heron?

I have the same Motorola SURFboard cable modem and I was wondering if this would be an easy fix to bypass my Ethernet problem ... or would I end up with the same problem?

---

