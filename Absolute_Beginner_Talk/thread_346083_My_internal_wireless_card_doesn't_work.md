---
title: "My internal wireless card doesn't work"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by firebirdworks on 2007-01-25
After completely batching the entire setup for the fourth time, I need help.  My wireless card won't work on ubuntu.  The switch that turns it on is on the "on" position, but the on light is off.  It worked when I used windows (thank goodness thats over), but now it won't work.  Can any one help? By the way it is a HP wireless card (internal).  Thanks.
:guitar:

---

### Post by Kobalt on 2007-01-25
Hello,

I have a HP laptop as well and I got my wireless card to work. We need to know what type of wireless card you have to make it work. To know this, please type in a Terminal the following command and copy/paste here the result. 
```
lspci
```

---

### Post by firebirdworks on 2007-01-25
Thanks for helping.
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

---

### Post by Kobalt on 2007-01-25
Allright, you have the same card as me, it will be easy then. 

1. First we will blacklist the wrong drivers with these two commands : 
```
lsmod | grep 43xx
sudo gedit /etc/modprobe.d/blacklist
```
Add *blacklist bcm43xx* between the " " at the end of the file, save and close. 
Now you unload the module with : 
```
sudo modprobe -r bcm43xx
```
And we are ready to setup the good drivers.

2. You will need the windows drivers to get you card to work. Download them [here]("http://ubunteros.free.fr/sp34152.exe"). As it is a .exe file you will need to install cabextract to use it so type this command to install it : 
```
sudo aptitude install cabextract
```
Now when it's done, extract the drivers in a folder named *bcmwl5* :
```
sudo mkdir bcmwl5
cabextract sp34152.exe /bcmwl5
```

3. Now that we have the drivers from windows we need a tool to use them, Ndiswrapper. The version of the repos didn't work for me, so I downloaded the latest version from [here]("http://sourceforge.net/projects/ndiswrapper") and compiled it. To do so, download the latest version and type these commands (make sure you have both *build-essential* and *linux-headers-'uname -r'* packages installed and if you had a previously installed version of ndiswrapper with Synaptic **remove it completely**) : 
```
tar -xzvf ndiswrapper-1.37.tar.gz
cd ndiswrapper-1.37
make distclean
make
sudo make install
```

4. Now that the tool is installed you need to set it up : 
```
sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -i /home/$USER/bcmwl5/bcmwl5.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

5. We make this tool launch at startup : 
```
sudo gedit /etc/modules
```
simply add *ndiswrapper* at the end of the list

6. Enter your ESSID and WEP key in the network manager, with right click on the icon from the notification area.

6. We're done! To check it, type this : 
```
sudo ifdown eth1
sudo ifup eth1
```

The wifi light should be blue as the sky now :)

---

### Post by firebirdworks on 2007-01-25
Wow.
Thanks for all the work.  I just got home so now I need to start working with it.  Thanks again and I will post if I encounter any problems.

---

### Post by drascus on 2007-01-25
Nice explanation its good that we have people like you in the forums. 
~drascus~

---

### Post by firebirdworks on 2007-01-28
I agree.  Only one problem.
This is a TON of code.  I have worked with it for the last three days.  I am tearing my hair out.  I talked with some "linux savy" people that say it has everything to do with selecting the right Ndiswrapper file.  I must have downloaded and installed the wrong one.  Can you show me what I may need.  Oh, and thanks for being awesome.

---

### Post by Kobalt on 2007-01-28
Ok, I will try to make things a bit clearer, so that all you need to do is copy/paste the commands. I need to know what is your user's name on your Ubuntu install, so that I can have the good path (in ex. /home/your user name/...) etc.

---

### Post by Coombabah on 2007-02-09
I have a Lenovo 3000 C200. Wireless and sound on this laptop are not Linux friendly :( still have no sound.

This got my broadcom 4311 going with WEP. It has been up for an hour so far without crashing the OS. Much better than the last method I tried.

wifi-radar and network-admin were unable to configure the wireless interface but iwconfig works every time.

lspci list this as my wireless card
03:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

and this as the sound card that still does not work
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Before tackling that I will have to work out why the single quote key does not work on this keyboard :)

Keyboard preferences had a layout with dead keys. That's fixed now.

---

### Post by Kobalt on 2007-02-09
Glad I could help you Coombabah. Just so you know, I've updated the driver to a newer version (I've edited my previous post accordingly). If you want to update your driver simply download the new file sp34152.exe then follow the second part of step 2 and follow step 4. And you're up to date :)

---

### Post by drs305 on 2007-02-26
Kobalt,

THANK YOU! I followed your post regarding
the Lenovo and wireless problems. I had been able to get an external
wireless card to work but had been unable to get the built-in card to
function until I followed your instructions. They were great and you
have been huge help.

I am now writing down the instructions and even though my wireless works, I have a couple of questions:

1.  When you write "bcm43xx" or "43xx", is that the exact format or should we actually substitute the actual version number (e.g. bcm4311)?  I put xx and it worked but it seems it really should be the actual number.

2.  I did everything in my home directory and have a folder bcmwl5 in it. Do I need to keep this folder or can it be deleted after everything is set up? I would prefer to have it somewhere else and if the folder is still necessary could I have just started your instructions from within another directory.

Thanks again for the help.

Lenovo 3000 N100 Laptop WITH wireless (now)

---

### Post by Kobalt on 2007-02-27
You're welcome drs305 ! :)

The bcm43xx is the actual name of the drivers : it is call so because it can supposedly work with all versions of broadcom cards for 43xx series (xx being whatever the number). So there is no replacing xx here...
Your concerns about having drivers and maybe ndiswrapper folders in your home directory is right, I actually don't keep these stuff out there myself. I described the way I store those things, plus an updated version of the drivers, on my blog. It's in French but since you read the instructions over here you will only need to follow the command lines : they are pretty easy, I bet you will understand everything.
Head over there to check this out : [http://www.ubunteros.fr/?p=64](http://www.ubunteros.fr/?p=64)

I'm glad I could help you ;) !
Cheerio

---

### Post by vloveya08 on 2007-02-27
So this is the...4th? time I've tried to set up ndiswrapper...and I'm so close (thank you by the way)

so when i run "sudo ndiswrapper -m" a whole string of stuff comes up...

```
valerie@valerie2:~$ sudo ndiswrapper -m
module configuration contains directive install pci:v000014E4d00004301sv000012F3sd0000103Cbc*sc*i* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 713, <MODPROBE> line 418.
module configuration contains directive install pci:v000014E4d00004301sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 713, <MODPROBE> line 419.
module configuration contains directive install pci:v000014E4d00004303sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 713, <MODPROBE> line 420.
module configuration contains directive install pci:v000014E4d00004307sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 713, <MODPROBE> line 421.
module configuration contains directive install pci:v000014E4d00004312sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 713, <MODPROBE> line 422.
module configuration contains directive install pci:v000014E4d00004320sv000000E7sd00000E11bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 713, <MODPROBE> line 423.
module configuration contains directive install pci:v000014E4d00004320sv000012F4sd0000103Cbc*sc*i* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 713, <MODPROBE> line 424.
module configuration contains directive install pci:v000014E4d00004320sv000012F8sd0000103Cbc*sc*i* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 713, <MODPROBE> line 425.
module configuration contains directive install pci:v000014E4d00004320sv000012FAsd0000103Cbc*sc*i* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 713, <MODPROBE> line 426.
module configuration contains directive install pci:v000014E4d00004320sv000012FBsd0000103Cbc*sc*i* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 713, <MODPROBE> line 427.
module configuration contains directive install pci:v000014E4d00004320sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 713, <MODPROBE> line 428.
module configuration contains directive install pci:v000014E4d00004325sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 713, <MODPROBE> line 429.
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...


```

(the last line is what made me hopeful...that has never ever come up before)

anyway...

after running the rest of the commands, the computer still doesn't recognize my wireless card...

its not quite the same as yours, its a 4310, but I figured it was close enough that it should work (every other howto for my specific card requires the same windows driver)

If it helps this is what comes up when i run ifup

```
valerie@valerie2:~$ sudo ifup eth1
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
There is already a pid file /var/run/dhclient.eth1.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

```

If you have any suggestions that would be wonderful...

---

### Post by Kobalt on 2007-02-28
Do you have a previous version of ndiswrapper installed on your system ? Launch Synaptic and search for ndiswrapper : if it finds anything select 'remove completely' and then try to compile it again by starting with :
```
$ sudo make uninstall
$ sudo make clean
```
A previously installed version of ndiswrapper seems to be bugging the one you're trying to compile...

---

### Post by vloveya08 on 2007-02-28
I tried what you said, but the same errors keep coming up...

I erased the file and told it to write it again, and that got rid of the errors, but it is still not creating either an eth1 or a wlan0, which is the same problem that I've had in the past when I've tried to use ndiswrapper...

everything says that it should be working, it says driver installed, hardware present, and all the numbers match up but for some reason it is just not working...

Edit: I figured it out...on the ndiswrapper.sf.net wiki, I was using the first driver (sp33008) and I used the other one (which apparently had some fixes...) and it fixed it, I now have internet...YAY!


Thank you so very much for your help.

---

### Post by Prometheus.172214 on 2007-02-28
Hi,
    I am in the exact boat. My notebook is a Compaq Presario M2201 TU. I will check and let you know if I have a Broadcom or Intel wireless controller.

---

### Post by ozPATT on 2007-03-01
Still no joy. :( I am following your instructions, but something is not going right.

I have removed everything to do with ndiswrapper using Synaptic.
I have downloaded the exe file, and the ndiswrapper-1.38.tar.gz file

bcm43xx was already at the end of my blacklist

i used sudo apt-get install build-essential which seemed to download some stuff and do something with it, but when i try to do the same for the linux-headers-'uname -r', it says it can't find the package. Could this be why it doesn't work?

When i get to this bit: sudo ndiswrapper -e bcmwl5; it says that it doesnt exist in /etc/ndiswrapper

Hope to hear back soon, as this has now (aside from the last however many weeks) been 7 hours trying to get it working - a whole day of productivity gone... :(

thanks

Patrick

---

### Post by ozPATT on 2007-03-01
hahahahahahahahahahahahahahaha

you should have given me the French version the first time :D never has the colour blue looked so bright :D

Woohoo! my laptop is cured and I am using the newest kernel! 

I went through the french one, and had no errors, so figured I must be doing something right. Then at the end nothing seemed to be different, and when i used ifdown eth1, and ifup eth1, and neither of them worked, just gave me the same errors i had had for ages. 

Then I decided I would restart, et voila! It works! Thank you soooooooooo much, you have saved the day and Im sure many future days :)

Many Thanks

Patrick

---

### Post by Kobalt on 2007-03-01
Glad I could help you Pat' ;) ! 
Just so you know : linux-headers-'uname -r' is the package linux-headers-<your kernel version> and to know your kernel version you must type in a Terminal the command *uname -r*... Which is why we refer at this package as linux-headers-'uname -r'

---

### Post by ozPATT on 2007-03-01
ahh cool thanks for the info :D i managed to break my computer again about 5 mins after i got it fixed, but you will be pleased to know that the wireless is still working like a charm :D - i just cant log in to the gui to use it :(

---

### Post by Prometheus.172214 on 2007-03-02
All right here is some more information. The Wireless Controller in my System is a Broadcom Controller. I have tried a couple of tools like Wifi Radar, Wireless Assistant etc, but none of them detect the Wireless network. Below are the screenshots from the device manager. It helps me little, because I don't have a clue for what I am looking at and what I am supposed to look at. It is possible that Windows has clouded my vision ! Anyway, I am stuck with a wired connection and can go online with the wired NIC, but get no where with the wireless. Kind of defeats the entire idea of having a wireless enabled notebook pc. Your guidance is highly appreciated. 


[http://img293.imageshack.us/img293/3293/screenshot1tj2.png](http://img293.imageshack.us/img293/3293/screenshot1tj2.png)

[http://img67.imageshack.us/img67/5792/screenshot2ix3.png](http://img67.imageshack.us/img67/5792/screenshot2ix3.png)

[http://img111.imageshack.us/img111/8428/screenshot3ys7.png](http://img111.imageshack.us/img111/8428/screenshot3ys7.png)

---

### Post by Kobalt on 2007-03-02
Allright Prometheus.172214, your card is a Broadcom 4318. It is a very common card, there is a huge howto thread [over here]("http://www.ubuntuforums.org/showthread.php?t=197102") you might want to check. That'll help you out.

---

### Post by Prometheus.172214 on 2007-03-02
You The Man ! (Talk about my laziness in not searching right)

---

### Post by chris_ak on 2007-03-02
Excellent!  I tried your method initially but I ran into problems but no others worked so I eventually ended up back here.  One problem I had was during the cabextract step the files kept dumping into my home directory rather than in bcmwl5.  To solve this I just made sure that the .exe file was definitely already in the folder and cd bcmwl5 and did the cabextract in there.  I don't know if it was just me messing up a step or what.  but at any rate if anyone runs into this problem just do what I did.  I really thought I would never see that blue light again.

---

### Post by Kobalt on 2007-03-03
Great, two more wifi-Ubuntu users ! ;)

---

### Post by drs305 on 2007-03-05
> **vloveya08 said:**
> I tried what you said, but the same errors keep coming up...

Thank you so very much for your help.

vloveya08,

My card is also a Broadcom. I think mine is a 4311 and it's now working in a Lenovo 3000 N100. I had some directory issues as did a poster above but everything is now working. Did you get yours to work?

I followed Kobalt's instructions and then saved what I did in a format I'd understand if I had to do it again. The notes may only make sense to me but here they are:

	lsmod | grep 43xx   # Blacklist bad drivers  (43xx is the proper format, don't substitute 4311)
	sudo gedit /etc/modprobe.d/blacklist
		Add blacklist bcm43xx at the end, save and close
	sudo modprobe -r bcm43xx	# Unload module
	Download good drivers from: [http://ubunteros.free.fr/sp34152.exe](http://ubunteros.free.fr/sp34152.exe)	( sp34152.exe )
	sudo aptitude install cabextract  # Install cabextract to use above file
	sudo mkdir bcmwl5 
	sudo mv sp34152.exe /bcmwl5   # Create folder
	cd bcmwl5
	sudo cabextract sp34152.exe 	# Extract to newly created directory
	Install Ndiswrapper from:   [http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper) 
	tar -xzvf ndiswrapper-1.37.tar.gz
	cd ndiswrapper-1.37 
	make distclean
	make
	sudo make install
	Setup ndiswrapper:
	sudo ndiswrapper -e bcmwl5
	sudo ndiswrapper -i /etc/ndiswrapper-1.37/bcmwl5/bcmwl5.inf
	sudo ndiswrapper -l
	sudo ndiswrapper -m
	sudo modprobe ndiswrapper
	sudo gedit /etc/modules	# Make ndiswrapper launch at startup
	Add ' ndiswrapper ' at end of list, save & close

On my machine, I had to make sure the external radio switch was on, as I haven't discovered how to access the Broadcom software yet. I gain access by right clicking on the network manager icon.

Thanks again to Kobalt for all the help.

---

### Post by delaguer on 2007-04-11
great tutorial!! I finally get the wireless working!!! Thanks a lot!

---

### Post by noahtron on 2007-04-19
i'm fine until i get to:

----------------
4. Now that the tool is installed you need to set it up : 
[CODE]sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -i /home/$USER/bcmwl5/bcmwl5.inf
sudo ndiswrapper -l
----------------

when i enter 'sudo ndiswrapper -l' into the terminal i get:

bcmwl5 : driver installed
        device (14E4:4319) present (alternate driver: bcm43xx)
bcmwl5.sys : invalid driver!


how do i make bcmwl5.sys into a valid driver! :confused: 
also, once i get to this step, my wireless connection option disappears from the network manager, as if i didnt even have a card...

alternatively, how do i start all over again, in case i made a mistake?

i'm running feisty, i have the same card, and i got ndiswrapper off synaptic today...

---

### Post by typhen on 2007-04-24
Works for me and my Ubuntu Lenovo 3000 C200! Thanks Kobalt!
It's great to have experienced some install/compile command line action on my first ubuntu day!

---

### Post by jaywee on 2007-04-27
> **Kobalt said:**
> Allright, you have the same card as me, it will be easy then. 

1. First we will blacklist the wrong drivers with these two commands : 
```
lsmod | grep 43xx
sudo gedit /etc/modprobe.d/blacklist
```
Add *blacklist bcm43xx* between the " " at the end of the file, save and close. 
Now you unload the module with : 
```
sudo modprobe -r bcm43xx
```
And we are ready to setup the good drivers.

2. You will need the windows drivers to get you card to work. Download them [here]("http://ubunteros.free.fr/sp34152.exe"). As it is a .exe file you will need to install cabextract to use it so type this command to install it : 
```
sudo aptitude install cabextract
```
Now when it's done, extract the drivers in a folder named *bcmwl5* :
```
sudo mkdir bcmwl5
cabextract sp34152.exe /bcmwl5
```

3. Now that we have the drivers from windows we need a tool to use them, Ndiswrapper. The version of the repos didn't work for me, so I downloaded the latest version from [here]("http://sourceforge.net/projects/ndiswrapper") and compiled it. To do so, download the latest version and type these commands (make sure you have both *build-essential* and *linux-headers-'uname -r'* packages installed and if you had a previously installed version of ndiswrapper with Synaptic **remove it completely**) : 
```
tar -xzvf ndiswrapper-1.37.tar.gz
cd ndiswrapper-1.37
make distclean
make
sudo make install
```

4. Now that the tool is installed you need to set it up : 
```
sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -i /home/$USER/bcmwl5/bcmwl5.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

5. We make this tool launch at startup : 
```
sudo gedit /etc/modules
```
simply add *ndiswrapper* at the end of the list

6. Enter your ESSID and WEP key in the network manager, with right click on the icon from the notification area.

6. We're done! To check it, type this : 
```
sudo ifdown eth1
sudo ifup eth1
```

The wifi light should be blue as the sky now :)
Thanks a lot,and it works fine in my computer!!

---

### Post by jonathanmotes on 2007-10-01
Wow, thanks so much for this. Gutsy uses Ndiswrapper Version 1.43 (in the repositories) which doesn't seem to work for my card (BCM94311) while version 1.42 (which I used with Feisty) worked fine. Looking at this, I decided to download the source code ( Version 1.48 ) and followed the instructions here. I finally have my wireless working on Gutsy after trying for over a week!

---

### Post by mark.oconnor on 2007-10-31
BCM94311 is my Broadcom card on a new HP G5000 alptop - Its a dead stick and I'm beginning to regret ubuntu as wireless is key for me - How might the advice above need modification to accomondate my card version - if there is anyone in the Bristol area of the UK that is a linux expert I am happy to buy you a beer or three to get this  sorted but would be happy for instruction here if no!t

Many thanks in advance for your replies to a frustrated newbie

cheers

Mark

---

### Post by mrgordonz on 2007-12-13
> **Kobalt said:**
> 
3. Now that we have the drivers from windows we need a tool to use them, Ndiswrapper. The version of the repos didn't work for me, so I downloaded the latest version from [here]("http://sourceforge.net/projects/ndiswrapper") and compiled it. To do so, download the latest version and type these commands (make sure you have both *build-essential* and *linux-headers-'uname -r'* packages installed and if you had a previously installed version of ndiswrapper with Synaptic **remove it completely**) : 
```
tar -xzvf ndiswrapper-1.37.tar.gz
cd ndiswrapper-1.37
make distclean
make
sudo make install
```

4. Now that the tool is installed you need to set it up : 
```
sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -i /home/$USER/bcmwl5/bcmwl5.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

Hi Kobalt,

Everything goes fine until I have to execute ```
make distclean
```

Here is what I get:
```
make -C driver clean
make[1]: Entering directory `/opt/ndiswrapper-1.50/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/opt/ndiswrapper-1.50/driver'
make -C utils clean
make[1]: Entering directory `/opt/ndiswrapper-1.50/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/opt/ndiswrapper-1.50/utils'
rm -f *~
rm -fr ndiswrapper-1.50 ndiswrapper-1.50.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/opt/ndiswrapper-1.50/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h built-in.o
make[1]: Leaving directory `/opt/ndiswrapper-1.50/driver'
make -C utils distclean
make[1]: Entering directory `/opt/ndiswrapper-1.50/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/opt/ndiswrapper-1.50/utils'
rm -f .\#*
root@goopodnb1:/opt/ndiswrapper-1.50# make
make -C driver
make[1]: Entering directory `/opt/ndiswrapper-1.50/driver'
make -C /usr/src/linux-headers-2.6.15-29-386 SUBDIRS=/opt/ndiswrapper-1.50/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-29-386'
  LD      /opt/ndiswrapper-1.50/driver/built-in.o
  CC [M]  /opt/ndiswrapper-1.50/driver/crt.o
In file included from /opt/ndiswrapper-1.50/driver/crt.c:16:
/opt/ndiswrapper-1.50/driver/ntoskernel.h:716: error: field ‘lock’ has incomplete type
/opt/ndiswrapper-1.50/driver/ntoskernel.h: In function ‘raise_irql’:
/opt/ndiswrapper-1.50/driver/ntoskernel.h:753: warning: implicit declaration of function ‘mutex_lock’
/opt/ndiswrapper-1.50/driver/ntoskernel.h: In function ‘lower_irql’:
/opt/ndiswrapper-1.50/driver/ntoskernel.h:775: warning: implicit declaration of function ‘mutex_unlock’
make[3]: *** [/opt/ndiswrapper-1.50/driver/crt.o] Error 1
make[2]: *** [_module_/opt/ndiswrapper-1.50/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-29-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/opt/ndiswrapper-1.50/driver'
make: *** [all] Error 2

```

I get similar errors with the next two commands:
```
make
sudo make install
```

Consequently, when I run 
```
sudo ndiswrapper -e bcmwl5
```
I get the message:
```
sudo: ndiswrapper: command not found
```

I downloaded the latest version of ndiswrapper (1.50).  Should I be using a particular version?  My wifi card is the same as yours - BCM4311, in a HP Pavilion 6000.

My kernel is 2.6.15-29-386, and I am using Dapper Drake.

Any ideas why I am getting the errors above?  I'll see if I can download and use the same version of ndiswrapper you used - maybe that will do the trick.

---

### Post by mrgordonz on 2007-12-13
> **drs305 said:**
> I followed Kobalt's instructions and then saved what I did in a format I'd understand if I had to do it again. The notes may only make sense to me but here they are:

	lsmod | grep 43xx   # Blacklist bad drivers  (43xx is the proper format, don't substitute 4311)
	sudo gedit /etc/modprobe.d/blacklist
		Add blacklist bcm43xx at the end, save and close
	sudo modprobe -r bcm43xx	# Unload module
	Download good drivers from: [http://ubunteros.free.fr/sp34152.exe](http://ubunteros.free.fr/sp34152.exe)	( sp34152.exe )
	sudo aptitude install cabextract  # Install cabextract to use above file
	sudo mkdir bcmwl5 
	sudo mv sp34152.exe /bcmwl5   # Create folder
	cd bcmwl5
	sudo cabextract sp34152.exe 	# Extract to newly created directory
	Install Ndiswrapper from:   [http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper) 
	tar -xzvf ndiswrapper-1.37.tar.gz
	cd ndiswrapper-1.37 
	make distclean
	make
	sudo make install
	Setup ndiswrapper:
	sudo ndiswrapper -e bcmwl5
	sudo ndiswrapper -i /etc/ndiswrapper-1.37/bcmwl5/bcmwl5.inf
	sudo ndiswrapper -l
	sudo ndiswrapper -m
	sudo modprobe ndiswrapper
	sudo gedit /etc/modules	# Make ndiswrapper launch at startup
	Add ' ndiswrapper ' at end of list, save & close


Hi drs305,

I have tried following the instructions, but I have some issues with directories or files "not existing".  If it isn't too much trouble, I have a few questions for you:

1.  When you download the Windows drivers from [http://ubunteros.free.fr/sp34152.exe](http://ubunteros.free.fr/sp34152.exe), where do you save the exe file?  I saved it in a directory /home/phobbs/downloads/drivers/broadcom.  I suspect this is not really where it is meant to go.

2.  After you execute the command ```
sudo cabextract sp34152.exe
``` do you subsequently move the directory bcmwl5?

3.  When you download the ndiswrapper file (ndiswrapper-1.37.tar.gz), where did you put it?  I initially put it in /home/phobbs/downloads/ndiswrapper, but again I suspect this is not the ideal location.

4.  When you extract the contents of ndiswrapper-1.37.tar.gz, where do they go?  In Kobalt's original instructions, he puts them under /opt/ndiswrapper-1.37.tar.gz, but you seem to have them under /etc.  What is the difference, and which is "right"?

5.  When I got the step ```
sudo ndiswrapper -e bcmwl5
``` I got this error: ```
couldn't delete /etc/ndiswrapper/bcmwl5: No such file or directory
```

I must confess I am thoroughly confused about what I'm supposed to do - especially when I get an error that isn't mentioned.

Cheers

---

### Post by monestri on 2007-12-21
> **mrgordonz said:**
> Hi Kobalt,

Everything goes fine until I have to execute ```
make distclean
```

Here is what I get:
```
make -C driver clean
make[1]: Entering directory `/opt/ndiswrapper-1.50/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/opt/ndiswrapper-1.50/driver'
make -C utils clean
make[1]: Entering directory `/opt/ndiswrapper-1.50/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/opt/ndiswrapper-1.50/utils'
rm -f *~
rm -fr ndiswrapper-1.50 ndiswrapper-1.50.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/opt/ndiswrapper-1.50/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h built-in.o
make[1]: Leaving directory `/opt/ndiswrapper-1.50/driver'
make -C utils distclean
make[1]: Entering directory `/opt/ndiswrapper-1.50/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/opt/ndiswrapper-1.50/utils'
rm -f .\#*
root@goopodnb1:/opt/ndiswrapper-1.50# make
make -C driver
make[1]: Entering directory `/opt/ndiswrapper-1.50/driver'
make -C /usr/src/linux-headers-2.6.15-29-386 SUBDIRS=/opt/ndiswrapper-1.50/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-29-386'
  LD      /opt/ndiswrapper-1.50/driver/built-in.o
  CC [M]  /opt/ndiswrapper-1.50/driver/crt.o
In file included from /opt/ndiswrapper-1.50/driver/crt.c:16:
/opt/ndiswrapper-1.50/driver/ntoskernel.h:716: error: field &#8216;lock&#8217; has incomplete type
/opt/ndiswrapper-1.50/driver/ntoskernel.h: In function &#8216;raise_irql&#8217;:
/opt/ndiswrapper-1.50/driver/ntoskernel.h:753: warning: implicit declaration of function &#8216;mutex_lock&#8217;
/opt/ndiswrapper-1.50/driver/ntoskernel.h: In function &#8216;lower_irql&#8217;:
/opt/ndiswrapper-1.50/driver/ntoskernel.h:775: warning: implicit declaration of function &#8216;mutex_unlock&#8217;
make[3]: *** [/opt/ndiswrapper-1.50/driver/crt.o] Error 1
make[2]: *** [_module_/opt/ndiswrapper-1.50/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-29-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/opt/ndiswrapper-1.50/driver'
make: *** [all] Error 2

```

I get similar errors with the next two commands:
```
make
sudo make install
```

Consequently, when I run 
```
sudo ndiswrapper -e bcmwl5
```
I get the message:
```
sudo: ndiswrapper: command not found
```

I downloaded the latest version of ndiswrapper (1.50).  Should I be using a particular version?  My wifi card is the same as yours - BCM4311, in a HP Pavilion 6000.

My kernel is 2.6.15-29-386, and I am using Dapper Drake.

Any ideas why I am getting the errors above?  I'll see if I can download and use the same version of ndiswrapper you used - maybe that will do the trick.

I am also having this problem. Any help would be apreciated.

*Edit* @ mrgordonz

It might be hard to get the latest version running on this version of ubuntu. Some functions are only available on newer kernels. I tried compiling ndiswrapper 1.45 and it worked perfectly. Go to sourceforge; they keep a full list of previous versions.

---

### Post by ozPATT on 2008-03-07
> **Kobalt said:**
> You're welcome drs305 ! :)

The bcm43xx is the actual name of the drivers : it is call so because it can supposedly work with all versions of broadcom cards for 43xx series (xx being whatever the number). So there is no replacing xx here...
Your concerns about having drivers and maybe ndiswrapper folders in your home directory is right, I actually don't keep these stuff out there myself. I described the way I store those things, plus an updated version of the drivers, on my blog. It's in French but since you read the instructions over here you will only need to follow the command lines : they are pretty easy, I bet you will understand everything.
Head over there to check this out : [http://www.ubunteros.fr/?p=64](http://www.ubunteros.fr/?p=64)

I'm glad I could help you ;) !
Cheerio

the french link doesnt work any more, and is the only instructions that have ever worked for me :D could you tell me where i can find these commands again please?? 

Patrick

---

