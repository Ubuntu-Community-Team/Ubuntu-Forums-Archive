---
title: "New Laptop, New OS, No High Res, No Wireless!!!!"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by CoyoteE on 2008-01-10
[SIZE="4"][/SIZE]Hey everybody!!! Here I am (another fed up consumer with the ever present Vista) trying to be rid of this burden so I decided to go with Ubuntu with which I was successful  in getting both to live in my new Laptop in harmony (It's a Fujitsu LifeBook N6460 with a dedicated 256Mb video card). The Laptop works fine but I really want to throw Cinelerra in (that's the reason I bought it in the first place, I mean the video editing!!!) and Ubuntu doesn't see or show my video card and I can't seem to get my screen to show in a normal 1440X900 res (all I get is 800X600!!!!) and... I know it's a lot! but my wireless also doesn't work!!! I am totally new to linux so I barely have an Idea on how to use a package manager!!! Please spare my ignorance or is it that my hardware has no drivers for it yet????:confused:

---

### Post by PeterJS on 2008-01-10
The drivers exist, but wireless and graphics drivers, generally are available under open licenses so they can't be installed by default. The graphics card is pretty easy, the drivers can be installed through System > Administration > Restricted Drivers Manager, if the wireless drivers are in there too you're golden, if not let us know what the wireless card is and we'll see what we can do about finding you some instructions.

Edit: Let's hope it's not an Acme wireless card. :)

---

### Post by Xavieran on 2008-01-10
First things first:Hardware specs...
do ```
lspci
``` (list pci cards) in a terminal (Applications>Accessories>Terminal)
and post the output...
 
Are you using Gutsy Gibbon 7.10?
I had the same issues with low screen res and didn't know enough to fix them so I used Feisty instead...

---

### Post by buccaneere on 2008-01-10
> **CoyoteE said:**
> Hey everybody!!! Here I am (another fed up consumer with the ever present Vista) trying to be rid of this burden so I decided to go with Ubuntu with which I was successful  in getting both to live in my new Laptop in harmony (It's a Fujitsu LifeBook N6460 with a dedicated 256Mb video card). The Laptop works fine but I really want to throw Cinelerra in (that's the reason I bought it in the first place, I mean the video editing!!!) and Ubuntu doesn't see or show my video card and I can't seem to get my screen to show in a normal 1440X900 res (all I get is 800X600!!!!) and... I know it's a lot! but my wireless also doesn't work!!! I am totally new to linux so I barely have an Idea on how to use a package manager!!! Please spare my ignorance or is it that my hardware has no drivers for it yet????:confused:

Bring up a terminal and enter [HTML]iwconfig[/HTML] , then [HTML]sudo iwlist scan[/HTML] to start on wireless diags...

post the returns for each.

---

### Post by CoyoteE on 2008-01-12
[SIZE="4"][/SIZE]Thx Guys!!! I am currently using my wireless card!!! Yes, I am using Gutsy 7.10!!! Tried the restricted drivers thing to no avail, it says that I don't have any!!! And last but not least here is my post:
:guitar:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9581
01:00.1 Audio device: ATI Technologies Inc Unknown device aa08
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
1c:03.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
1c:03.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
1c:03.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
1c:03.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)

---

### Post by ugm6hr on 2008-01-12
Look like this person with the same ATI graphics card found things working with an upgrade to the Hardy **kernal** (although I think upgrading is not necessary):
[http://ubuntuforums.org/showthread.php?p=4095477&highlight=9581#post4095477](http://ubuntuforums.org/showthread.php?p=4095477&highlight=9581#post4095477)

Something about using Envy to reinstall the driver is mentioned:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Hopefully Envy will automate the process for you.  I haven't tried it myself - but it looks easy enough.  It appears Linux Mint includes it as default.

---

### Post by CoyoteE on 2008-01-12
Ok, I tried it (the upgrade) and I have enabled the driver but I can't seem to adjust the res or set the ATI card from the graphics folder.I've restarted my laptop about a dozen times!!! (OS is asking me to do it each time I try to set it up but it never works!!!!):confused:[COLOR="DarkGreen"][/COLOR]I'm Stuck!!!!!

---

### Post by CoyoteE on 2008-01-14
[COLOR="DarkGreen"][/COLOR]Envy won't install!!!! Not double clicking or on the terminal!!! I already set it to uni and multiverse!!!!:(

---

### Post by PeterJS on 2008-01-14
Does it give a specific error when you try and install it from the terminal?

---

### Post by ugm6hr on 2008-01-15
> **CoyoteE said:**
> Envy won't install!!!! Not double clicking or on the terminal!!! I already set it to uni and multiverse!!!!:(

A little more information would he helpful.  Firstly, is it Envy that won't install, or the driver?

If Envy:
Which version did you download (what is the file name)?
Does GDebi Package installer start when you double-click?
Are you online when installing?
Have you checked dependencies?
See: [http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

---

### Post by CoyoteE on 2008-01-17
Ok,I downloaded New Envy for Gutsy. I tried the package installer method and got:"Error: Cannot install 'build-essential'
Tried the terminal and nothing seems to happen all I got was:ulises@ulises-laptop:~$ cd path_to_envy's_deb_package
> sudo dpkg -i envy*.deb
> sudo apt-get install -f
> sudo envy -t
> 
> 
> 
>

---

### Post by PeterJS on 2008-01-17
Have you tried installing build essential yourself:
```

sudo apt-get install build-esential

```
that might produce a more useful error message.

---

### Post by ugm6hr on 2008-01-18
> **CoyoteE said:**
> Ok,I downloaded New Envy for Gutsy. I tried the package installer method and got:"Error: Cannot install 'build-essential'


Eh? This doesn't make sense.  Envy is a .deb file, so does not need build-essential until you run it (I think).  Double-clicking it should just install it.

Is Envy in your menu tree under Applications-> Menu Tree now?

Anyway - are you online on the Ubuntu box when doing this?  Have you enabled all repositories (see attached pic) - In Preferences in Add/Remove...

PS: I think you need to read a little about Terminal and file structure if instructions are going to mean anything to you.

The Terminal method requires you to actually *cd* (change directory) to where you have downloaded Envy New .deb (i.e. *path_to_envy's_deb_package* meeds replacing with a real directory).  To do this - copy the .deb to your Desktop, and then do this:
```
cd ~/Desktop
```

Then, to install it, you need to put the *actual* envy file name in. Assuming it hasn't changed since I used it:
```
sudo dpkg -i envy_0.9.9-0ubuntu6_all.deb
sudo apt-get install -f
```

Then it should be in your menu tree to run it.

---

