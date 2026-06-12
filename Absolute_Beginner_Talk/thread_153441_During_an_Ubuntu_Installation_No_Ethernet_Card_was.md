---
title: "During an Ubuntu Installation: No Ethernet Card was Detected!"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-31
Hello all !!!

I am trying to install Ubuntu 5.10 Breezy on a new PC:

Motherboard: Asus P5LD2-VM

I have a Router & this is the way my New PC is going to Access the Internet.

A different (older) PC that I have, is working Fine with Ubuntu & the Router & Accessing the Internet (through the Router).

So basically, the Router is setup correctly!

That different (older) PC that I mentioned, has a Motherboard: Intel D865PERL


My Problem is the following:

During the Ubuntu 5.10 Breezy install, I get the following window:
(To help you out, let me call each window:
  Window A, Window B, Window C, etc... etc. ...)


_Window A_:
Title:
Detect Network Hardware

Message:
No Ethernet Card was detected, but a Firewire interface is present.
It's possible, though unlikely, that with the right Firewire hardware connected to it, this could be your Primary Ethernet Interface.
Do you intend to use Firewire Ethernet?

Pick a choice:
YES or NO


In this stage, I pick "NO", cause it seems more logical to me...

I get another window:


_Window B_:
Title:
Configure the Network

Message:
No network interfaces detected. No network interfaces were found. The installation system was unable to find a network device.
You may need to load a specific module for your network card, if you have one. For this, go back to the Network Hardware detection step.

Pick a choice:
Go Back & Continue


In this stage, I pick "Go Back", cause there might be a "module list" I could select my LAN drivers from...

I get another window:


_Window C_:
Title:
[?]Ubuntu Installer Main Menu:

Message:
This is the main menu for the Ubuntu Installer.
Choose the next step in the Install process:

List of choices:
01. Choose Language
02. Select a keyboard Layout
03. Detect & mount CD-ROM
04. Load Installer Components from CD
05. Detect network hardware
06. Configure the Network
07. Configure a multiseat system
08. Detect Hardware
09. Partition Disks
10. Install the base system
11. Copy remaining packages to hard disk
12. Configure timezone
13. Setup users & passwords
14. Configure apt
15. Install the Grub boot loader on a hard disk
16. Install the Lilo boot loader on a hard disk
17. Continue without boot loader
18. Finish the installation
19. Change debconf priority
20. Check the CD-ROM (s) integrity
21. Save debug logs
22. Execute a shell
23. Abort the Installation


Since here, I do NOT know what to pick, I hit on the "ESC" button on my keyboard.


The "Window B" fires up again:

This time I select "Continue", to continue with the installation...

BUT when the installation is finished & I get to the Desktop, I fire Mozilla Firefox Internet Browser, type an address - e.g. http://www.yahoo.com" & get NOWHERE in the NET!!!????&*(%^&(@#$!@%!

Can somebody help me figure out how to solve this?

I want to setup this PC for my girl, to get her to learn how to use Ubuntu too!!!

Thanks!

P.S. 1> I did not have such problem with my Intel Mobo, but this is an ASUS one...

P.S. 2> According to the asus mobo page, this Mobo (ASUS P5LD2-VM), has an Intel Gb LAN, so hopefully it should be easy to setup... [http://uk.asus.com/products4.aspx?l1=3&l2=11&l3=194&model=536&modelmenu=1](http://uk.asus.com/products4.aspx?l1=3&l2=11&l3=194&model=536&modelmenu=1)

---

### Post by rwestgeest on 2006-04-01
Probably the installer does not know your network card and therefore cannot install a driver (loadable module). Sometimes this happens.

Advice: Google for your network card under linux and see if others have had similar problems and possible results. Probably sombody did have the same problems as you did installing ubuntu or any other distro. 

If all fails then you can always fall back to ndiswrapper and a windows driver for your card. 

sudo apt-get install ndiswrapper

sudo ndiswrapper -i <path to the inffile of your driver> 

sudo /etc/init.d/networking restart

good luck

---

### Post by dvarsam on 2006-04-01
I visited the "download section" of the ASUS Website:
[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)

And Found the following:

> 
1. _Drivers for Windows_:
Version   	  V9.0.15.0   	  2005/06/01 update
OS 	DOS / Win2K / WinXP / Win2003
Description 	Intel(R) Tekoa Enthernet Driver V9.0.15.0 for DOS Windows 2000/XP/2003 & 64bit XP/2003
File Size 	28.57 (MBytes)

2. _Drivers for Linux_:
Version   	  V9.0.15.0   	  2005/06/01 update
OS 	Linux
Description 	Intel(R) Tekoa Enthernet Driver V9.0.15.0 for Linux
File Size 	166.47 (KBytes)


I downloaded Both Drivers.

I first started with the Linux ones...

The file was a ".zip" type.

1. I right-clicked on it, selected "Open with Archive Manager", selected the Folder, and from the Stardard Toolbar, I selected "Extract".
2. A new window came up: I selected "Desktop" & clicked on "Extract".
3. I got a new file, named "LINUX" on my Desktop. I performed a "chmod -R 777 LINUX" to remove ALL locks.
4. Inside the "LINUX" folder, there were 3 items:
    a. A file: "e1000-6.0.54.tar.gz"
    b. A file: "LICENSE"
    c. A file: README"

5. The "README" file suggested the following:

> 
For the latest Intel network drivers for Linux, refer to the following 
website. In the search field, enter your adapter name or type, or use the 
networking link on the left to search for your adapter:

    [http://downloadfinder.intel.com/scripts-df/support_intel.asp](http://downloadfinder.intel.com/scripts-df/support_intel.asp)


So, I thought that getting the LATEST Drivers, would be the best appoach on this...

I was asked to:

> 
"Select your product in the product categories listed on the left. Downloads are grouped by product."


So, I went under "Network Connectivity\Intel Desktop Adapters"

There was a huge list in there... (about 20 choices)
I know I had a GbLAN (Gibabit), so I had to look for that...

I found:
> 
Intel PRO/ 1000 PT
Intel PRO/ 1000 GT
Intel PRO/ 1000 MT
Intel PRO/ 1000 CT
Intel PRO/ 1000 T Desktop


...and, the rest were for a speed "100 LAN", so that was NOT my case...

I did NOT know what to choose, so I picked "Intel PRO/ 1000 GT".

I got into the following page:
[http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?ProductID=1878&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?ProductID=1878&lang=eng)

It said:

> 
Select your operating system for available downloads.


I went for "Linux"!

I finally ended up here:
[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1878&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1878&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

And found this:

> 
Linux* Gigabit Adapter Base Driver   Ver.# 7.0.33   Date: 3/13/2006   Download
[e1000-7.0.33.tar.gz] (168KB)

Linux* base driver for 2.4.x and 2.6.x kernels for Intel® PRO/1000 family of Desktop and Server adapters. Use implies license acceptance.	
	
Read Me (txt)    Release Notes (txt)   

OS:Linux*


The above file, named "e1000-7.0.33.tar.gz" looked the same as the file I got from the ASUS site (e.g. "e1000-6.0.54.tar.gz"), only it looked like it could be a NEWER version...!

So, I thought I could go with that...!

I clicked on the "download" link & found this:

> 
This download is also valid for the products listed below. Use the links below for additional product downloads:

Intel PRO/1000 PT Desktop Adapter
Intel PRO/1000 GT Desktop Adapter
Intel PRO/1000 MT Desktop Adapter
Intel PRO/1000 T Desktop Adapter

... and many-many others...


The only one I could NOT find was the:
Intel PRO/1000 CT 

But then, I thought I would fall in the "most people's" category & went & downloaded the file!

Inside the "README" file (in BOTH ASUS - old - drivers & Intel's newest Drivers), it says the following:
To build a binary RPM* package of this driver, run 'rpmbuild -tb 
<filename.tar.gz>'.  Replace <filename.tar.gz> with the specific filename 
of the driver.

So, I thought I could create an ".rpm" file & then with the program "alien" create a ".deb" file.

So, on a Terminal window, I type (as suggested):

root@ubuntu:/home/dimitris/Desktop# rpmbuild -tb e1000-7.0.33.tar.gz

AND I get the following Output:

> 
Executing(%prep): /bin/sh -e /var/tmp/rpm-tmp.90777
+ umask 022
+ cd /usr/src/rpm/BUILD
+ cd /usr/src/rpm/BUILD
+ rm -rf e1000-7.0.33
+ /bin/gzip -dc /home/dimitris/Desktop/e1000-7.0.33.tar.gz
+ tar -xvvf -
drwxr-xr-x root/root         0 2006-02-03 23:53:41 e1000-7.0.33/
drwxr-xr-x root/root         0 2006-02-03 23:53:41 e1000-7.0.33/src/
-rw-r--r-- root/root      9782 2006-02-03 23:53:41 e1000-7.0.33/src/Makefile
-rw-r--r-- root/root     10268 2006-02-03 23:53:41 e1000-7.0.33/src/e1000.h
-rw-r--r-- root/root     57641 2006-02-03 23:53:41 e1000-7.0.33/src/e1000_ethtool.c
-rw-r--r-- root/root    262972 2006-02-03 23:53:41 e1000-7.0.33/src/e1000_hw.c
-rw-r--r-- root/root    140765 2006-02-03 23:53:41 e1000-7.0.33/src/e1000_hw.h
-rw-r--r-- root/root    136995 2006-02-03 23:53:41 e1000-7.0.33/src/e1000_main.c-rw-r--r-- root/root      4325 2006-02-03 23:53:41 e1000-7.0.33/src/e1000_osdep.h
-rw-r--r-- root/root     23657 2006-02-03 23:53:41 e1000-7.0.33/src/e1000_param.c
-rw-r--r-- root/root      5030 2006-02-03 23:53:41 e1000-7.0.33/src/kcompat.c
-rw-r--r-- root/root     21706 2006-02-03 23:53:41 e1000-7.0.33/src/kcompat.h
-rw-r--r-- root/root     21158 2006-02-03 23:53:41 e1000-7.0.33/src/kcompat_ethtool.c
-rw-r--r-- root/root     18671 2006-02-03 23:53:41 e1000-7.0.33/LICENSE
-rw-r--r-- root/root     25850 2006-02-03 23:53:41 e1000-7.0.33/README
-rw-r--r-- root/root      6472 2006-02-03 23:53:41 e1000-7.0.33/ldistrib.txt
-rw-r--r-- root/root     16057 2006-02-03 23:53:41 e1000-7.0.33/e1000.spec
-rw-r--r-- root/root     12268 2006-02-03 23:53:41 e1000-7.0.33/e1000.7
-rw-r--r-- root/root       417 2006-02-03 23:53:41 e1000-7.0.33/SUMS
+ STATUS=0
+ '[' 0 -ne 0 ']'
+ cd e1000-7.0.33
+ exit 0
Executing(%build): /bin/sh -e /var/tmp/rpm-tmp.90777
+ umask 022
+ cd /usr/src/rpm/BUILD
+ cd e1000-7.0.33
+ mkdir -p /var/tmp/e1000-7.0.33-root
++ uname -r
+ KV=2.6.12-9-386
+ KA=i386
++ echo 2.6.12-9-386
++ sed '{ s/hugemem//g; s/smp//g; s/enterprise//g; }'
+ KV_BASE=2.6.12-9-386
+ '[' -e /usr/src/kernels ']'
++ echo 2.6.12-9-386
++ sed 's/-.*//'
++ echo 2.6.12-9-386
++ sed 's/\([0-9]*\.[0-9]*\)\..*/\1/'
+ KSP='/lib/modules/2.6.12-9-386/build
             /usr/src/linux-2.6.12-9-386
             /usr/src/linux-2.6.12
             /usr/src/kernel-headers-2.6.12-9-386
             /usr/src/kernel-source-2.6.12-9-386
             /usr/src/linux-2.6
             /usr/src/linux'
++ for d in '$KSP'
++ '[' -e /lib/modules/2.6.12-9-386/build/include/linux ']'
++ echo
++ for d in '$KSP'
++ '[' -e /usr/src/linux-2.6.12-9-386/include/linux ']'
++ echo
++ for d in '$KSP'
++ '[' -e /usr/src/linux-2.6.12/include/linux ']'
++ echo
++ for d in '$KSP'
++ '[' -e /usr/src/kernel-headers-2.6.12-9-386/include/linux ']'
++ echo
++ for d in '$KSP'
++ '[' -e /usr/src/kernel-source-2.6.12-9-386/include/linux ']'
++ echo
++ for d in '$KSP'
++ '[' -e /usr/src/linux-2.6/include/linux ']'
++ echo
++ for d in '$KSP'
++ '[' -e /usr/src/linux/include/linux ']'
++ echo
+ KSRC=
++ echo
++ awk '{ print $1 }'
+ KSRC=
+ '[' -e /include/linux/rhconfig.h ']'
+ make -C src clean
make: Entering directory `/usr/src/rpm/BUILD/e1000-7.0.33/src'
Makefile:65: *** Linux kernel source not found.  Stop.
make: Leaving directory `/usr/src/rpm/BUILD/e1000-7.0.33/src'
error: Bad exit status from /var/tmp/rpm-tmp.90777 (%build)

RPM build errors:
    Bad exit status from /var/tmp/rpm-tmp.90777 (%build)

root@ubuntu:/home/dimitris/Desktop#


What "the heck" do I do now?

Please Help....

I am hopeless...

P.S.> I feel I want to Return my ASUS Mobo & go for an Intel one...
        But I do NOT know if this is the best approach, cause I may end up in 
        the same problem...
        Besides, ASUS claims that it Incorporates Intel's LAN technology...
        I may end up in the SAME trouble...
        Please Help

---

### Post by dvarsam on 2006-04-01
On the Drivers I got from Intel - e.g. e1000-7.0.33.tar.gz, I did the following:

1. I right-clicked on it, selected "Open with Archive Manager", selected the Folder, and from the Stardard Toolbar, I selected "Extract".
2. A new window came up: I selected "Desktop" & clicked on "Extract".
3. I got a new file, named "e1000-7.0.33" on my Desktop.


Inside the "e1000-7.0.33" folder, there was NO "configure" file to Run.

However, there was a folder named "src" (it probably means "source")

Inside there, there is a file named "Makefile".

So, I launch a Terminal window & type:

root@ubuntu:/home/dimitris/Desktop/e1000-7.0.33/src# make

I get the following output:
> 
Makefile:65: *** Linux kernel source not found.  Stop.


What can I do now?

Any ideas?

Thanks.

---

### Post by smelly_feet on 2006-04-01
[http://www.keylabs.com/linux/results/asus_P5LD2-VM.html](http://www.keylabs.com/linux/results/asus_P5LD2-VM.html)


Im having the same problem.  Installing the following right now

64bit breezy badger on p5ld2-vm pentiumD 805 2x512mb....


If I get the lan working I'll post again. If not.....I've been jailed for throwing my pc off the bridge ;)


cheers all

---

### Post by dvarsam on 2006-04-01
[QUOTE=smelly_feet][http://www.keylabs.com/linux/results/asus_P5LD2-VM.html](http://www.keylabs.com/linux/results/asus_P5LD2-VM.html)


Im having the same problem.  Installing the following right now

64bit breezy badger on p5ld2-vm pentiumD 805 2x512mb....


If I get the lan working I'll post again. If not.....I've been jailed for throwing my pc off the bridge ;)


cheers all[/QUOTE]

How did you manage to perform a search for that Mobo, in the [www.keylabs.com](www.keylabs.com) internet site?

Cause I want to search for alternative Mobo's, if I can NOT make mine work...
So, if I go to the shop & return it, I want to know (from beforehand) which OTHER one would work...

So, for example, some guy suggested buying this one:

[http://www.xpcgear.com/msi945gneof.html](http://www.xpcgear.com/msi945gneof.html)

I do NOT want to replace mine, get this one suggested & then realize that I am getting the SAME problem...
The guy on the Store will also get pissed-off if I get borrowing Mobos & return them, until I find one that works...

Question:
How can I search on this new Mobo I got suggested?
Where would I perform a search on: [http://www.keylabs.com](http://www.keylabs.com)

Thanks.

P.S.> In the meantime, I will wait for your results...

---

### Post by dvarsam on 2006-04-01
I visited the Following Site:
[http://www.keylabs.com/linux/results/](http://www.keylabs.com/linux/results/)

At the SAME time I visited ALL ASU's LGA775 Mobos from their Site:

[http://uk.asus.com/products2.aspx?l1=3&l2=11](http://uk.asus.com/products2.aspx?l1=3&l2=11)

_Conclusion_:

If you would like to buy a Mobo for your Linux, do NOT choose an ASUS Motherboard.
NONE of their LGA775 Chipset Mobos, is able to install the LAN drivers right from the start - e.g. when installing Your Ubuntu OS (or any other Linux OS)...

The LAN cards are NOT going to be detected & you will have to mess around with ".tar.gz" file formats to install your LAN Drivers...

_Warning_:
Messing with ".tar.gz" file formats, IS THE MOST DIFFICULT PROCEDURE in the whole LINUX world!!!!

_Conclusion_:
If you are NOT an expert, try to find some Mobo from a different Manufacturer...
Hopefully, it will install the Drivers right from the start, or include a ".deb" file to install - which is very easy!

---

### Post by Mustard on 2006-04-01
There is an awful lot to read in this thread, so I haven't looked at it all, but did you try the ndiswrapper suggestion that was made earlier in the thread?

---

### Post by dvarsam on 2006-04-01
[QUOTE=Mustard]There is an awful lot to read in this thread, so I haven't looked at it all, but did you try the ndiswrapper suggestion that was made earlier in the thread?[/QUOTE]

No man.
I did NOT.
Which of the 2 below should I install:

1. ndiswrapper-source

OR:

2. ndiswrapper-utils

Thanks.

P.S.> There is a ".tar.gz" file, which I also could not install.

Thanks.

---

### Post by dvarsam on 2006-04-01
I am also supposed to do this:

> 
sudo ndiswrapper -i <path to the inffile of your driver>

sudo /etc/init.d/networking restart


But, on which ".inf" file?

From the Windows Drivers, I searched the "PRO1000" Folder & found these:

1. Folder: PRO1000/WS03XP2K/e1000325.inf
2. Folder: PRO1000/WS03XP2K/e1e5132.inf
3. Folder: PRO1000/WS03XP64/e1000645.inf
4. Folder: PRO1000/WS03_32E/e1e5132e.inf
5. Folder: PRO1000/WS03_32E/e1G5132e.inf

I guess the "WS03XP2K" means (probably):

WS= Windows
03= for Windows Server 2003
XP= for Windows XP
2K= for Windows 2000
64= for 64bit XP
32= for 32bit ?

My new PC is a 64bit one.
However, the Ubuntu OS I installed, was from the Regular Ubuntu v5.10 (Breezy) CD (the same CD I used to Install Ubuntu on a 32bit Machine)...

I do NOT know if I should have installed a different Ubuntu v5.10 CD, but, which ".inf" file should I go for?

Thanks.

P.S.> I hope this does not damage anything...

---

### Post by Mustard on 2006-04-01
Eeny..meeny..miney...mo...ummm...I choose this one.. :)

e1G5132e.inf

Hehehe..your guess is as good as mine. :)  I'm assuming from what you say that you have a 32 bit install of Ubuntu, and they seem to be referring to a '32' of some kind..and both the last ones are the same inf file, but don't seem to be operating system specific.  Heck, try them all!

I've never used ndiswrapper either I should mention, so I'm probably the last person you should ask. :D


-edit-

You could try starting a new thread in the Networking section of the forum asking specifically about the ndiswrapper instructions.

-edit2-

I'm wondering whether ndiswrapper only works for wireless cards too.  I'm not totally sure.

Hmmm..I just found this at the ndiswrapper website..


[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)
> NdisWrapper

Some vendors do not release specifications of the hardware or provide a linux driver for their wireless network cards. This project implements Windows kernel API and NDIS (Network Driver Interface Specification) API within Linux kernel. A Windows driver for wireless network card is then linked to this implementation so that the driver runs natively, as though it is in Windows, without binary emulation.
Status

The driver works quite well with many miniPCI (builtin), PCI, PCMCIA (Cardbus only) and USB cards. **Although ndiswrapper is intended for wireless network cards, other devices are known to work: e.g., USB to serial port device, ethernet card, home phone network device etc. See Wiki entry List for devices known to work.** 

---

### Post by dvarsam on 2006-04-01
Hey "smelly feet", listen to this!!!

I just found 3 more people having THE SAME Problems.

Maybe they have the SAME Mobos we have...

Read this Forum's Article#: 102083

Let us ALL unite & see what we can make of...

Keep me posted man...

Thanks.

---

### Post by dvarsam on 2006-04-03
Hey "smelly feet", listen to this!!!

If you are having difficulty to setup your Audio to work with your "Asus P5LD2-VM" Mobo (the same Mobo, I have...):

Read this Forum's Article#: 154233,

or click here:

[http://ubuntuforums.org/showthread.php?t=154233](http://ubuntuforums.org/showthread.php?t=154233)

I just found out, that there is NO need to install Drivers for Sound!

Just read on that thread man...

At least we have got sound working!

Keep me posted man...

Thanks.

P.S.> Are you still breathing man, because I have not got any reply from you yet...

P.S.2> Anybody willing to help us solve this out, guys?
         PLEASE................?

---

### Post by rwestgeest on 2006-05-19
>> if [ Ubuntu_Forum=Exist ] ; then echo "Why don't I get any response from you guys?"
>> else echo "Ubuntu Forum does NOT Exist!"
>> fi

Good point. Must be frustrating. I haven't setup a(n email) notification on threads that i replied to. Should have done that. 

Anyway what i did in my case was, i first tried to figure out what the working version of the driver for my windows setup was and take the inf file that belonged to that. I did that by looking the windows device properties and on the cd that came with my network driver. 

Then installing the driver was really as simple as 

sudo ndiswrapper -i <path to the inffile of your driver>

(dont forget to modprobe ndiswrapper)

---

