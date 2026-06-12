---
title: "wireless on mac book"
date: 2007-05-15
forum: Apple Intel Users
---

### Post by andrewbossie on 2007-05-15
ok, im having great difficulties getting wireless to work wih feisty on a first generation mac book. ive gone through countless tutorials, google searches, and forums looking for help, i have and atheros card that is "unknown" to ubuntu, with a card id on 068c:001c. ive tried madwifi and ndiswrapper, both to no avail, and the lenovo driver doesnt seem to work. so can some one please help me out?

---

### Post by ronocdh on 2007-05-15
> **andrewbossie said:**
> ok, im having great difficulties getting wireless to work wih feisty on a first generation mac book. ive gone through countless tutorials, google searches, and forums looking for help, i have and atheros card that is "unknown" to ubuntu, with a card id on 068c:001c. ive tried madwifi and ndiswrapper, both to no avail, and the lenovo driver doesnt seem to work. so can some one please help me out?
Try the posts referred to [here]("http://ubuntuforums.org/showpost.php?p=2628664&postcount=2"). Use **sudo update-pciids** and then run **lspci** to see your chipset.

---

### Post by andrewbossie on 2007-05-15
ok so i ran sudo update-pciid, and got : Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

---

### Post by ronocdh on 2007-05-15
> **andrewbossie said:**
> ok so i ran sudo update-pciid, and got : Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
Good. Have you tried widemos's post on using MadWifi? Have you tried ndiswrapper? Please post more info on your hardware and the greater situation (e.g. what you have tried, how it hasn't worked, etc.).

---

### Post by benanzo on 2007-05-15
I have the same chip as you in my MacBook.  It should work out of the box with Feisty since the revision of the Madwifi drivers that shipped included support for this card.  What specifically is the problem?  Does NetworkManager see that you have a wireless connection at all?

if you do in a terminal:
```
sudo iwlist ath0 scan
```

do you get anything returned?

---

### Post by godd4242 on 2007-05-15
> **ronocdh said:**
> Good. Have you tried widemos's post on using MadWifi? Have you tried ndiswrapper? Please post more info on your hardware and the greater situation (e.g. what you have tried, how it hasn't worked, etc.).

He said in OP that ndiswrapper and MadWifi have not previously worked for him.

---

### Post by ronocdh on 2007-05-15
> **godd4242 said:**
> He said in OP that ndiswrapper and MadWifi have not previously worked for him.
I asked about specific guides, because he didn't post any info. MadWifi worked for very few people in this forum until widemos posted his how-to. Even more people were able to (myself included) once Bsantos posted a redaction. Saying "Beryl doesn't work" isn't informative; posting which guide was used and the hardware it was tried on offers those reading the thread a shot at helping out.

---

### Post by andrewbossie on 2007-05-16
when i ran "sudo iwlist ath0 scan" i got this in return " Scan completed :
          Cell 01 - Address: 00:12:0E:09:95:DA
                    ESSID:"WEST4851"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/94  Signal level=-26 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100"

So i do have a connection, but i cannot connect, i could using os x, and the WEP Key is correct.

---

### Post by benanzo on 2007-05-16
Ok, so the problem is most likely with NetworkManager then.

To troubleshoot NM we're going to walk through and look at exactly what it's doing when you're trying to connect.

Open a terminal Applications -> Accessories -> Terminal

Do this:
```
sudo killall NetworkManager
```

You will see the network icon disappear from your status bar.

Then do this:
```
sudo NetworkManager --no-daemon
```

This will restart NetworkManager but this time everything it does will be printed in your terminal.  If you close the terminal NetworkManager will die again.  Try to connect to your network while watching the terminal output.  If the connection fails you will see something resembling an error or disconnection status print out.  Copy and paste it back here so we can see what's wrong.  After you're done you can do CTRL-c to kill NetworkManager.

Do this to restart it normally (without it relying on the open terminal) :
```
sudo NetworkManager
```

---

### Post by andrewbossie on 2007-05-16
NetworkManager: <information>   DHCP daemon state is now 1 (starting) for interface ath0
NetworkManager: <information>   DHCP daemon state is now 9 (fail) for interface ath0
NetworkManager: <information>   Activation (ath0) Stage 4 of 5 (IP Configure Timeout) scheduled...
NetworkManager: <information>   Activation (ath0) Stage 4 of 5 (IP Configure Timeout) started...
NetworkManager: <debug info>    [1179337120.312316] real_act_stage4_ip_config_timeout (): Activation (ath0/wireless): could not get IP configuration info for 'WEST4851', asking for new key.
NetworkManager: <information>   Activation (ath0) New wireless user key requested for network 'WEST4851'.
NetworkManager: <information>   Activation (ath0) Stage 4 of 5 (IP Configure Timeout) complete.
NetworkManager: <information>   DHCP daemon state is now 14 (normal exit) for interface ath0

---

### Post by benanzo on 2007-05-16
You might read through this thread:
[http://ubuntuforums.org/showthread.php?t=187571](http://ubuntuforums.org/showthread.php?t=187571)

Among other things, one suggestion was to choose "Connect to other Network" from the NM menu, then input your network and key.

You might also try temporarily disabling any encryption and trying again.  That will narrow down the problem.  It could be that NM isn't giving your WEP key at all, or it's simply not receiving anything back after it does.

---

### Post by DucentiVigintiDuo on 2007-05-24
> **benanzo said:**
>  Does NetworkManager see that you have a wireless connection at all?

if you do in a terminal:
```
sudo iwlist ath0 scan
```

do you get anything returned?

I'm suddenly having a problem with my WiFi as well.
First generation 1.83 Macbook, used to work out of the box and scan/find networks, but now Feisty doesn't even recognize that I have a WiFi card!

Could it possibly have anything with me updating to Ubuntu Studio? I don't see how that would matter...

On performing that command I get: 

```
ath0        Interface doesn't support scanning.
```

Do you know what I can/should do? I really need the wireless.

---

### Post by ivesjd on 2007-05-24
With the ubuntu studio upgrade, are you using the low latency kernel? Because my wifi worked out of the box with feisty and then with the Low Latency kernel I had nothing. You can use the regular kernal and get the US look. Theres a thread with a short walk through on here somewhere.(Cant find it atm)

---

### Post by DucentiVigintiDuo on 2007-05-24
I have no idea, as you can see I'm quite the noob on Linux :P
Can you tell me how I can find out what kernel is being used?

---

### Post by benanzo on 2007-05-24
I'm not familiar with what kernel Ubuntu Studio is using, but there is a chance that whoever compiled that kernel removed the Madwifi driver code because it contains a proprietary HAL module that can't supported.

To find out what kernel you're running do:
```
uname -r
```

Also, try modprobing the wireless driver to see if it does, in fact, exist in that kernel:
```
sudo modprobe ath_pci
```

If it says that it doesn't exist, then that kernel removed support from the standard Ubuntu kernel.  If you don't get any output, then it succeeded, try the above step again:
```
sudo iwlist ath0 scan
```

---

### Post by DucentiVigintiDuo on 2007-05-24
Thanks for your instructions, **benanzo**.

```
user@pc:~$ uname -r
2.6.20-15-lowlatency
user@pc:~$ sudo modprobe ath_pci
Password:
FATAL: Module ath_pci not found.
```


So yeah, I am running the low latency kernel apparently, and it can't find the module.
What should I do?

Is there a way for me to not compromise low latency for recording and have WiFi as well?

---

### Post by benanzo on 2007-05-24
I see that your kernel does not include support for the wireless card.  That's OK, we'll just add it ourselves:

Download the necessary packages to build Madwifi from source:
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

Now go download the madwifi source code [[COLOR="Green"]_here_[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233&release_id=510590") and save it to your desktop.
Extract the archive either by right-clicking and choosing **Extract Here** or by navigating to it in a terminal by doing:
```
cd ${HOME}/Desktop
```
```
tar -xvf madwifi-0.9.3.1.tar.gz *#(or .tar.bz2)*
```
This will create a directory called **madwifi-0.9.3.1** on your desktop containing all the source code to the Madwifi wireless driver.

****(Be sure to save this directory after we're finished, just in case it doesn't work, you can uninstall easily.)****

Enter this directory in a terminal:
```
cd ${HOME}/Desktop/madwifi-0.9.3.1
```
if you do *ls* it should show:
```

ben@macbook:~/Desktop/madwifi-0.9.3.1$ ls
ath            contrib    include          Makefile.inc  regression  tools
ath_hal        COPYRIGHT  INSTALL          net80211      release.h
ath_rate       docs       kernelversion.c  patches       scripts
BuildCaps.inc  hal        Makefile         README        THANKS

```

Compile the driver:
```
make
```
Install the driver:
```
sudo make install
```

Insert the driver into your kernel:
```
sudo modprobe ath_pci
```

Check NetworkManager to see if it sees any networks or do:
```
sudo iwlist ath0 scan
```

*See [[I]this*]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo") page if you want to remove the Madwifi driver in the future.[/I]

---

### Post by Gen2ly on 2007-05-24
This a first gen macbook, does he need to build these?  Would installing madwifi-tools do the trick?  I ask because I figured the latest madwifi drivers where specific to the new madwifi chipset.

---

### Post by DucentiVigintiDuo on 2007-05-25
**benanzo**, thank you so much for your guide and for taking the time to guide me through!
I followed it to the letter and it shows the WiFi is enabled.

I'm probably going to try it out at a hotspot today, if there are any problems I'll let you know.

Apparently when you install Ubuntu Studio you have to install the new drivers, first gen Macbook or not.

---

### Post by benanzo on 2007-05-25
0.9.3.1 is the latest stable Madwifi that supports the first-gen macbooks.  Even the SVN snapshots (which many have been using to get support for the new Atheros chips in the Core 2 Duos) supports the older chips, but there a few regression bugs that cause the module to fail to unload cleanly on power-off/suspend.  This version is the best so far.

---

### Post by Gen2ly on 2007-05-25
Thanks for clearing that up, I assumed the drivers were forked with the new 802.11g standard.

---

### Post by fredronn on 2007-05-26
On this same topic, I'm having some trouble with wireless on my first gen macbook as well.

Everything is working fine actually, even suspend, even though battery life is not as good in ubuntu as in osx, but it's not terribly important. What's important though is a stable wifi-connection which just seems impossible. Using ubuntu any wireless connection is dropped every ten minutes on average making it almost unusable. Is anyone experiencing the same issue? Does anyone know of a fix?

---

### Post by Gen2ly on 2007-05-26
Try it manually.  Bring up the wireless card, scan for aps and connect with dhcp:
> 
ifconfig ath0 up
wlanconfig ath0 list scan

dhclient ath0

---

### Post by Halsnalle on 2007-05-27
Okay, I've got a MacBook Pro C2D 2,33Ghz and now I'd like to get wireless working.

I've understood thus far that I need to install MadWifi to get it working. I'm trying to follow this manual: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo) -- "This document is intended to be a complete set of instructions on how to get, install and use the latest MadWifi driver. No previous experience of wireless networking under Linux is assumed."

But I'm too new to Linux to understand the instructions, getting lost already at the second step: "Open a shell terminal in the MadWifi source directory." I know how to open a terminal. But a shell terminal? In a source directory? :confused:

---

### Post by benanzo on 2007-05-27
I'll give you the run down.  If you're using a MacBook Pro with Intel *Core 2 Duo* and not just *Core Duo* then you need to checkout the latest available code from the Madwifi subversion repository.  That is the code that the Madwifi developers are working on daily.  It is by no means characterized as "stable" although it seems pretty good.  If you have a MacBook with *Core Duo* the latest stable release (at the time of this writing) **0.9.3.1** should be used until a couple bugs are ironed out in the svn code.

The first thing to do is download the necessary packages to compile from source:

Open a terminal **Applications -> Accessories -> Terminal**
and type:
```
sudo apt-get install subversion build-essential linux-headers-$(uname -r)
```

Go to your desktop so you can see where everything is and what's going on:
```
cd ${HOME}/Desktop
```

[COLOR="Red"]**UPDATE**[/COLOR]
[COLOR="DarkGreen"][This]("http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2372-20070525.tar.gz") SVN snapshot is known to work well on Ubuntu Feisty and Gutsy.  To use this snapshot simply download it to your desktop, right-click it and select **Extract Here**.  Then follow the relevant steps below to compile this driver rather than using the current iteration of the SVN code.
[/COLOR]

> **[COLOR="Red"]For users willing to use SVN code ONLY (this includes users who are comfortable fixing their system if it becomes unbootable):[/COLOR]**
Download the actual Madwifi source code:
```
svn checkout http://svn.madwifi.org/trunk madwifi
```
This will create a directory on your desktop called **madwifi** which has all the sources for the driver.
Change into that directory (the source directory) :
```
cd ${HOME}/Desktop/madwifi
```
If you do **ls** inside the source directory it should show:
```

ben@macbook:~/Desktop/madwifi$ ls
ath            contrib    include          Makefile.inc  regression  tools
ath_hal        COPYRIGHT  INSTALL          net80211      release.h
ath_rate       docs       kernelversion.c  patches       scripts
BuildCaps.inc  hal        Makefile         README        THANKS
 
```


Now compile the driver:
```
make
```

Now install the driver:
```
sudo make install
```

Now insert the driver into your kernel:
```
sudo modprobe ath_pci
```

Now check NetworkManager to see if you can see any networks
or do:
```
sudo iwlist ath0 scan
```

---

### Post by Halsnalle on 2007-05-27
Thanks Benanzo, it went well until the insert-into-kernel step.

Then my screen froze, the computer runs hot and the fans speed up. After five minutes or so I restarted the computer, and now I can't get Ubuntu to start. A tenth or so of the progress bar loads, and then nothing happens...

---

### Post by Gen2ly on 2007-05-27
I think Benanzo's post there should be a sticky on this forum.  Mod?

---

### Post by cevans on 2007-05-30
> **Dirk.R.Gently said:**
> I think Benanzo's post there should be a sticky on this forum.  Mod?

Considering that with the current trunk it often causes the kernel to panic, and then causes the kernel to panic on booting, even when booting into single-user mode (I had to boot with init=/bin/bash), I should think not. In general, instructions for normal users should never use sources directly from an unstable trunk in a a version control system. One never knows what will happen to the code in the future.

In this case, I know that r2372 works without freezing.

---

### Post by benanzo on 2007-05-30
Compiling and installing the SVN code is only advised for users with a MacBook Pro with Intel Core 2 Duo or other machine that uses the newest Atheros chipset.  Support for these chips (to my knowledge) only exists in the newest Madwifi code.  It is, therefore, reasonable to suggest that this code be used in the hopes of gaining a minimum of functionality for these users.  It was stated and is more-or-less common knowledge that SVN code is risky.  Any user with an Atheros chipset that predates these newest chips should a) use the pre-compiled modules in *linux-restricted-modules* or b) compile and install the latest *stable* Madwifi code (currently **0.9.3.1**) as the SVN code seems to offer no benefit to these chips and even causes some panicky behaviour.

---

### Post by cevans on 2007-05-30
> **benanzo said:**
> Compiling and installing the SVN code is only advised for users with a MacBook Pro with Intel Core 2 Duo or other machine that uses the newest Atheros chipset.  Support for these chips (to my knowledge) only exists in the newest Madwifi code.  It is, therefore, reasonable to suggest that this code be used in the hopes of gaining a minimum of functionality for these users.  It was stated and is more-or-less common knowledge that SVN code is risky.  Any user with an Atheros chipset that predates these newest chips should a) use the pre-compiled modules in *linux-restricted-modules* or b) compile and install the latest *stable* Madwifi code (currently **0.9.3.1**) as the SVN code seems to offer no benefit to these chips and even causes some panicky behaviour.

I'm sorry, I didn't explain myself well here, as I had just written another response elsewhere on the same topic, and neglected to mention some important points that I had written about there. I should have emphasised that I think pointing users to the unstable *trunk* in a VCS is a bad idea in general, because one doesn't know whether the code will still work only hours after one has given the advice. As I mentioned, the trunk from about 2 hours ago caused a kernel panic when loaded on C2D MBPs, and then when booting, even when using single-user mode (I used init=/bin/bash to fix this, but most users won't be able to deal with that). You wouldn't have found out about this yourself, because it was caused by changes after you installed madwifi.

Instead of pointing to the trunk, it would be better to point to a particular revision. In the case of madwifi, there are snapshots, and [r2372]("http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2372-20070525.tar.gz") works. By giving this link instead of the svn trunk, I know that if someone else has a kernel panic, it isn't because of changing code. I don't have to worry about random changes that a developer might make without thinking about users of the trunk, because users aren't supposed to be using the trunk (at least in most communities; the Haskell community seems to be different, and users are expected to use the darcs trunk. But when the developers expect the use of the trunk, they develop in a very different style).

When there aren't snapshots, you can make one, or give the appropriate vcs commands to check out a particular revision.

---

### Post by Chrisj303 on 2007-05-30
Well, i've just followed Benanzo's instructions to install the latest mad wi-fi code, and now my mac won't boot Ubuntu!

When i did this : sudo modprobe ath_pci

My desktop froze, so i had to hard re-boot but now my ubuntu partition freezes when the progress bar is 1/6th of the way! 

How can i get back into my ubuntu install? - there is some work there i need to access, and i am totally at odds as to what to do now! I'm guessing that i could fix it with the LiveCD, but i have no experiance in Linux repair.

cheers,
chrisj303

---

### Post by cevans on 2007-05-30
> **Chrisj303 said:**
> Well, i've just followed Benanzo's instructions to install the latest mad wi-fi code, and now my mac won't boot Ubuntu!

When i did this : sudo modprobe ath_pci

My desktop froze, so i had to hard re-boot but now my ubuntu partition freezes when the progress bar is 1/6th of the way! 

How can i get back into my ubuntu install? - there is some work there i need to access, and i am totally at odds as to what to do now! I'm guessing that i could fix it with the LiveCD, but i have no experiance in Linux repair.

cheers,
chrisj303

Didn't you read the post directly below his that reported this problem, and my post about how to avoid it? It is quite hard to fix, which is one of the reasons why I've asked Benanzo to change his instructions: you'll have to use the LiveCD, mount the filesystem on your hard drive, go into the /lib/modules/YOURKERNEL/net/ and then delete ath_pci.ko, or go into the LiveCD, go to the svn directory, type sudo make uninstall, and hope that the makefile you happened to check out works.

In general, don't trust directions that tell you to check out code from the trunk of a repository in svn, cvs, or any other version control system. The poster of the instructions cannot know if the instructions will work or not even given exactly the same circumstances, because the code is constantly changing.

---

### Post by Chrisj303 on 2007-05-30
> **cevans said:**
> Didn't you read the post directly below his that reported this problem, and my post about how to avoid it? It is quite hard to fix, which is one of the reasons why I've asked Benanzo to change his instructions: you'll have to use the LiveCD, mount the filesystem on your hard drive, go into the /lib/modules/YOURKERNEL/net/ and then delete ath_pci.ko, or go into the LiveCD, go to the svn directory, type sudo make uninstall, and hope that the makefile you happened to check out works.

In general, don't trust directions that tell you to check out code from the trunk of a repository in svn, cvs, or any other version control system. The poster of the instructions cannot know if the instructions will work or not even given exactly the same circumstances, because the code is constantly changing.


Thanks,

I understand your soloution  - chroot into ubuntu install via LiveCD, then do as you said - shouldn't present to much of a problem.Thanks a lot!

Whats really frustrating, is that i had wireless working on my macbook using the madwifi drivers  -for one day!
Then it just stopped connecting to my WPA encrypted network (literally) overnight.

I see the last stable release is newer than the one i had working briefly, so i will give that a try.

cheers,
chrisj303

---

### Post by cevans on 2007-05-30
I'm not sure if the stable release will work for you. If I have time, I'll figure out the problem with the trunk, but until then, I know that [r2372]("http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2372-20070525.tar.gz"), a snapshot from a few days ago, shouldn't cause the freezing problem.

I'm also thinking about a general way to prevent freezes like this from continually occuring on boot, by changing around modprobe a bit. I might bring it up on devel-discuss or somewhere similar, and might develop a prototype of the system.

---

### Post by benanzo on 2007-05-30
I modified the instructions to include warning about the SVN code regression from when I originally posted.  I should not have overlooked that possibility.

---

### Post by kzm. on 2007-06-06
i got some weird behaviour with the new madwifi for the c2c as well.. i did as described and the wireless seemed to work, as i could see tons of wireless networks. but then it wont work.. it showed i was connected to my network but internet wouldnt work without the cable. so i rebooted and everything was gone! when i looked at my hardware with dsmeg it showed me:
[   36.517256] ath_pci: disagrees about version of symbol _ath_hal_attach
[   36.517260] ath_pci: Unknown symbol _ath_hal_attach
[   36.517315] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[   36.517317] ath_pci: Unknown symbol ath_hal_process_noisefloor
[   36.517514] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[   36.517516] ath_pci: Unknown symbol ath_hal_computetxtime
[   36.517689] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[   36.517691] ath_pci: Unknown symbol ath_hal_mhz2ieee
[   36.517759] ath_pci: disagrees about version of symbol ath_hal_detach
[   36.517761] ath_pci: Unknown symbol ath_hal_detach
[   36.518471] ath_pci: disagrees about version of symbol ath_hal_init_channels
[   36.518473] ath_pci: Unknown symbol ath_hal_init_channels
[   36.518629] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[   36.518631] ath_pci: Unknown symbol ath_hal_getwirelessmodes

anybody had this problem too? i also tried to repeat the installation steps, but that wont work neither... :(

---

### Post by fizz on 2007-08-28
I get the same thing

---

### Post by Lars Noodén on 2008-01-05
the correct command to checkout madwifi is
svn checkout [http://svn.madwifi.org/madwifi/trunk/](http://svn.madwifi.org/madwifi/trunk/) madwifi

---

### Post by cyberdork33 on 2008-01-05
Try using code tags:
```
 svn checkout [http://svn.madwifi.org/madwifi/trunk/](http://svn.madwifi.org/madwifi/trunk/) madwifi
```

---

