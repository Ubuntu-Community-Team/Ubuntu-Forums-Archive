---
title: "[SOLVED] Need help from the beginning"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by clickquick on 2008-01-16
I wanted to try Ubuntu becuase of all the cool things I've seen on youtube. The cube desktop to be more specific. I like the idea that I can make something that most Windows users never see. But I have been trying to get my wireless (and wired) network to work for the past two days and I am so confused.

I've read through so many tutorials and so many posts it's making my head spin. I come across a tut that says I need ndiswrapper, so I DL ndiswrapper 1.5.1  with another computer and try to figure out how to installed it.( so confused again)
I find a tut that says I need a Kernel, So I looked around and couldn't find what I was supposed to get. So I roamed through the forum trying to find answers and I seen here and there some things to DL like m4-1.4.9, compiz, automake-1.10, libtool-1.5.24 and perl-5.10.0.

But to be honest I am so confused at this point I have no idea what to do. These tut's I keep finding start out ok but then they start running under the assumption I know some stuff and I get to a point where I am like huh?

If anyone can lend some kind of hand I would appreciate it thank you.

---

### Post by eolson on 2008-01-16
Type of machine?  Laptop/Desktop?  What are the specs as best you know?

---

### Post by Dr Small on 2008-01-16
Could you please post the output of:
```
lspci
```

Dr Small

---

### Post by mikewhatever on 2008-01-16
Can you go to Applications>Accessories>Terminal and post the output of the following command here. > sudo lshw -C network
The output should show your network hardware. Have you tried this tut [https://help.ubuntu.com/7.10/internet/C/index.html](https://help.ubuntu.com/7.10/internet/C/index.html) as you call it?

---

### Post by tad1073 on 2008-01-16
I am in the same position and the tut's just run you in circles and you can't get a straight answer from anyone. I have been pulling my hair out ever sice I installed ubuntu, but I got it running. If you are on a pre-configured modem and or router everything is fine, but if you have to configure it from linux, that is a different story. Here is [my post](http://ubuntuforums.org/showthread.php?t=669287) about my troubles.

---

### Post by clickquick on 2008-01-16
wow ok since my writer doesn't seem to work with ubuntu either gonna have to write this out the long and hard way lol.

My machine is a desktop I built a long time ago, amd barton socket A cpu can't remember the speed but prob around 1.2 or 1.8 ghz, 1G RAM ati radeon video card with 512M I think if not it is a 256. 60G HDD with linksys wmp54G wireless card, it also as two built in LAN's on the motherboard which the MB is an asus A7N8X-E. I use a linksys router with cable ISP.

lsoci output is 
00:00.0 Host bridge: nVidia corporation nForces AGP (different version?) (revc1)
00:00.1 RAM Memory: nVidia Corpation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM Memory: nVidia Corpation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM Memory: nVidia Corpation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM Memory: nVidia Corpation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM Memory: nVidia Corpation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Coporation nForce2 SMBus (MCP) (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia corportation nForce Audio Processing Unit (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controller (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForces External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corportation nForce2 IDE (rev a2)
00:0d.0 FireWire (ieee 1394): nVidia Corportation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corportatin nForce2 AGP (rev c1)
01:04.0 Ethernet Controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
01:08.0 Network controller: RaLink RT 2500 802,1g Cardbus/mini-PCI (rev 01)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATAlink/SATARaid] Serial ATA Controller (rev 02)
03:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600}
03:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)

the end

Now for the sudo lshw -c network output
Hardware Lister (lshw) - B.02.08.01
usage: lshw [-format] [-ptions ...]
lshw -version
-version print program version (B.02.08.01)

format can be
-html output hardware tree as HTML
-xml poutput hardware tree as XML
-shot output hardware paths
-businfo output bus information

options can be 
-class CLASS only show a certain class of hardware
-C CLASS same as '-class CLASS
-disable TEST disable a test (like pci, isapnp, cpuid, etc.)
-enable TEST enable a test (like pci, isapnp, cpuid, etc.)

although I think this wasn't the houtput you were hoping for but I've been known to be wrong lol

---

### Post by clickquick on 2008-01-16
Oh and fyi being wired to the network doesn't let me on the internet either, nor can I see my network work grp or see my other computer.

---

### Post by mikewhatever on 2008-01-16
Terminal is case sensitive in Linux, and there is a capital **C** in the command I asked for. It's a good practice to copy/past commands rather then typing.

---

### Post by nikoPSK on 2008-01-17
> **mikewhatever said:**
> Terminal is case sensitive in Linux, and there is a capital **C** in the command I asked for. It's a good practice to copy/past commands rather then typing.

that's always good. :) By cube thing you mean compiz fusion. It's included by default with gutsy. Just download compizconfig-settings-manager and enable desktop cube. Goto General options, desktop size and set the first slider to four.

---

### Post by ckennow on 2008-01-17
> **mikewhatever said:**
> Terminal is case sensitive in Linux, and there is a capital **C** in the command I asked for. It's a good practice to copy/past commands rather then typing.

i might be wrong but i got the impression that he hand typed the contents of those files.  Perhaps installing ssh and using putty to work remotely would be in order

---

### Post by clickquick on 2008-01-17
Ok I got my internet to work by using someons wpa codes or whatever it was, then I was able to log onto the internet and download the updates as well as upgrade from 7.04 to 7.10 So now my internet is fixed and I can log on. 

nikoPSK, I'm gonna need more step by step info as to what you mean. I just got ubuntu 3 days ago so I am so new the light still hurts my eyes lol

fyi I don't know what gutsy is or how to tell if I have it,

---

### Post by nikoPSK on 2008-01-17
> **nikoPSK said:**
> that's always good. :) By cube thing you mean compiz fusion. It's included by default with gutsy. Just download compizconfig-settings-manager and enable desktop cube. Goto General options, desktop size and set the first slider to four.

well click the following: [compizconfig-settings-manager]("apt:compizconfig-settings-manager")

Once installed, open it up by going to System->Preferences->Advanced Desktop Effects Settings 

Once there goto, general options, goto the desktop size tab and set the first slider to four.

You now enable desktop cube and cube rotate. You can get enable two other nice plugins, cube caps and cube reflection. To activate the cube:

hold down Ctrl + Alt + Left click and drag.

nikoPSK

---

### Post by clickquick on 2008-01-17
Wow that was the first easy thing I've done on ubuntu...click the link and it installs the software nice. I set everything up like you described but it didn't activate the cude. the ctrl+alt+left click drag doesn't do anything. if I do a ctrl+alt+arrow key it changes desktops but not in the 3d cube mode. Is there something else I need to enable or disable/change?

---

### Post by nikoPSK on 2008-01-17
> **clickquick said:**
> Wow that was the first easy thing I've done on ubuntu...click the link and it installs the software nice. I set everything up like you described but it didn't activate the cude. the ctrl+alt+left click drag doesn't do anything. if I do a ctrl+alt+arrow key it changes desktops but not in the 3d cube mode. Is there something else I need to enable or disable/change?

to make sure it's enabled run ```
compiz --replace
```

(you need GPU drivers as well)

---

### Post by clickquick on 2008-01-17
maginus@maginus-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 1002:4152 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by nikoPSK on 2008-01-17
hrm? Try enabling compiz... Goto System->Preferences->Appearance

The desktop effects tab, then hit custom... :)

---

### Post by clickquick on 2008-01-17
It says desktop effects could not be enabled. Does it matter that in the system>administrations>restricted drivers. that my ati accelerated graphics driver is not in use?

before I upgraded to 7.10 I had 7.04 and I was able to enable desktop effects, then I upgraded and saw this restricted driver so I enabled it and found out it turned my desktop effects off. So I disabled it and I couldn't bring the effects back.

---

### Post by nikoPSK on 2008-01-17
yes, it does. Please enable the driver. :)

---

### Post by clickquick on 2008-01-17
Ok just rebooted after enabling it and went to set the appearance for effects and I got "The Composite extention is not available"

and it wont go away when I hit OK

---

### Post by stoodleysnow on 2008-01-17
You could try going to System-Administration-Synaptic Package Manager and searching for 'compiz'. make sure you have the right files installed (someone else will have to tell you exactly which are the right ones - I'm not sure). XGL has a reputation as being a bit of a pain. If that is the problem, yo might do better with an Nvidia Graphics Card - any newer than late 2002 I think. (but the newer the better).

---

### Post by clickquick on 2008-01-17
compiz comes up several time in that search

---

### Post by clickquick on 2008-01-17
I got the custom desktop effects enabled by disabling the restricted driver and restarting, I also hit esc and chose some generic kernel thing it was at the top of the list during the reboot. I came in and it let me enable it.

Still unable to get the cube working so I went to rotate cube in the advance desktop conf and I noticed in the actions tab that the "Initiate" which has the buttons ctrl+alt+button1 (which is what you told me to use to get the cube moveing) is disabled....how do I enable it?

---

### Post by clickquick on 2008-01-17
never mind it seems that was some kind of bind key, but I bound it to the menu key cause I can't figure out how to disable it again. But I got the cube working yay thankis for all the help guys and gals

---

### Post by nikoPSK on 2008-01-17
glad I can/ could help. Please mark this thread as "SOLVED". :)

---

