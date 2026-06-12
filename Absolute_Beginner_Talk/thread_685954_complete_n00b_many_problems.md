---
title: "complete n00b many problems"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by sirfonners on 2008-02-02
I just bought a new Acer Extensa 5420 from Bestbuy today for college, it was cheap and decent specs so I picked it up. I had done a little research and already had decided to put Ubuntu on as soon as I took it out of the box because Vista sucks. I installed everything ok but I am having a few problems.

I guess I kinda need a crash course here are some of the problems I am having right now, and I have not ide what I am doing or what to do.

First my wireless isnt working, I have googled over and over and havent found something that helped, or i guess that I understood. It works directly plugged into my router but no wireless. I have no idea whats wrong, the option doesnt even come up to go to wireless when using the live disk.

Seconds my firefox is weird, I went to go to stickam to see if my webcam was working, but I needed to install flash player and stuff but it wouldnt let me, I found the fix going through the problems by going to software sources and ticking everything in the main page. It installed everything, but stickam.com still looks weird, and the whole go live thing doesnt even work when it pops up wtf??

thats pretty much the only thing I am worried about right now,

I dont really know how to use linux, So far I love it more than vista as it runs faster and is just kinda cool. IF anyone can give me a n00b step by step help...or point me in the right direction pleeeaase do x[


thanks, jon

---

### Post by randy78 on 2008-02-02
Check this guide out!

Great resource put together by the folks of the community ;)

[https://wiki.ubuntu.com/Training?action=AttachFile&do=get&target=student.pdf]("https://wiki.ubuntu.com/Training?action=AttachFile&do=get&target=student.pdf")

---

### Post by ugm6hr on 2008-02-02
Can't help with the webcam - I don't have one.

But for wifi - post the output from these commands:

```
lspci
lshw -C network
```

---

### Post by sirfonners on 2008-02-02
> **ugm6hr said:**
> Can't help with the webcam - I don't have one.

But for wifi - post the output from these commands:

```
lspci
lshw -C network
```

i did this, it still doesnt give me the option to use wireless
is any the info it gave me give any details of what might be wrong?

---

### Post by kellemes on 2008-02-02
> **sirfonners said:**
> i did this, it still doesnt give me the option to use wireless
is any the info it gave me give any details of what might be wrong?


Can you post the output please?

---

### Post by ugm6hr on 2008-02-02
> **sirfonners said:**
> i did this, it still doesnt give me the option to use wireless
is any the info it gave me give any details of what might be wrong?

We need to see the output!  Can't help solve the problem without the correct info.

---

### Post by spiderbatdad on 2008-02-02
Hi and welcome. Just remember the first time you ever turned on windows...you probably didn't know how to do anything. In no time at all, you'll find you have far more control over your computer and far more configurability than you ever had with windows.

Wireless can be a pain if you can't  manually configure it. If you could open your terminal via Applications>>Accessories>>Terminal and enter ```
sudo lshw -C net
``` then your password, and copy/post the result here...the forum can help you get your wireless working. In the terminal window just hold the mouse button and drag it over the entire text output. Once it is all highlighted, right click and select copy. Come back here to post a reply and choose the "#" symbol for code tags. Then right click and select paste.

---

### Post by sirfonners on 2008-02-02
this is everything i got
sorry for bein such a noob lol

> 00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 15)
05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
0b:06.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
0b:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0b:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
0b:06.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
fonners@fonners-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1d:72:14:7a:07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=75.30.68.216 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0


---

### Post by ugm6hr on 2008-02-02
The important bits:
```
product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
```

Have you tried System-> Administration-> Restricted Driver Manager?
This *might* be all that is required - just make sure that the Atheros Wifi driver is enabled.

But I think this chipset is one of the newer Atheros ones.  According to madwifi - it is supported with the newest madwifi driver.  If the Restricted Driver doesn't work - you might have to use the latest version from madwifi.

Before you try that - make sure you have updated Ubuntu, then try the restricted drivers again.

Links:
[http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5006EG](http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5006EG)
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

---

### Post by spiderbatdad on 2008-02-02
It looks like all that needs to happen is to try to manually configure the network using the Network Monitor applet in the notification area at the upper right of you screen.  Left click to see if your wireless network is listed. Right click to manually configure. You may have to choose roaming mode. If you wireless network is secured, the will be other issue to deal with.  Check out the networking forum stickies, too. You may have to do some reading to get your wireless working.

---

### Post by sirfonners on 2008-02-02
ohh geeez, i still have no idea whats wrong
I went to restricted driver drivers
and then clicked enabled for (HAL) like you guys said
but under status it says "not in use"



oooh many I hate this right now I dont know how to do anythiiiing:confused:
I dont even understand what to do with those likes posted
like how to use the info lol

goood

---

### Post by spiderbatdad on 2008-02-02
I believe you will have to reboot after enabling a driver.

---

### Post by sirfonners on 2008-02-02
> **spiderbatdad said:**
> I believe you will have to reboot after enabling a driver.

I have, but still not wirelesses shows
and it still says not in use

---

### Post by spiderbatdad on 2008-02-02
ok have you tried to manually configure the wireless by left clicking on the nm applet and selecting "manually configure?"

---

### Post by sirfonners on 2008-02-02
> **spiderbatdad said:**
> ok have you tried to manually configure the wireless by left clicking on the nm applet and selecting "manually configure?"

it only shows:

wired connection
and
modem connection

in the manual configuration

---

### Post by spiderbatdad on 2008-02-02
in your terminal try ```
sudo iwconfig
```

---

### Post by spiderbatdad on 2008-02-02
and if you right click on the nm applet, do you have the option to enable wireless?

---

### Post by sirfonners on 2008-02-02
```
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.
```


and no the option isnt available

---

### Post by spiderbatdad on 2008-02-02
you should have eth1 or wifi0...this is most likely an issue with the driver...I think. Have you looked into installing madwifi-tools from synaptic?

---

### Post by sirfonners on 2008-02-02
> **spiderbatdad said:**
> you should have eth1 or wifi0...this is most likely an issue with the driver...I think. Have you looked into installing madwifi-tools from synaptic?

i have noooooooooooooo idea how:(
i have been trying to figure out 
but havent been able to :(

---

### Post by ubuntu-freak on 2008-02-02
Can't help with wireless, but use my [how-to](http://ubuntuforums.org/showthread.php?t=661833) to get multimedia working and such.
 
Nathan

---

### Post by spiderbatdad on 2008-02-02
get madwifi herehttp://madwifi.org/
hopefully you know how to install a tar?
Download the package to your Desktop. Right click on it and select "extract here" Then click on that floder and read the Install and Readme files.

---

### Post by sirfonners on 2008-02-02
> **spiderbatdad said:**
> get madwifi herehttp://madwifi.org/
hopefully you know how to install a tar?
Download the package to your Desktop. Right click on it and select "extract here" Then click on that floder and read the Install and Readme files.

haha no dont know how to
i assume that reading those files will help?

---

### Post by spiderbatdad on 2008-02-02
yes reading will help. Generally you open the terminal and change into the directory where the package or file is...so if it is located on your desktop you enter in the terminal```
cd Desktop
``` notice desktop has a capital "D" Linux commands and paths are case sensitive. Now your command prompt has changed slightly to indicate your present working directory (pwd) Next, as you have already extracted  the package you can cd again into that folder just type```
cd ma  and hit the tab key
```the tab key should auto complete the file name for you. This would have worked for cd Desktop as well. Though in Gutsy, due to the Documents directory,  I have to type cd De (and tabkey)

Now that your pwd is madwifi(whatever)$ you can run the necessary commands for install the package, ie ```
./configure
make
sudo make install
``` In most cases you will need to have previously installed the package build-essential from synaptic, in order to have the tools necessary to compile a package...everything should be fairly automatic after that.  Deb packages are much easier to install...point and click.

---

### Post by sirfonners on 2008-02-02
> **spiderbatdad said:**
> yes reading will help. Generally you open the terminal and change into the directory where the package or file is...so if it is located on your desktop you enter in the terminal```
cd Desktop
``` notice desktop has a capital "D" Linux commands and paths are case sensitive. Now your command prompt has changed slightly to indicate your present working directory (pwd) Next, as you have already extracted  the package you can cd again into that folder just type```
cd ma  and hit the tab key
```the tab key should auto complete the file name for you. This would have worked for cd Desktop as well. Though in Gutsy, due to the Documents directory,  I have to type cd De (and tabkey)

Now that your pwd is madwifi(whatever)$ you can run the necessary commands for install the package, ie ```
./configure
make
sudo make install
``` In most cases you will need to have previously installed the package buil-essential from synaptic, in order to have the tools necessary to compile a package...everything should be fairly automatic after that.  Deb packages are much easier to install...point and click.

oh ok, that makes things easier, uhhm what is the synaptic thing you're talkign about.



thanks for all the help though, i am so glad the forums are here:)

---

### Post by spiderbatdad on 2008-02-02
ok synaptic package manager is your first choice for software resources. You should be able to find it under System>>Administration>>Synaptic Package Manager. The search filter at the top is very helpful for locating packages...as there are many. Just click the search icon and enter build and it will considerably narrow the list for to find build-essential, or you could enter build-essential.

---

### Post by sirfonners on 2008-02-02
still nothing :(

---

### Post by spiderbatdad on 2008-02-02
with all you've learned now about where to find packages and how to install them, perhaps it's time to post a question as to how to use madwifi to get your wireless working...of course read any appropriate threads that the post offers you.

---

### Post by sirfonners on 2008-02-02
> **spiderbatdad said:**
> with all you've learned now about where to find packages and how to install them, perhaps it's time to post a question as to how to use madwifi to get your wireless working...of course read any appropriate threads that the post offers you.

AWESOME I finally got it working using ndiswrapper!!
so now it shows that there is a wirless option
and for a second it showed wireless networks availabe
but now there doesn show any networks available (not even ones nearby liek before)
after i restarted it, is there a certain setting my router or my wireless settings have to be on?


Alssoooo does anybody have an idea on how I get my integrated cam and mic working? do I use the ndiswrapper the same way??

---

### Post by bigpalmtree on 2008-02-13
[SIZE="5"]I HAVE YOUR ANSWER!!!
GO HERE TO GET ALL THE DRIVERS FOR XP since I HATE VISTA.
I HAD A HEADACHE FINDING THIS WEBSITE BUT WAS ABLE TO GET THE DRIVERS I NEEDED.
[/SIZE]
[SIZE="5"][COLOR="DarkGreen"]Steps for install: I HIGHLY RECOMMEND Mozilla Firefox for browsing and downloading from this FTP website!  IE sux royally for FTP browsing and Firefox is faster and gives you the basic "save to" option insted of click and drag which is Ghetto slow as Hell!

**[COLOR="DarkOrange"]http://support.acer-euro.com/drivers/ftp/ftp.html[/COLOR]**

1) Goto Notebook folder
2)Scroll down and look for Extensa 5420
3)Select the "Driver" folder, NOT Vista, then Driver because then you'll have Vista drivers in there.
4)DOWNLOAD GETRIGHT to download files, sometimes the ftp server gets a little funky and i had trouble downloading the SUPER Fing propreitary ATI VGA drivers for it.  Download kept canceling on it's own.  Getright get's it downloaded one way or another without any problems!
5)In the driver folder you will find multiple drivers, some of two kinds.  BEST TO DO IF ONE VERSION DOESNT WORK TRY ANOTHER.  DEPENDING ON WHERE AND WHEN YOUR SYSTEM WAS BUILT WILL DETERMIN THAT.  IE: there are two webcam drivers, two Wireless internet drivers.. etc.. it won't hurt to try one then it not work, just try the other and it will!
6) IGNORE THE 56k MODEM DRIVERS FROM THERE
goto [www.acersupport.com](www.acersupport.com)  , and find the Extensa 5420G under support & drivers.
Look for Foxxcom if the other two drivers from the FTP site DO NOT WORK, this one will EVEN THOUGH IT SAYS "Vista" it will work in XP just fine.
7)IF YOU NEED FURTHER HELP EMAIL ME @
[email]bigpalmtree@gmail.com[/email] OR [email]kdelcol@neo.rr.com[/email]  (preferably Roadrunner because i get way too much spam on gmail and do not know if yours will turn up in the wrong folder!

Thanx, AND I WILL TRY TO HELP YOU THE BEST I CAN DO NOT SPAM MY EMAIL, SEND ME ONE MESSAGE WITH ALL YOUR QUESTIONS, I WILL HELP YOU THE BEST I CAN.

thanx again!
Big Palmtree[/COLOR][/SIZE]

---

### Post by gnicko on 2008-02-18
> **sirfonners said:**
> AWESOME I finally got it working using ndiswrapper!!
so now it shows that there is a wirless option
and for a second it showed wireless networks availabe
but now there doesn show any networks available (not even ones nearby liek before)
after i restarted it, is there a certain setting my router or my wireless settings have to be on?


Alssoooo does anybody have an idea on how I get my integrated cam and mic working? do I use the ndiswrapper the same way??
Just a thought.....

This might sound kind of strange, but are you sure thast the cam and mic aren't working? I've got the same computer and was thinking that the cam and mic weren't working, but then I installed Zapping TV viewer and suddenly, using this program, I was able to use the cam and microphone...not with any other programs, but works with that one.

---

