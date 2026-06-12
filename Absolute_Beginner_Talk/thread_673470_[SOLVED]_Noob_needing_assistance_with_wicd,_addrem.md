---
title: "[SOLVED] Noob needing assistance with wicd, add/remove programs. Please Help!!"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by huntwell on 2008-01-20
I am new to Ubuntu Gutsy and need some help with getting Wicd to work properly. In addition, I need some help getting add/remove programs to work. I must have done something to cause it not to function anymore.

First, I quit using network manager since I could not figure out how to configure it for a WPA secured wireless connection. I downloaded Wicd since it came so highly recommended, but I can't get it to work. When I go into Applications and find it in the menu, I can click on it, but nothing happens. It doesn't open at all. I have a wired internet connection, but would really like to configure Ubuntu for wireless.

Secondly, when I go to Applications and go to Add/Remove Programs, this is what it says:

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Anyone have any info on why this is happening how?

I appreciate any help I can get with these issues.

Thanks.

---

### Post by JoshuaRL on 2008-01-20
Alright, I have a couple steps for you.  First with Wicd.  Go into the terminal and type the name of the program.  That way you'll see any error messages that come up and you can report them to us.

As for the updates, that should be an easy fix.  Could you post the output of:
```

sudo gedit /etc/apt/sources.list

```
That will tell you what sources your system is looking at when it tries to update.  We can go from there.

---

### Post by Sef on 2008-01-20
In add/remove, have you changed the top right box to 'All Available Applications'?

---

### Post by imdano on 2008-01-20
What version of wicd are you using?  And did you make sure the wicd daemon was running? Try running this command to start it:
```
sudo /etc/init.d/wicd start
```Then run the wicd tray icon using the command ```
/opt/wicd/tray.py
```

---

### Post by huntwell on 2008-01-20
Thanks for such quick replies.

See my terminal log:

bash: wicd: command not found

bash: Wicd: command not found

Output of:sudo gedit /etc/apt/sources.list 

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

This is what happened when I typed in: sudo /etc/init.d/wicd start & /opt/wicd/tray.py

sudo /etc/init.d/wicd start
Stopping any running daemons...
Starting wicd daemon...
/opt/wicd
wicd daemon: pid 6105

/opt/wicd/tray.py
attempting to connect daemon...
daemon not running...
You need to start the daemon before using the gui or tray.  Use the command 'sudo /etc/init.d/wicd start'.

When I went to Add/Remove, the error came up and I am not able to change any settings.

Again, thank you all very much for your help.

---

### Post by JoshuaRL on 2008-01-20
Okay, there's two ways you can fix the updates.  Either go into Preferences -> Administration -> Software sources and make sure you have everything allowed, or in the file you just posted uncomment, or remove the # from in front of every line that starts with "deb".  Then run:

```

sudo apt-get update

```

---

### Post by imdano on 2008-01-20
> **huntwell said:**
> This is what happened when I typed in: sudo /etc/init.d/wicd start & /opt/wicd/tray.py

sudo /etc/init.d/wicd start
Stopping any running daemons...
Starting wicd daemon...
/opt/wicd
wicd daemon: pid 6105

/opt/wicd/tray.py
attempting to connect daemon...
daemon not running...
You need to start the daemon before using the gui or tray.  Use the command 'sudo /etc/init.d/wicd start'.Looks as though the daemon isn't starting for some reason.  What version of wicd are you using?

---

### Post by huntwell on 2008-01-20
I'm using Wicd version 1.4.1

With reference to the other post, I'm sorry, but I don't quite understand exactly what I need to do as far as removing the #from each deb listing. I'm not sure how to go about doing that.

Also, at the top right of the desktop next to the volume icon, there is an orange icon with a starburst like symbol in the center and when I put the arrow over it, it says "This usually means that your installed packages have unmet dependencies"

It seems like there are a lot of problems and at this point I am wondering if I should reinstall ubuntu and start fresh.

Thanks for all of your help.

---

### Post by jrusso2 on 2008-01-20
Sounds to me like wicd didn't install.  Sounds like a broken package.

---

### Post by erfahren on 2008-01-20
> **huntwell said:**
> 
With reference to the other post, I'm sorry, but I don't quite understand exactly what I need to do as far as removing the #from each deb listing. I'm not sure how to go about doing that.

in the terminal do:
```

gksudo gedit /etc/apt/sources.list

```
Select all and the paste the below into the file overwriting the contents - (I just removed the comments (#'s) and cleaned it up a little)
```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

```
save the file and do
```

sudo apt-get update

```
you probably will get errors so do (this will fix broken dependencies): 
```

sudo apt-get install -f

```
now try to update the sources again
```

sudo apt-get update

```
and then to get all the software updates that wil be available:
```

sudo apt-get upgrade

```
now you can try getting Wicd to work

---

### Post by erfahren on 2008-01-20
oh - if you're not connected to the internet post the output of the "sudo apt-get install -f" command from my post above

---

### Post by huntwell on 2008-01-21
Thank you so much! Problem solved! Unfortunately, I am still not able to open Wicd. Any suggestions?

Thanks again,
huntwell

---

### Post by erfahren on 2008-01-21
try just reinstalling the Wicd .deb again (don't uninstall just double-click the deb installer and reinstall)

then try what's in imdano's first post again

---

### Post by huntwell on 2008-01-21
OK, so I reinstalled Wicd and then typed in the code:sudo /etc/init.d/wicd start

This is what it said: Stopping any running daemons...
Starting wicd daemon...
/opt/wicd
wicd daemon: pid 6074

When I entered the command:/opt/wicd/tray.py

It said: attempting to connect daemon...
daemon not running...
You need to start the daemon before using the gui or tray.  Use the command 'sudo /etc/init.d/wicd start'.

What do you make of this? I am still not able to get Wicd to do anything when I try to open it from the Applications menu.

Thanks for your help.

---

### Post by erfahren on 2008-01-21
I'm sorry - try:
```

/opt/wicd/gui.py

```
from: [http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq)

---

### Post by imdano on 2008-01-21
Most likely that command will just tell give you an error when it tries to connect to the wicd daemon.  The question is why is the daemon failing to run.  Open up /opt/wicd/daemon.py (make sure you do it with sudo, or you won't be able to save changes to the file), and find these lines near the very bottom of the file [php]#kill output
#POI:500 stdout redirection
output = FlushWriter()
sys.stdout = output #open("data/wicd.log","w")
sys.stderr = output[/php]
Then comment them out so they look like this [php]#kill output
#POI:500 stdout redirection
#output = FlushWriter()
#sys.stdout = output #open("data/wicd.log","w")
#sys.stderr = output[/php]Save the file and close it.  Then open a terminal and run ```
sudo /opt/wicd/daemon.py
```And post any error message that appears.

---

### Post by huntwell on 2008-01-21
So... first, my apologies for being so difficult, but I tried using the code: sudo /opt/wicd/daemon.py and this is what showed up in the terminal:

/opt/wicd
wicd daemon: pid 16612
laptop:~$ lo        no wireless extensions.

eth0      no wireless extensions.

eth1: ERROR while getting interface flags: No such device
eth1      Interface doesn't support scanning.

Please be patient with me as I am so new at this. What can you tell me about what I need to do next? I went to the web site that erfahren posted and did everything it says to do, but I still can't get Wicd to open or do anything. Any other suggestions?

Thanks for your time,
Huntwell

---

### Post by erfahren on 2008-01-21
what kind of wifi card/device to you have? you're going to make sure the card is recognized and there's a driver installed and working. 
see: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

post the output of this (we actually just need the "Ethernet controller" line for your wifi  card):
```

lspci

```
and also:
```

sudo lshw -C network

```

also make sure that your /etc/network/interfaces file only has something like this in it (if it has other commented out lines ( with #s) at the top that's ok):
```

# The loopback network interface
auto lo
iface lo inet loopback

```

---

### Post by huntwell on 2008-01-21
results of code: lspci:

laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
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
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)

Results for code: 
laptop:~$ sudo lshw -C network

  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:8c:38:82
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.2.2 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s

Results for code: # The loopback network interface
auto lo
iface lo inet loopback

laptop:~$ # The loopback network interface
-laptop:~$ auto lo
bash: auto: command not found
-laptop:~$ iface lo inet loopback

---

### Post by erfahren on 2008-01-21
sorry it took awhile to get back to you - it's pretty cold here (+5° F now) and it's starting to mess with my motivation - lol !

anyway - that last thing I put in my previous post wasn't intended to be ran as a command (but no harm done) - I was just going to have you browse to your /etc/network/interfaces file and look at it (you can just right-click and open in the text editor (it would open as read-only).

or you see its contents from just:
```

cat /etc/network/interfaces

```
you should only have what's below - (if you have some other commented out lines (with #s preceding them) at the top then that's ok):
```

# The loopback network interface
auto lo
iface lo inet loopback

```
if there is anything else in there then back it up (probably not necessary but a good idea):
```

sudo cp /etc/network/interfaces /etc/network/interfaces_back

```
...and open it in Gedit with permissions and remove anything other than what I showed above (again, commented out lines in there are ok) - and save it
```

gksudo gedit /etc/network/interfaces

```
all that was the easy part - that's just necessary for Wicd

- the real problem you're having though is that there doesn't look like there's a driver loaded for your Wifi card - which is a Broadcom BCM4312 802.11a/b/g (rev 01) 

I did some looking around on that card and came up with [this](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy) (I started [here](https://help.ubuntu.com/community/WifiDocs)) - it looks like you might just be able to enable the driver if you have an internet connection (see first section).

I don't anything else about installing that driver, I'm not familiar with it. If you need to ask questions somewhere about it make sure you mention that you're using Gutsy 64-bit (I think you are, aren't you?)

once you get that driver enabled you can try Wicd again and see what happens

---

### Post by huntwell on 2008-01-22
erfahren,

Thanks for your help. I think I followed your directions correctly (although being a noob, its possible I may have gone wrong somewhere) and I still cannot get Wicd to open.

I also went to the link you provided and checked off to make sure the driver is running. Still nothing.

At this point, I am not sure how to proceed. 

Maybe smacking my head against a wall will help :)

Anyway, thanks again for taking so much time to help me out.

---

### Post by imdano on 2008-01-22
Ok, let's continue trying to figure out why it won't open.  In addition to the lines I had you comment out earlier, I've got another change for you to make.  Find this section in daemon.py (it should be a little bit higher than the previous spot) [php]if True: #for easy disabling
    try:
        pid = os.fork()
        if pid > 0:
            # exit first parent
            sys.exit(0)[/php] And change it to: [php]if False: #for easy disabling
    try:
        pid = os.fork()
        if pid > 0:
            # exit first parent
            sys.exit(0)[/php]Run the daemon from the console again, and post any error messages.  Also, once you've started the daemon, run /opt/wicd/gui.py from another console, and post any error messages you see popping up there.

---

### Post by huntwell on 2008-01-25
imdano,

thanks for the follow up. Now I can get Wicd to open up and show the wicd manager, but now it does not show any wireless connections. 

It detected my wired connection just fine. I have gone to several sites and downloaded the appropriate software to get my broadcom wifi working, but it still won't detect any wireless networks. 

I have ndiswrapper and fwcutter installed, network manager is disabled, and yet I still cannot find a way to get my wireless working.

Is this a lost cause? Do I just need to accept the fact that my wireless will not work on this computer with linux?

If I can't get it working, I still have appreciated all of your assistance with this issue.

---

### Post by imdano on 2008-01-25
Based on your this portion of one of your earlier posts ```
Results for code:
laptop:~$ sudo lshw -C network

*-network UNCLAIMED
description: Network controller
product: BCM4312 802.11a/b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:05:00.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
```It looks as though your broadcom card doesn't have a driver associated with it, which is why you're not seeing any wireless networks.  I don't have a broadcom card myself so I can't really be too much help, but there are a bunch of tutorials here on the forums for installing the drivers a variety of broadcom cards.  You might want start a thread specifically about getting your card working if you don't have any luck searching.

---

### Post by erfahren on 2008-01-25
> **huntwell said:**
> I have ndiswrapper and fwcutter installed, network manager is disabled, and yet I still cannot find a way to get my wireless working. ....

I don't think you're supposed to use both ndiswrapper and fwcutter, just one or the other from what I understand.

I don't think getting your wifi to work with Linux is hopeless - there's [this post](http://ohioloco.ubuntuforums.org/showthread.php?t=600097) which I'm certain is concerning you're same card - Broadcom BCM4312 802.11a/b/g **(rev 01)** - and also under the Ubuntu 64-bit forum section.

You might consider switching to 32-bit Ubuntu (just the regular [i386 version](http://releases.ubuntu.com/7.10/)) - the 64-bit version sometimes requires extra configuration to get hardware (and programs) installed and/or working properly.

I tried the 64-bit version for awhile but found that all the extra research and extra steps to install some things wasn't worth it to me. Unless you're doing serious graphic or video editing you won't really notice a difference in speed between the two.

-- just a thought

---

### Post by huntwell on 2008-01-27
Erfahren,

I think you are right. I found out that my xp windows version is not 64, it is the x86. I will try the 32 bit version and see what happens.

How do you suggest I proceed with the uninstallation of the 64 and and reinstallation of ubuntu in the 32 bit. It wasn't until just yesterday that I found out how to check what version of windows I have and it is not the 64. This may be much of the problem, yes?

While I have you, I was wondering if you wouldn't mind mulling over one more thing. After I performed a defrag and installation of ubuntu, my screensaver in win xp is not activating. I checked all of the settings and made sure it is set to active, but it never activates no matter what setting I have it at. Additionally, when I click on preview, it kicks out of preview and doesn't work unless I click on it several times. 

What do you think?

Lastly, you all have been fantastic at helping me with my problems and I am very grateful.

Thank you.

---

### Post by erfahren on 2008-01-28
sry it took awhile to reply....

if you haven't installed the 32-bit yet, all you need to do is take the "Manual" partitioning option when installing with the LiveCD, You'll see the Ubuntu partition (ext3 filesystem) in the partition table. Just check the box to format it and set the mount point as root. It will reformat the old partition and install to there (no need to uninstall the 64-bit version first).

note: when setting the mount point for root - if there isn't a drop-down menu for it and you need to type in, just type it in as a slash ( / ). --- (there sometimes isn't a drop-down menu, for me at least).

see: psychocat's guide: [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
and the screeenshot there: [http://img216.imageshack.us/my.php?image=feistydual12tj0.png](http://img216.imageshack.us/my.php?image=feistydual12tj0.png)

--- with the 32-bit Ubuntu, and now that you know more about setting up your wifi driver, you should have better luck with it (hopefully). 


As far as the screensaver problem in your WinXP - if the problem only came about after you defragged and resized the partition - the only thing I know that you could try is to run Windows Check Disk (Error checking) a couple times (it's been my experience that it doesn't always fix al the errors the first time through). You can check the results in the Administrative Tools > Event Viewer > Application under a "Winlogon" entry.  see: [http://www.housing.hawaii.edu/resources/support/chkdsk.htm](http://www.housing.hawaii.edu/resources/support/chkdsk.htm)

(Its actually a good idea to run the Check Disk first on Windows anytime you go to defrag it. No one ever suggests that though - I kind of wished they would.)

-- good luck!

---

### Post by huntwell on 2008-01-29
erfarhren,

Thanks for getting back to me. You don't take long at all to reply, no apology necessary. Most times when I post on other sites sometimes I never get a reply or it takes several days.

How do I mark this thread as solved? Everything is good now. I have wireless working with network manager even! And I am very surprised at the page loading speeds, SUPER FAST! Anyway, this all came about since I reinstalled Ubuntu using the i386 version and I made the mistake of letting it take the entire disk drive. I had to reformat and reinstall windows and Ubuntu both. The good thing about that has been that I created a partition from the windows cd and now nothing overlaps at all and all of my programs work great on both the Ubuntu partition and windows partition.

Well, enough about that. Also wanted to take the opportunity to thank you for all of your help. I know helping me out has probably taken quite a bit of your time and I greatly appreciate it.

Thank you.:)

---

### Post by erfahren on 2008-01-29
you're quite welcome - glad you got everything working! ( hope you didn't lose any critical data when you wiped out your Windows.) 

my internet seems to work a little faster in Ubuntu than it does in Windows as well - I have no idea why that is.

to mark the thread as Solved just go to the "Thread Tools" above the top post.

good luck!

---

### Post by huntwell on 2008-01-29
Fortunately, no critical data was lost since I put all of my files and folders on an external hard drive. It has taken me a while to do some transferring, but not too bad.

Again, thanks for the help.

---

