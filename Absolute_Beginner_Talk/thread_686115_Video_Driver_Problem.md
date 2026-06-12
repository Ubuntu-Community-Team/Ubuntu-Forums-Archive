---
title: "Video Driver Problem"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Daawoow on 2008-02-02
Hello Fellow Forum dwellers

I'll start at the beginning (of my problem ) at the end of December I installed Linux on my computer.
Everything went off without a hitch, however when I tried to install the newest video card setting for my video card, the downloaded and I was prompted to restart, I did but when the Ubuntu loading screen appeared it went blank after that.
Well, I said whatever, reinstalled and just didn't install the most recent driver.

However today, I get the World of Warcraft bug, and wanted to see if I could figure out how to use wine with WoW.

Long story short, I got envy to install my drivers, computer restarts gets to loading screen and stops.

I try another fresh install, goes great. I attempt to install drivers again and no dice, same thing happens.

I have been through:
(Post the way you got the ATI driver to work)
[http://ubuntuforums.org/showthread.php?t=221320&highlight=x1300+driver](http://ubuntuforums.org/showthread.php?t=221320&highlight=x1300+driver)

and some others through recovery Disk.

Anyway machine specifics:
Video card is an ATI Radeon x1300

Computer is a:
 intel P4 2.8Ghz
1.5 gig Ram

I'm running Ubuntu 7.10

For those liek me my problem is:
After install of radeon Video driver for x1300 Ubuntu gets to loading screen  the orange bar completes then screen goes blank

Any tips will be tried and re-tried and greatly appreciated


Thanks,
~G

---

### Post by ajgoyt on 2008-02-02
Please post any error messages so we can help you - Does the screen / monitor keep refreshing etc etc

---

### Post by Daawoow on 2008-02-02
It refreshes once, no error messages appear. The monitor simply does black, and computer shows no sign of processing information (no hard-drive noise / light blinking).
The driver it **installed** is  xorg-driver-fglrx.

---

### Post by ajgoyt on 2008-02-02
Just a quick test would be to - put in the feisty live CD [SIZE="6"]***_and don't install anything_***[/SIZE],  just let it boot and run in live cd mode..... t :)

---

### Post by Daawoow on 2008-02-02
I can get it to boot after this happens with:
sudo dpkg-reconfigure -phigh xserver-xorg

Start it in recovery mode and just enter that.
So it isn't completely dead, but this is what leads me to believe that the driver is causing the issue.

I'm trying to figure out how, if I in fact can, update the drivers.

pardon my ignorance, I will do that, what exactly would I be looking for, just seeing if it starts?

Sorry, I'm rather noobish, thank you very much for you're help.

---

### Post by ajgoyt on 2008-02-02
Do you have the Live CD?

 Lets try a test.

will it boot off the Live Cd.......?

---

### Post by Daawoow on 2008-02-02
Starts up from the CD no problem.

---

### Post by ajgoyt on 2008-02-03
Now we no it's not hardware related!

 I am not a good enough geek to work you through  what appears to be a software/ driver issue. You have a couple of different choices.

1. Have someone else more capable of helping you undo / re install the video card drivers.

2. if it's been awhile since you have re formatted / started over ***_and you really don't have anything worth saving? _*** Then maybe you should just format and re -install.

Hope this Helps:)

AJ

---

### Post by Daawoow on 2008-02-03
Thanks for your Help AJ.

I had figured it was not a hardware issue because it would only mess up after I had installed the drivers.

Also, I had just reformatted my hard-drive and re drew partitions about 5 hours ago.

I have found a few more tutorials like
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually)

Thanks again for your help.
~G

---

### Post by draze on 2008-02-03
i had the smae and i fixed it
 try tuping cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

---

### Post by draze on 2008-02-03
wait...this is gonna get u back to the initial screen and video settings you had. you should have no black screen after you do that.

the video card....i have the same problem..i have Radeon X1600...i am trying to solve it now.

---

### Post by Daawoow on 2008-02-03
Thanks for your Help AJ.

I had figured it was not a hardware issue because it would only mess up after I had installed the drivers.

Also, I had just reformatted my hard-drive and re drew partitions about 5 hours ago.

I have found a few more tutorials like
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually)

Thanks again for your help.
~G

---

### Post by Daawoow on 2008-02-03
Yeah, that is to just fix it so it starts up.

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually)

This seems to be helpful, at least the "Method 2: Install the Catalyst 8.1 Driver Manually"
However once I get to the configuration it screws up the driver again, so I don't know, let me know if you get something!
Thanks
~G

---

### Post by Daawoow on 2008-02-03
~~Bump~~

I'm really confused here, if somebody who knows what is going on could give me a hand that would be great =D

Thanks, 
~G

---

### Post by deoki on 2008-02-05
I'm having the same problem.
Please, some one help out the guys like us with ATI X1300?

I have my Ubuntu locked (screen goes blank after drivers update to enable effects) since December and no one has found a solution to the updates of ATI drivers for X1300 cards, both mobile and desktop versions.

In my case, I've tried everything that was said in this thread, but no success.

Why does this happens? It's not a hardware problem, but I'm sure its some kind of bug, and it has been submitted many time to the Ubuntu bug section.

:confused:

---

### Post by deoki on 2008-02-09
Help, please! :(

Anyone?

---

### Post by deoki on 2008-02-21
Why wont someone help us out???

Not even a single person?!?

---

