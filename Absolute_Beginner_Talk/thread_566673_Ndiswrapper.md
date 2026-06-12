---
title: "Ndiswrapper"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by Liliitha on 2007-10-03
Well I have downloaded ndiswrapper, unzipped it, and now it is sitting in a file.  I have no idea what to do to install it because whenever I click on an .exe which for windows is what installs it, it says I can't do that.  The directions on how to do it were rather vague...  They say to mix the files from the Linksys CD together but what do I do after that?  How do I activate ndiswrapper?

---

### Post by tdrusk on 2007-10-03
Open a terminal and enter
```
lspci
```
paste the output here. I can probably find you a step by step guide for your card.

---

### Post by RomeReactor on 2007-10-03
Hi. Just as a comment: if you don't need the absolutely most up to date packages for NdsWrapper, you can get the **.deb** packages here:

[NdisWrapper Common]("http://mirrors.xmission.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.38-1ubuntu1_all.deb")

[NdisWrapper Utils]("http://mirrors.xmission.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb")

To install them, just double-click on them (first ndiswrapper-common, then ndiswrapper-utils).

---

### Post by Liliitha on 2007-10-03
gaurdian@Box:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
gaurdian@Box:~$ 



Is what comes out.  When I type       apt-get install ndiswrapper-utils-1.48     or ndiswrapper  or ndiswrapper-utils    or ndiswrapper-common    It just says the package cannot be found.

---

### Post by tdrusk on 2007-10-03
You're very lucky :)

go to system>administration>synaptic package manager
search for bcm43xx-fwcutter
install it 

I'm not sure what it will ask, but if you have any questions ask here.

That should work. You may have to restart after it's done. Click the network manager (top right) and select your wireless access point.

Delete the ndisrapper files. You don't need them.

---

### Post by Liliitha on 2007-10-03
: (  Nothing happend.  It detected nothing.  As for the ndiswrapper, Well I installed it.  ^>^  A bunch of numbers came up after I told it to install the directory...   I don't think anything happend... just a bunch of numbers popped up.  At least it's something?  ^>^  Any advice on how to get the drives up and running?  Or why the latter decision did not help?

---

### Post by tdrusk on 2007-10-03
> **Liliitha said:**
> : (  Nothing happend.  It detected nothing.

You're going to have to be more specific. What detected nothing? Did the installer install?

If the installer did not detect your wireless first try rebooting.If it still doesn't work toggle your wireless on and off.

---

### Post by Liliitha on 2007-10-03
> **fuzzyhair said:**
> You're going to have to be more specific. What detected nothing? Did the installer install?

If the installer did not detect your wireless first try rebooting.If it still doesn't work toggle your wireless on and off.

It didn't install.  It couldn't find the package.

---

### Post by tdrusk on 2007-10-03
> **Liliitha said:**
> It didn't install.  It couldn't find the package.

open a terminal and enter
```
sudo aptitude install bcm43xx-fwcutter
```
that should install it.

If it doesn't install

click system, administration, synaptic package manager. Go to settings, repositories, and make sure 4 boxes are checked (all but sourcecode)

I just thought of a reason why this wouldn't be working if the above doesn't work...

What version of Ubuntu are you running?

I have to go to bed. I will check this thread in about 8 hours. I hope you get this worked out. Other people should be able to help you with this, as it is a matter of installing a program and not actually configuring the card.

---

### Post by Liliitha on 2007-10-03
Alright this is what I get when I do the latter.


gaurdian@Box:~$ sudo aptitude install bcm43xx-fwcutter
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "bcm43xx-fwcutter"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
gaurdian@Box:~$ 
gaurdian@Box:~$

Anyone want to add to this?

---

### Post by crjackson on 2007-10-03
Okay, click on this link and follow the **[SIZE="3"][_[COLOR="Blue"]guide[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306")[/SIZE]**...

---

### Post by LuisC-SM on 2007-10-03
I think of two possibilities:
Whether you are not running Ubuntu Feisty FAwn 7.04 or you have no enabled the repositories as fuzzyhair mentioned above.
**@fuzzyhair wrote:**
> If it doesn't install

**[COLOR="DarkRed"]click system, administration, synaptic package manager. Go to settings, repositories, and make sure 4 boxes are checked (all but sourcecode)[/COLOR]**

I just thought of a reason why this wouldn't be working if the above doesn't work...

What version of Ubuntu are you running?
Did you do that?

---

### Post by jw5801 on 2007-10-03
As above make sure you have all the repositories enabled, and then run ```
sudo apt-get update
``` before you try and install the package.

---

### Post by Liliitha on 2007-10-03
I am running Ubuntu 7.04 and all of the boxes are checked.  It still does not read the file.  This is what I get now working with the ndiswrapper.

> gaurdian@Box:~$ ndiswrapper -l
bcmwl5 :[B] driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
drivers : invalid driver![/B]
gaurdian@Box:~$ 

I don't think this is what I should be getting.

---

### Post by jw5801 on 2007-10-03
Ok, that output with ndiswrapper means you've tried to install the driver from a directory that didn't actually contain the driver. ndiswrapper is a silly program that won't tell you if it can't find a file, it'll just go ahead and make the entry anyway and then complain that it doesn't work.Firstly undo what you've already done, ```
sudo ndiswrapper -e bcmwl5
```Then follow [this](http://ubuntuforums.org/showthread.php?t=201902) howto.

---

### Post by NullHead on 2007-10-03
Liliitha

You could give [my mini How-to a try]("http://ubuntuforums.org/showthread.php?p=3440795#post3440795"). It might be a little hard to get if you don't know much about linux but please try it any wase ;) It's down at the bottom. You might want to try [this]("http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318") thread a try and [this]("http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306") and [this]("http://ubuntuforums.org/showthread.php?t=405990") is a good one too. Hope I  didn't confuse you but [hears another very good]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty") one that I'm very sure should fix you up nicely ;)

---

### Post by Liliitha on 2007-10-03
Alright this is what I got... : (

> To load the module

gaurdian@Box:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gaurdian@Box:~$ sudo ndiswrapper -i ~/Drivers/bcmwl5.inf
installing bcmwl5 ...
couldn't open /home/gaurdian/Drivers/bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.
gaurdian@Box:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
driver bcmwl5 is already installed
gaurdian@Box:~$ ndiswrapper -l
bcmwl5 : invalid driver!
drivers : invalid driver!
gaurdian@Box:~$ sudo ndiswrapper -i ~/desktop/bcmwl5.inf
driver bcmwl5 is already installed
gaurdian@Box:~$ ndiswrapper -l
bcmwl5 : invalid driver!
drivers : invalid driver!
gaurdian@Box:~$ sudo ndiswrapper -m
module configuration already contains alias directive

gaurdian@Box:~$ sudo modprobe ndiswrapper
gaurdian@Box:~$ 



I don't know what happend but it seems even more bombed then before... : (  Got to love computers...
Well I will be back tomorrow it is getting late.

---

### Post by jw5801 on 2007-10-04
The driver wasn't in the directory you specified. What is in that directory? Can you give us the output of ```
ls ~/Drivers/
```Before you do anything else you need to remove the dodgy attempted install,```
sudo ndiswrapper -e bcmwl5
```So whenever you see "bcmwl5 : invalid driver!" it hasn't installed properly and you'll need to run the command above to remove it, before you try installing it again. In order to install the driver you'll need to make sure that both bcmwl5.inf and bcmwl5.sys are in the directory you're pointing at.

EDIT: Actually you may have a faulty ndiswrapper install, run ```
ndiswrapper -v
``` and post the output here. Doubtful, but is known to happen.

---

### Post by tdrusk on 2007-10-04
I strongly suggest focusing your attention on bcm43xx-fwcutter. It's designed to locate and install your card very easily. 

Please run
```
sudo aptitude update
```
```
sudo aptitude install bcm43xx-fwcutter
```

---

### Post by Liliitha on 2007-10-04
ndiswrapper -v

> 

gaurdian@Box:~$ sudo aptitude install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
**Couldn't find any package whose name or description matched "bcm43xx-fwcutter"**
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
[B]gaurdian@Box:~$ ndiswrapper -v
utils Error: no version specified!
driver modinfo: could not open ndiswrapper: No such device[/B]
gaurdian@Box:~$ 

Ok I am trying the latter now.  This is the output that came out.

---

### Post by tdrusk on 2007-10-04
> **Liliitha said:**
> ndiswrapper -v



Ok I am trying the latter now.  This is the output that came out.

did you do 
```
sudo aptitude update
```
first?

---

### Post by Liliitha on 2007-10-04
> **fuzzyhair said:**
> did you do 
```
sudo aptitude update
```
first?

Yup, it typed a page.  Then i did the second line and it said it wasn't found.

---

### Post by tdrusk on 2007-10-04
This is driving me mad.

Are you using the 64 bit version of Ubuntu?

---

### Post by jw5801 on 2007-10-04
bcm43xx-fwcutter is present in 64-bit anyway (I just searched and it's there).

Ok, well let's go with ndiswrapper, since we can find that!
The output of your ndiswrapper means you don't actually have a working install. So either try: ```
sudo apt-get install ndiswrapper-common ndiswrapper-modules ndiswrapper-utils
```or we can compile and install it from source (which is a newer version and probably better).
You already have the source code yes? If you don't, get it with this command:
```
wget http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz
```Otherwise use "cd" to change directories to wherever it is. You'll also need the tools required to compile the program:```
sudo apt-get install build-essential 
sudo apt-get install linux-headers-`uname -r` #make sure those are backticks (below the ~ on your keyboard), not apostrophes.
``` Then you'll want to extract the tarball```
tar -xzvf ndiswrapper-1.47.tar.gz
```change directories into the extracted folder:```
cd ndiswrapper-1.47
```Uninstall anything preexisting:```
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo make uninstall
sudo make uninstall
sudo make uninstall #yes you are meant to run it 3 times, just to make sure
```
Then make and install the program:```
sudo make
sudo make install
```
Then you'll want to cd to where the driver is located and install it:```
cd /wherever/the/driver/is #replace with the right directory
sudo ndiswrapper -i bcmwl5.inf
```and finally tell the Linux kernel that it should be using the ndiswrapper module:
```
sudo modprobe ndiswrapper
```


If you choose the ndiswrapper option you'll probably also want to blacklist the bcm43xx module, to do that use:```
sudo -s
rmmod bcm43xx
echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
exit
```

Then you should be cookin'! bcm43xx-fwcutter is probably easier if you can get apt to find it. You do have a working internet connection, right?

---

### Post by jw5801 on 2007-10-04
After you get it working you'll probably also want Linux to load the module at boot-up, else you're going to have to run a modprobe command everytime. Depending on which you go with, bcm43xx or ndiswrapper, you'll need to run the following command: ```
sudo -s
echo *insert-appropriate-module-here* >> /etc/modules
exit
```

---

### Post by Liliitha on 2007-11-05
> **jw5801 said:**
> bcm43xx-fwcutter is present in 64-bit anyway (I just searched and it's there).

Ok, well let's go with ndiswrapper, since we can find that!
The output of your ndiswrapper means you don't actually have a working install. So either try: ```
sudo apt-get install ndiswrapper-common ndiswrapper-modules ndiswrapper-utils
```or we can compile and install it from source (which is a newer version and probably better).
You already have the source code yes? If you don't, get it with this command:
```
wget http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz
```Otherwise use "cd" to change directories to wherever it is. You'll also need the tools required to compile the program:```
sudo apt-get install build-essential 
sudo apt-get install linux-headers-`uname -r` #make sure those are backticks (below the ~ on your keyboard), not apostrophes.
``` Then you'll want to extract the tarball```
tar -xzvf ndiswrapper-1.47.tar.gz
```change directories into the extracted folder:```
cd ndiswrapper-1.47
```Uninstall anything preexisting:```
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo make uninstall
sudo make uninstall
sudo make uninstall #yes you are meant to run it 3 times, just to make sure
```
Then make and install the program:```
sudo make
sudo make install
```
Then you'll want to cd to where the driver is located and install it:```
cd /wherever/the/driver/is #replace with the right directory
sudo ndiswrapper -i bcmwl5.inf
```and finally tell the Linux kernel that it should be using the ndiswrapper module:
```
sudo modprobe ndiswrapper
```


If you choose the ndiswrapper option you'll probably also want to blacklist the bcm43xx module, to do that use:```
sudo -s
rmmod bcm43xx
echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
exit
```

Then you should be cookin'! bcm43xx-fwcutter is probably easier if you can get apt to find it. You do have a working internet connection, right?

That did not work.  It said there was no module for the ndiswrapper and 
sudo apt-get install build-essential 
sudo apt-get install linux-headers-`uname -r` 
did not work either.  The last bit of them were missing...

---

### Post by Liliitha on 2007-11-05
> **jw5801 said:**
> Ok, that output with ndiswrapper means you've tried to install the driver from a directory that didn't actually contain the driver. ndiswrapper is a silly program that won't tell you if it can't find a file, it'll just go ahead and make the entry anyway and then complain that it doesn't work.Firstly undo what you've already done, ```
sudo ndiswrapper -e bcmwl5
```Then follow [this](http://ubuntuforums.org/showthread.php?t=201902) howto.

gaurdian@Box:~$ ndiswrapper -l
bcmwl5 : driver installed
device (14E4:4320) present (alternate driver:** bcm43xx**)
drivers : invalid driver!
gaurdian@Box:~$

I got this output again and now I think I know why.  I had my .cat file in the same folder, it installed bcmwl5 properly I would suppose but got confused because the .cat file was in the same folder.  This happend when the output came out bcm43xx.cat or something and I noticed that it was the .cat file in the same directory as the .inf.  Will ndis get confused if the .cat file is there and is there a way I can uninstall the .cat file?

**OH OK**  I am in a thoughtful mood at the moment.  I am going to take a random stab in the dark and say that bcm43xx, the program I was looking for, installs the .cat file while ndiswrapper uses the .inf and .sys files.  =) I think I am getting it now.  I just have to imagine Ubuntu terminal is a Starcraft computer mainframe in which I am locked up in the main computer room haul trying to escape the zerg and blow up the ship to destroy the research still detaching the computer mainframe room off and freeing myself and my friend.  I just have to learn the mainframe language and I can escape.

---

### Post by jw5801 on 2007-11-06
There isn't going to be an ndiswrapper module unless you can compile it, which you can't do unless you have the build-essential package. What's the error you get when you try to install it? Do you have a working internet connection. As for having a .cat file in the directory you have the .sys file in, no it won't make any difference. The .cat file is not "installed." When you run ndiswrapper -i bcmwl5.inf, it creates another entry elsewhere. You have a faulty one of these that you need to remove by running ```
sudo ndiswrapper -e bcmwl5
```

---

