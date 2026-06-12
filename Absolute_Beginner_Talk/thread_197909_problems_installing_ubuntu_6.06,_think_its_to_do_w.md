---
title: "problems installing ubuntu 6.06, think its to do with partitioning"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by killkoy on 2006-06-16
This is my first post in these forums so hello everybody and hear goes ;)

Im a linux newbie, but i have done a fair bit of reading and have used mandrake before. However i am good at going at things with an open mind.

I recently decided to have a go at using linux and after some research decided that ubuntu was for me. 
I wanted to dual boot it with xp so i downloaded the live cd.
The live cd works fine if i used it in graphics safe mode.
However when i click on the installer icon the installer hangs after i have specified my partitions.
I tried setting up the partitions before installing using the gnome partitioner but that also crashes.
any help would be appreciated.
I have 2 hard drives (80gb sumsung and 250gb maxator) and i am trying to install it onto the second. There are already formatted ntfs partitions on the 1st half of this drive, i want to split the 2nd half so that it has a fat32 partition for sharing/storing files for both xp and ubuntu and a partition for ubuntu.
my system specs are 
cpu - amd64 939 3200+
gfx - nvidia 6800gs
motherboard - asus a8n
hdd - above

I downloaded the am64 version of the live cd

thanks in advance

---

### Post by xenblend on 2006-06-16
try the alternate cd, it worked for me after the live cd had its way with my computer... :p

---

### Post by killkoy on 2006-06-16
[QUOTE=xenblend]try the alternate cd, it worked for me after the live cd had its way with my computer... :p[/QUOTE]

thanks, does the alternate installer include partitioning tools to allow me to partition the unpartitioned section of my hard drive, also is it easy to use, so that i wont have to spend hours working out how to install :rolleyes:

---

### Post by brentoboy on 2006-06-16
yes, it has a partitioner, it will ask you if you want to "take over" the entire hard drive, or if you want to do things manually.

it is not completely manual, but it is in text mode.  it gives you menus and stuff so you can pick and choose what you want done.

I still trust the "alternative" cd more than the new live installer -- the new way is much cooler, but the old way has been stable for a long time ("stable" in debian means: really really stable, almost obselete it is so stable).

---

### Post by uteck on 2006-06-16
You can run gparted or qtparted from the install/live cd and then partition the drive, then run the installer.  I did that on my laptop and it worked fine.

---

### Post by killkoy on 2006-06-16
[QUOTE=brentoboy]yes, it has a partitioner, it will ask you if you want to "take over" the entire hard drive, or if you want to do things manually.

it is not completely manual, but it is in text mode.  it gives you menus and stuff so you can pick and choose what you want done.

I still trust the "alternative" cd more than the new live installer -- the new way is much cooler, but the old way has been stable for a long time ("stable" in debian means: really really stable, almost obselete it is so stable).[/QUOTE]

looks like ill be downloading the alternate cd then:p 
thanks everyone:mrgreen:

---

### Post by killkoy on 2006-06-17
Ok then ive installed ubuntu using the altenate install. It worked fine.
However when i boot into ubuntu i dont get a nice gui, i just get a coloured mishmash on the screen. Do i need graphics drivers, if so how do i get them and install.
i can still acces the terminal using ctrl alt f1
and i cant conect to the internet because the only way that i know of setting up the network is using gedit which seems to need a gui to work.

---

### Post by Herman on 2006-06-17
```
 i can still acces the terminal using ctrl alt f1
``` Yes, do that and then do the following,
```
# sudo dpkg-reconfigure xserver-xorg
```  
 This will bring up a series of grey panels with questions about your video hardware, monitor and keyboard.
 The first question is 'Attempt to autodetect video hardware? [yes]
 
It helps if you at least know the brand of your computer's video card, and any other information that you know or can find out may also be helpful. The questions you will be asked are rather difficult, if you don't know after reading the questions carefully, the default choices are usually right, so just press 'enter' if in doubt. When the questions finish you'll find yourself back at the same command prompt you began from. 
 
 Type # startx  and you should see your new login screen form before your eyes.

Regards, Herman :D

---

### Post by killkoy on 2006-06-17
ok then, ive just had several goes at setting those options and it hasnt worked. There was a slight improvement after the second try when i just got a measage saing that x cant start. but for all the other trys i just get the coloured lines on my screen.
my graphics card is a 6800gs pcie

Thanks, killkoy :D

---

### Post by Herman on 2006-06-17
First, have you looked through **[Dealing with problems with the Xserver]("http://www.ubuntuforums.org/showthread.php?t=187177")**, it has been 'stickied' in 'Installation & Upgrades' to help with this subject.

I have two commands here I haven't ever needed to test for myself, (so I don't know what they are like), but they might work. They are in my bag of tricks I have collected from reading other threads in this forum. I hope they will help you. try these if you don't see anything in the above thread.
```
 sudo apt-get install ubuntu-desktop
``` If your installation might be incomplete, that command will install the needed packages. If it gives you an error, try
```
 sudo apt-get -f install
``` 
And follow any instructions. 
Good luck, Regards, Herman :D

---

### Post by killkoy on 2006-06-17
sorry but i cant conect to the internet because the only way that i know of setting up the network is using gedit which seems to need a gui to work.
I assume i need to conect to the internet to use those commands??
I have tried re-installing ubuntu but that didnt make any difference.

On a side note the support in these forums is amazing, just looking through the titles of some of the sheer number of posts is time consuming, an you members keep posting valuble and effective advice to beginners like me.
A brilliant community :D

Thanks, Killkoy

Edit - oh and your Alternate CD Dapper Installs guides are excellent Herman :D

---

### Post by Herman on 2006-06-17
>  I assume i need to conect to the internet to use those commands?? Yes, I think so too. Does your internet connection not get automatically configured during the fifth step or so in the 'alternate' install when you install with the internet wires plugged in?
Did the Live CD run okay in your machine?
If not, maybe just wait a while and see if another solution comes up somewhere, maybe someone else will chime in here with an idea or you'll come across the solution some day when you are browsing the forums without even trying. 
Perhaps give the older version 'Breezy Badger a try if you haven't already done so, it's almost as good and very stable. I still have a good 'Breezy' install, (I'm typing from it now). I have found that sometimes an earlier or later version will work in a machine. My old 'Book PC' ran 'Hoary' fine but had trouble with the CD drive being recognised for a 'Warty' install. Then it was able to have 'Breezy' installed in it no problems. (Unfortunatetly it's down with power supply trouble so I can't use it for testing 'Dapper' installs).
>  A brilliant community Yes, Mr Shuttleworth and his team and the forum organisers and others as well are geniuses to come up with such a great support system for Ubuntu. It's fun to participate in, and benefits everyone. I hope your problem can be solved soon. All the best, Regards, Herman :D

---

### Post by RRS on 2006-06-17
> my graphics card is a 6800gs pcie

You probably need to install the correct driver. Till then try selecting VESA when you run the reconfigure process, it may provide an adequate default till you can get you internet going for the proper driver.

For editing from the terminal rather then gedit try nano.

Also;
```
cat /etc/X11/xorg.conf
```
This will provide a readout of your current X configuration file. If it's possible to post it here perhaps someone can spot a problem.

---

### Post by thesedateone on 2006-06-18
[QUOTE=killkoy]
and i cant conect to the internet because the only way that i know of setting up the network is using gedit which seems to need a gui to work.[/QUOTE]

I've had this problem too, and yes: gedit needs X to run.  You can however use vi to edit your files with instead.  It's a little harder to use but is a mainstay for Linux.  It's installed everywhere and always works once you learn how to use it.

---

### Post by killkoy on 2006-06-18
> **Herman] Does your internet connection not get automatically configured during the fifth step or so in the 'alternate' install when you install with the internet wires plugged in?[/QUOTE]
no it doesnt, im conected using a wireless network, and i dont have a long enough ethernet cable to temporerly conect my computer during install. However i seem to have a wireless card that is supported by ubuntu as the guide that i found on th wiki says that since ubuntu 5.10 the drive is insalled out of the box (is a rt2500 chipset card)
> Did the Live CD run okay in your machine?
only if i run it in safe graphics mode. If i run it using the first option the same thing happens.
[QUOTE]You probably need to install the correct driver. Till then try selecting VESA when you run the reconfigure process, it may provide an adequate default till you can get you internet going for the proper driver.

For editing from the terminal rather then gedit try nano.

Also said:**
> 
OK thanks i will give these i go later
[QUOTE]I've had this problem too, and yes: gedit needs X to run. You can however use vi to edit your files with instead. It's a little harder to use but is a mainstay for Linux. It's installed everywhere and always works once you learn how to use it.
should i use vi or nano, do they both work from the cammand line, which one is more beginner friendly:confused::D

Thanks, killkoy.

---

### Post by RRS on 2006-06-18
> should i use vi or nano, do they both work from the cammand line, which one is more beginner friendly

People who use it regularly seem to prefer Vi but I've found Nano more "beginner friendly".

Open a file with each one and compare for yourself. You can always just browse the interface without actually changing the file just to get a basic feel for each editor.

Another suggestion, before editing any of your system files; ```
sudo cp /etc/(name of file) /etc/(name of file).backup
```
This will make a backup copy of the file so you can revert back to the original settings easily. I've also done this after editing once I've got something to work properly to save time recovering from my future experiments/mistakes.

---

### Post by killkoy on 2006-06-18
> Till then try selecting VESA when you run the reconfigure process

I did this and it worked woot \\:D/ thanks

ok now im having trouble connecting to my wireless network:roll:
i have a an edimax card that used ralink rt2500 and have been trying to use this guide to set it up: [https://wiki.ubuntu.com/WifiDocs/Driver/RalinkRT2500?highlight=%28rt2500%29](https://wiki.ubuntu.com/WifiDocs/Driver/RalinkRT2500?highlight=%28rt2500%29)

it is a wpapsk encrypted network. I have tried changing the network so that it is just wep encrypted but that doesnt have any effect. 

When i type ```
sudo ifup ra0
``` after doing the process described in the guide i get lots(4/5/6) messages saying something like scanning port 67 for dhcpthing.
then a message saying no dhcp, or something like that.

Any help much appreciated

Thanks, killkoy

---

### Post by killkoy on 2006-06-18
ok, update. when i type sudo ifup ra0 this is what happens:
```
~$ sudo ifup ra0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ra0/00:0e:2e:57:55:95
Sending on   LPF/ra0/00:0e:2e:57:55:95
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
edit - should i create a new thread with a more relevent title to my current problem?

---

