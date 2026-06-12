---
title: "installing hardware &amp; there drivers, beginner?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by BillB on 2008-02-07
I finally got Ubuntu 7.10 installed and stable on my Dell CPX laptop.
But I have *no *idea how to install hardware (wifi adapter, digital camera, etc.) and it's driver?
Do Windows drivers from CD's work?
Are there hardware drivers that are part of the Ubuntu OS download?
I really don't know?

I'm used to Windows finding new hardware, and walking you through it's instillation.
I have NO idea where to start w/ Ubuntu?   I messed around w/ Ubuntu for a few hours, but didn't find where you go to install new hardware?  What is the process?

---

### Post by stchman on 2008-02-07
> **BillB said:**
> I finally got Ubuntu 7.10 installed and stable on my Dell CPX laptop.
But I have *no *idea how to install hardware (wifi adapter, digital camera, etc.) and it's driver?
Do Windows drivers from CD's work?
Are there hardware drivers that are part of the Ubuntu OS download?
I really don't know?

I'm used to Windows finding new hardware, and walking you through it's instillation.
I have NO idea where to start w/ Ubuntu?   I messed around w/ Ubuntu for a few hours, but didn't find where you go to install new hardware?  What is the process?

Hardware drivers are in the Linux kernel.  If your hardware does not work then you are going to need drivers that modify the kernel.

What hardware do you have on your laptop that doe not work?

---

### Post by emarkd on 2008-02-07
Ubuntu should detect your hardware and install it without any input from you.  However, some hardware requires restricted drivers and you have to enable them from System > Administration > Restricted Drivers Manager.

Unfortunately, some hardware is quite tricky to set up.  If you have a specific piece of hardware that's giving you problems, post about it here and someone will try to help.

---

### Post by BillB on 2008-02-07
First, I am trying to install a 2WIRE 'g' wifi adapter.   *Nothing* happened when I plugged it in, or after I re-booted.
Restricted Drivers Manager says something like I don't need or have any.  I was playing around with that last night (for hours).

---

### Post by emarkd on 2008-02-07
Is that a USB device?  You can check what Linux thinks it is by running:

```
lsusb
```

That may give you a direction.

---

### Post by BillB on 2008-02-07
> **emarkd said:**
> Is that a USB device?  You can check what Linux thinks it is by running:

```
lsusb
```

That may give you a direction.

No, it is a PCMIA card.  What do I do?

---

### Post by BillB on 2008-02-07
I'm at a loss here....I *haven't even seen*, whatever it is that's supose to come up when your adding hardware?
The Restrictive Drivers Manager say that I don't have any hardware that needs restrictive drivers.

I get *nothing* after inserting my adapter card.  No blinking lights, no window, nothing!


By the way, this wifi adapter worked great in this laptop w/ Win 98 SE .

---

### Post by emarkd on 2008-02-07
The only PCMCIA card I own is a Sound Blaster Audigy2, but Ubuntu just detects it when I plug it in.  I don't have to do anything, but there is no visible notification that anything's been detected or changed.  Mine shows up on the PCI bus.  If yours is the same, you can check it out by running:

```
lspci
```

with your card plugged in.  If you don't see anything there that looks like your card, try:

```
lshw -short
```

If you still don't see anything, you can run that without the -short, but it'll output a lot of information.

---

### Post by BillB on 2008-02-07
OK, how do you "run" these things?  Where?

---

### Post by emarkd on 2008-02-07
Sorry, click on Applications > Accessories > Terminal and input the commands there.  We're trying to see if Ubuntu even notices that you've got something plugged in, plus we'll know exactly what hardware you have so you've got something specific to search for.

---

### Post by Rome.konig on 2008-02-07
maybe your Wifii card already is installed and works, but you just dont have it set up right, if you can use ethernet..go to applications>administration>synaptic
package maneger, and look for wireless assistant. or any other wireless progs they have that can help you out. Or with a different computer access your router... you may have to change your WPA or WEP settings on your router to get your laptop online. If you have a linksys check your IP clients pool and see if your laptops MAC adress shows up. If it does then that means its just a matter of configuration.

---

### Post by BillB on 2008-02-07
"input the commands"?   At that terminal it has the name of my laptop there ....how do I "input" commands?  I typed them in, but what do I to "input" them?  I tried a couple things, but nothing worked?

I also found an old 3Com Cellular Modem PCMIA card (that worked great w/ this laptop)....nothing w/ Ubuntu.

---

### Post by emarkd on 2008-02-07
You input the commands by typing them (or cut-n-paste) and hit enter.

---

### Post by BillB on 2008-02-07
> **Rome.konig said:**
> maybe your Wifii card already is installed and works, but you just dont have it set up right, if you can use ethernet..go to applications>administration>synaptic
package maneger, and look for wireless assistant. or any other wireless progs they have that can help you out. Or with a different computer access your router... you may have to change your WPA or WEP settings on your router to get your laptop online. If you have a linksys check your IP clients pool and see if your laptops MAC adress shows up. If it does then that means its just a matter of configuration.

Do you mean 'system'> administration> synaptic on Ubuntu?  Under 'communication' I have wvdial, a ppp dialer.

---

### Post by BillB on 2008-02-07
> **emarkd said:**
> You input the commands by typing them (or cut-n-paste) and hit enter.

I get "command not found".
I am typing them after my computers name and :~$, that is there when I open the window.

---

### Post by emarkd on 2008-02-07
Check to make sure you're getting them right.  Linux is case-sensitive and every command I've given you is all lower-case.  If in doubt, cut-n-paste them directly from your browser using the right-click mouse menu.

---

### Post by BillB on 2008-02-07
> **emarkd said:**
> Check to make sure you're getting them right.  Linux is case-sensitive and every command I've given you is all lower-case.  If in doubt, cut-n-paste them directly from your browser using the right-click mouse menu.

Is that "1" as in 1,2,3.... spci?  All after my computers name bill-laptop:~$....which I can not delete in that window.

I can not cut-n-paste, because I don't have a connection to the internet w/ that laptop!
I'm trying to get a connection w/ the wifi card in question.

---

### Post by Miller12 on 2008-02-07
It is a lower case L as in laughter.

---

### Post by Miller12 on 2008-02-07
It's going to come back with a bunch of information like this:
```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
[COLOR="Red"]00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/COLOR]
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```
You are going to be looking for the name of your wifi card where I have shown red.

---

### Post by BillB on 2008-02-07
> **Miller12 said:**
> It's going to come back with a bunch of information like this:
```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
[COLOR="Red"]00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/COLOR]
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```
You are going to be looking for the name of your wifi card where I have shown red.


All I see are the internal components of the laptop....w/ either code.
No wonder they do* nothing* in my Ubuntu laptop....ZERO.
(the 3COM modem was a VERY popular card....Ubuntu doesn't even see it)

And knowone can tell me which PCMIA wifi adapterd DO work w/ Ubuntu (in other threads)...they all talk about USB!
I can't believe that there is no PCMIA wifi adapter that will work w/ Ubuntu....but I guess there isn't one.

Ubuntu is a big headache, that can't even connect to the internet with a laptop.  Which should be a* simple *thing.

---

### Post by emarkd on 2008-02-07
Can you post the output of 'lspci' so we can all have a look?  And do be too hasty about blaming Ubuntu for this problem.  If a hardware manufacturer isn't interested in supporting their product for Linux users, there's very little the community can do about it.

---

### Post by BillB on 2008-02-07
> **emarkd said:**
> Can you post the output of 'lspci' so we can all have a look?  And do be too hasty about blaming Ubuntu for this problem.  If a hardware manufacturer isn't interested in supporting their product for Linux users, there's very little the community can do about it.

NO....I can NOT connect to the internet, so I can NOT post the lspci sheet.   Believe me, there are no PCMIA connections, and it isn't my hardware.

I don't care who's to blame....(like I said, the 3COM card was VERY poppular)

And KNOWONE can tell me which PCMIA wifi adapter will work w/ Ubuntu 7.10
That makes Ubuntu worthless on laptops which need adapter cards!   Unless you never want to connect to the internet.

---

### Post by emarkd on 2008-02-07
I got that you can't connect to the internet.  I'm following this post and have been very involved in trying to help you.  I'm sorry it's not working out.  You could run the command, copy the output to a file, transfer it to whatever you're using to connect and upload it from there, but it's OK if you don't want to.

Popularity has nothing to do with friendliness to FOSS software.  After all, Windows is very popular...

I'm sorry you're getting angry and frustrated.  We're only trying to help....

---

### Post by emarkd on 2008-02-07
Here's a link to some hardware compatibility information.  Maybe you can find something there.

[http://hardware4linux.info/](http://hardware4linux.info/)

---

### Post by BillB on 2008-02-07
I only have 11 things in lspci.

Intel host bridge
Intel PCI
2- TI card bus
2- Intel bridge
Intel IDE
Intel USB
ESS audio
ATI VGA
Intersol Network Controler

Does Ubuntu even see *any* PCMIA...ever?

---

### Post by chick penguin on 2008-02-07
more info if you want to check
[https://wiki.ubuntu.com/HardwareSupportMachinesBar%20ebones](https://wiki.ubuntu.com/HardwareSupportMachinesBar%20ebones)

---

### Post by BillB on 2008-02-07
Hold on!  I once read that 2WIRE was actually an Intersil Corporation card.

I DO have an Intersol Network Controler (Prisim Javelin) in my lspic list!

How do I get it to work?
I had bug#133823 writen down from when I was looking into loading Ubuntu.
Can this be made to work?

---

### Post by BillB on 2008-02-07
I re-searched "2WIRE 802.11g PCMIA not detected" and I think they have my fix?

But I don't really understand how to execute it?   Could someone *please* look at that post, and tell me (in beginners language) where I need to put the 'prism 54 common & pci' they talk of?

I'm excited now!

---

### Post by cwbar_1 on 2008-02-07
Hi Billb,  Hang on and I'll try to help.  First, since lspci recognizes your card, you're almost home free!  Since you are well versed in Windows, find the driver disc for your card.  Then follow these directions.  

1. Copy your_driver.inf & your_driver.sys to  /home/your_directory/  directory.
(you can drag and drop, just open Places>Home Folder and the file browser that opens when you insert your card's disc)  *****MAKE SURE YOU ARE USING XP OR LOWER DRIVER,,,,,,,,,,VISTA DRIVERS WILL NOT WORK**********

2. Install w/ndiswrapper.  (open a terminal and type ndiswrapper...if it is installed then copy and paste the following [starting with sudo] ONE LINE AT A TIME)  If the terminal reports that you do not have it installed,  open synaptic package manager  System>Administration>Synaptic Package Manager,,,, ignore any warnings about out of date etc... Insert the Ubuntu installation disc.  Synaptic will recognize the disc as a repository.. Click on search, type in ndiswrapper and install ndiswrapper_common and  
ndiswrapper-utils.  Then copy and paste the following one line at a time.
	
        sudo ndiswrapper -i /home/your_directory/your_driver.inf
	ndiswrapper -l
	sudo depmod -a
	sudo modprobe ndiswrapper
	sudo cp /etc/network/interfaces /etc/network/interfaces.orig
	echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
	sudo ndiswrapper -m
	echo 'ndiswrapper' | sudo tee -a /etc/modules
	echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

Then ,,,System>Administration>Network,,,, your wireless should show up.  Click on your wireless and set it up using your network name.

There are several things at this point that COULD be obstacles.  But this will probably get you going.   

I hope this helps.  You are in for one nice ride once all is set up!!!!!!!!



If the addition modules you just spoke of NEED to be loaded,  check for their installation by typing in modprobe -l   (that is -lower-case L)

---

### Post by BillB on 2008-02-08
> **cwbar_1 said:**
> Hi Billb,  Hang on and I'll try to help.  First, since lspci recognizes your card, you're almost home free!  Since you are well versed in Windows, find the driver disc for your card.  Then follow these directions.  

1. Copy your_driver.inf & your_driver.sys to  /home/your_directory/  directory.
(you can drag and drop, just open Places>Home Folder and the file browser that opens when you insert your card's disc)  *****MAKE SURE YOU ARE USING XP OR LOWER DRIVER,,,,,,,,,,VISTA DRIVERS WILL NOT WORK**********

2. Install w/ndiswrapper.  (open a terminal and type ndiswrapper...if it is installed then copy and paste the following [starting with sudo] ONE LINE AT A TIME)  If the terminal reports that you do not have it installed,  open synaptic package manager  System>Administration>Synaptic Package Manager,,,, ignore any warnings about out of date etc... Insert the Ubuntu installation disc.  Synaptic will recognize the disc as a repository.. Click on search, type in ndiswrapper and install ndiswrapper_common and  
ndiswrapper-utils.  Then copy and paste the following one line at a time.
	
        sudo ndiswrapper -i /home/your_directory/your_driver.inf
	ndiswrapper -l
	sudo depmod -


	sudo modprobe ndiswrapper
	sudo cp /etc/network/interfaces /etc/network/interfaces.orig
	echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
	sudo ndiswrapper -m
	echo 'ndiswrapper' | sudo tee -a /etc/modules
	echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

Then ,,,System>Administration>Network,,,, your wireless should show up.  Click on your wireless and set it up using your network name.

There are several things at this point that COULD be obstacles.  But this will probably get you going.   

I hope this helps.  You are in for one nice ride once all is set up!!!!!!!!



If the addition modules you just spoke of NEED to be loaded,  check for their installation by typing in modprobe -l   (that is -lower-case L)


Driver disk?

2WIRE does not come w/ any disks/CD....they don't have any, they only have a 'download' drivers.

?

---

### Post by cwbar_1 on 2008-02-08
BillB,
Two ways to go as I see it.
1. If you dual booted with XP & Ubuntu;  In th XP side of your system, look for the TWWGPC_Temp directory in c:\.  Copy the 2 files,,,,WlanUIG.inf & WlanUIG.sys to a USB or floppy.  Then use these two files to follow the previous instructions.   

2. IF you are not dual booting,  and if you have access to an XP machine, go to the 2 wire site and download the driver package.  When the package has been downloaded, double click on the .exe file to unzip it. (don't worry, you are not installing the file on the host computer, you are just unzipping the file and creating a temporary directoy.) Open the TWWGPC_Temp directory and copy the files.  Then follow the directions.  I know all of this seems overwhelming, but hang in there.  Ubuntu is worth it.   (BTW, you probably have 3 ore 4 months of getting un-used to windows,,,,probably a shorter time than it took you to be comfortable in windows!)   Good Luck.

---

### Post by BillB on 2008-02-08
No, I can not dual boot.

Is #2 simple instructions on how to burn a driver CD, that would *also *work w/ XP?
Come to think of it, I think my sister can burn CD's

---

### Post by cwbar_1 on 2008-02-08
Number 2 is not instructions on burning an XP driver's disc. It is simply instructions for borrowing another computer with an internet connection to get the files you need.  If yo want an XP driver's disc, the just download the driver "zip" file, unzip it, read the "Read Me" file, and copy the contents of the directory just created to a CD.  If you want to use the drivers for Ubuntu, just follow the directions stated in my last post. (#2) If there is any confusion about the previous, you only need 2 files (.inf & .sys) in order to use Ndiswrapper for your Ubuntu installation.  Can you download files using the computer you are posting on the forum with?

---

### Post by BillB on 2008-02-08
> **cwbar_1 said:**
> Number 2 is not instructions on burning an XP driver's disc. It is simply instructions for borrowing another computer with an internet connection to get the files you need.  If yo want an XP driver's disc, the just download the driver "zip" file, unzip it, read the "Read Me" file, and copy the contents of the directory just created to a CD.  If you want to use the drivers for Ubuntu, just follow the directions stated in my last post. (#2) If there is any confusion about the previous, you only need 2 files (.inf & .sys) in order to use Ndiswrapper for your Ubuntu installation.  Can you download files using the computer you are posting on the forum with?

In #2 you say "copy" the files....copy to what?  This (old) PC can only copy to floppy (or HD).
My sister is a software engineer (of 30yrs) and has a CD burner I can use tonight.

What a (real) headache I'm getting from this!

---

### Post by BillB on 2008-02-08
> **cwbar_1 said:**
> BillB,
Two ways to go as I see it.
1. If you dual booted with XP & Ubuntu;  In th XP side of your system, look for the TWWGPC_Temp directory in c:\.  Copy the 2 files,,,,WlanUIG.inf & WlanUIG.sys to a USB or floppy.  Then use these two files to follow the previous instructions.   

2. IF you are not dual booting,  and if you have access to an XP machine, go to the 2 wire site and download the driver package.  When the package has been downloaded, double click on the .exe file to unzip it. (don't worry, you are not installing the file on the host computer, you are just unzipping the file and creating a temporary directoy.) Open the TWWGPC_Temp directory and copy the files.  Then follow the directions.  I know all of this seems overwhelming, but hang in there.  Ubuntu is worth it.   (BTW, you probably have 3 ore 4 months of getting un-used to windows,,,,probably a shorter time than it took you to be comfortable in windows!)   Good Luck.

OK, I used option 2 and had a CD made....I put it in my Ubuntu laptop and it comes up w/ a LINUX icon and the cdrom0 - File Browser window....there are 14 different files.
What next?

What is a w/ndiswrapper?
What/where is a terminal?

---

### Post by BillB on 2008-02-08
> **BillB said:**
> OK, I used option 2 and had a CD made....I put it in my Ubuntu laptop and it comes up w/ a LINUX icon and the cdrom0 - File Browser window....there are 14 different files.
What next?

What is a w/ndiswrapper?
What/where is a terminal?

OK, I found the terminal (again)....and the Synaptic Package Manager.  Inserted the Ubuntu installation disk and clicked on search and typed in ndiswrapper........NOW WHAT?  There is NO button to get it to search?

"install ndiswrapper-common"....HOW?

---

### Post by BillB on 2008-02-08
> **cwbar_1 said:**
> Hi Billb,  Hang on and I'll try to help.  First, since lspci recognizes your card, you're almost home free!  Since you are well versed in Windows, find the driver disc for your card.  Then follow these directions.  

1. Copy your_driver.inf & your_driver.sys to  /home/your_directory/  directory.
(you can drag and drop, just open Places>Home Folder and the file browser that opens when you insert your card's disc)  *****MAKE SURE YOU ARE USING XP OR LOWER DRIVER,,,,,,,,,,VISTA DRIVERS WILL NOT WORK**********

2. Install w/ndiswrapper.  (open a terminal and type ndiswrapper...if it is installed then copy and paste the following [starting with sudo] ONE LINE AT A TIME)  If the terminal reports that you do not have it installed,  open synaptic package manager  System>Administration>Synaptic Package Manager,,,, ignore any warnings about out of date etc... Insert the Ubuntu installation disc.  Synaptic will recognize the disc as a repository.. Click on search, type in ndiswrapper and install ndiswrapper_common and  
ndiswrapper-utils.  Then copy and paste the following one line at a time.
	
        sudo ndiswrapper -i /home/your_directory/your_driver.inf
	ndiswrapper -l
	sudo depmod -a
	sudo modprobe ndiswrapper
	sudo cp /etc/network/interfaces /etc/network/interfaces.orig
	echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
	sudo ndiswrapper -m
	echo 'ndiswrapper' | sudo tee -a /etc/modules
	echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

Then ,,,System>Administration>Network,,,, your wireless should show up.  Click on your wireless and set it up using your network name.

There are several things at this point that COULD be obstacles.  But this will probably get you going.   

I hope this helps.  You are in for one nice ride once all is set up!!!!!!!!



If the addition modules you just spoke of NEED to be loaded,  check for their installation by typing in modprobe -l   (that is -lower-case L)


OK, with some help on another post I got the ndiswrapper's installed.

When you say "Then copy and paste the following one line at a time"....where do you paste them?  It's not clear?

I can't copy & paste, but will be typing them one at a time....I just need to know where?  In the same space the ndiswrappers were?  Are those spaces before the - & /?

---

### Post by mygor on 2008-02-09
Hi Bill Its me Bill from Ohio.

I believe you need to open the terminal to execute those commands. Have a little patience do not get discouraged. It will take a little time to get used to. Try to type the commands exactly as they are written. I hope this will help!

---

### Post by mygor on 2008-02-09
Hey Bill!

I don't know if you have found this or not. Its worth a try. Go to [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Scroll down to section 2 this is a step by step how to on wireless. Keep in mind that when you have to enter commands you will have to open a terminal window.

Bill

---

### Post by BillB on 2008-02-09
Hi Bill,

Thanks....as I have never heard of a 'terminal' before (Ubuntu), or what it does.  I'll give it a try, as I don't really know how to cut from one computer w/ an internet connection, and paste to another w/o a connection as instructed.
How are the animals today?

Bill
p.s.  But to think that every piece of hardware that I try to ad to a Linux machine (printer, camera, etc.) will be as difficult as the wifi adapter is discouraging.

---

### Post by halitech on 2008-02-09
Hi BillB

I know how discouraging it can be when trying to learn a new OS, I switched myself about 2 years ago and I still get frustrated at times because I tend to revert back to my windows way of thinking. I have only ever had trouble with 1 piece of hardware (no, I don't have wireless on my desktop so didn't have that headache) and that was with a webcam. Everything else I've tossed at Ubuntu, it has just seen and installed it and away I went. Wireless seems to be the achilles heal of linux so far (but don't blame Linux, its the companies that don't feel they need to support us to blame) but things are getting better and easier as time goes by.

Hang with it and I'm sure you will find the results very rewarding :)

---

### Post by BillB on 2008-02-09
> **cwbar_1 said:**
> BillB,
Two ways to go as I see it.
1. If you dual booted with XP & Ubuntu;  In th XP side of your system, look for the TWWGPC_Temp directory in c:\.  Copy the 2 files,,,,WlanUIG.inf & WlanUIG.sys to a USB or floppy.  Then use these two files to follow the previous instructions.   

2. IF you are not dual booting,  and if you have access to an XP machine, go to the 2 wire site and download the driver package.  When the package has been downloaded, double click on the .exe file to unzip it. (don't worry, you are not installing the file on the host computer, you are just unzipping the file and creating a temporary directoy.) Open the TWWGPC_Temp directory and copy the files.  Then follow the directions.  I know all of this seems overwhelming, but hang in there.  Ubuntu is worth it.   (BTW, you probably have 3 ore 4 months of getting un-used to windows,,,,probably a shorter time than it took you to be comfortable in windows!)   Good Luck.

I seem to get the same results as step #2 by downloading the XP driver, then right clicking it and choosing 'Extract Here' which gives you the TWWWGPC_Temp directory files.  Am I missing something?
I did both ways.

---

### Post by BillB on 2008-02-09
Well I struggled through this WHOLE proceduer....borrowed PC's, asked (several) software engineers I know (w/ 30yrs+ experience each), had people make me Cd's, I even had to borrow a keypad as the 'f' key on my laptop is acting up.

3 Days later, and a pounding head....NOTHING!

Thats right....NOTHING in Network.

---

### Post by mygor on 2008-02-09
> **BillB said:**
> Hi Bill,

Thanks....as I have never heard of a 'terminal' before (Ubuntu), or what it does.  I'll give it a try, as I don't really know how to cut from one computer w/ an internet connection, and paste to another w/o a connection as instructed.
How are the animals today?

Bill
p.s.  But to think that every piece of hardware that I try to ad to a Linux machine (printer, camera, etc.) will be as difficult as the wifi adapter is discouraging.

I don't believe they will be as difficult Wifi seems to be the one that gives the most problems. I have a set of usb speakers that is giving me fits right now. It would seem that the system thinks they are a memory device. LOL! I'm still searching the forums about that. I'll ask later if I can't find the answer on my own.

I think in another post that you said your network card was recognized as a (Prism controller) or something. If that is so then your problem may not be the drivers. You may instead try to set up the network if the card has been recognized. From what I have read so far you have to put in the settings for the card and the router so they can communicate with each other. In my last post here I put up a link for setting up the wifi network. You should try going there for more instructions.

Bill

---

