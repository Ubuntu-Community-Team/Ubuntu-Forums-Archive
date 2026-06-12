---
title: "Madwifi make errors"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Zargon2000 on 2007-04-02
Madwifi make errors 

--------------------------------------------------------------------------------

Please help! Newly installed Ubunto (I really want to try this out!), and trying to get internet connection. If I can get an internet connection, I won't have to keep booting back and forth from WinXP to Ubunto to ask you guys for help!  :-) I downloaded madwifi-base-1_2_1b and am trying to install it.  I run the make and make install commands and I get errors.  (See attachments)  Also, there are a lot of directories in the madwifi directory (ath, hal, include and more) that have makefile files in them, along with a bunch of files with the .c and .h extension on them. What do I need to do to install these files?? Thanks a bunch form a newbie XP to Linux user!!

I have the output from the make and make install commands attached.

---

### Post by josephus on 2007-04-02
Where did you get the madwifi-base-1_2_1B file.  I looked around and can't quite figure out what that is.  If you want to compile madwifi from source, then go to the madwifi.org site and start from there.  It'll eventually lead you here

[http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233](http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233)

and you can download the tar.gz file which you can unpack and make.  Just use make in the base directory, and then sudo make install.

The preferred way to install madwifi is to go through the repositories and download the precompiled files.  If you have a wired connection you can use synaptic. First add the restricted repositories to the  list of sources and then download appropriate linux-restricted-modules which includes the wireless drivers that you need.

It sounds like you don't even have a wired connection on ubuntu, then I think you can download the debian files in windows and copy them over to the ubuntu partition and install using the sudo dpkg -i <package name>.

[http://packages.ubuntu.com/edgy/misc/linux-restricted-modules-2.6.17-10-generic](http://packages.ubuntu.com/edgy/misc/linux-restricted-modules-2.6.17-10-generic)

I'm assuming here that you are using Edgy with kernel version 2.6.17-10-generic.  This may not be the case and you can check  with: uname -a

There might be a couple of other files that you need to install along with the debian file listed on the link above, and they will be mentionned to you as a unsatisfied dependency when you try to install the package.

Hope this helps.
[I]
edit:  oops. I guess linux-restricted-modules are included in the edgy eft livecd and therefore you should be able to get it without jumping through so many hoops.[/I]

---

### Post by nonewmsgs on 2007-04-02
well good news and bad news.  bad news first.  im a bit confused about the output.  good news - ubuntu includes a madwifi driver! it doesnt have all the commands but it works good enough that i replaced all my prism cards with atheros netgear ones.

i think damn near all of these require sudo so if i forget one, feel free to add one.

sudo modprobe ath_pci
sudo modprobe wlan_scan_sta
sudo iwlist ath0 scan

If you get a message such as: 
ath0      Failed to read scan data : Resource temporarily unavailable

instead of actual scan results, and you are in an environment that requires a shared encryption key, try running: 
iwconfig ath0 key <yourkey>
iwpriv ath0 authmode 2

This will tell the card that it is operating in a restricted, shared-key environment, and thus it needs to use the key you supply with iwconfig. To use an open system key (which is often considered more secure) use iwpriv authmode 1: 

iwconfig ath0 key <yourkey>
iwpriv ath0 authmode 1
sudo iwconfig ah0 essid "eddie" 

(eddie is, of course, the name of your router)
 
around this point your card will light up and start connecting and you can try to do it through the wireless card with more typical-GUI conventions or continue....

dhclient ath0
dhcpcd ath0

(one of these will work depending on the way your isp is set up)

ping [www.yahoo.com](www.yahoo.com)

and see if you see anything
if you have wep

iwconfig ath0 key <wep key (in hex)>
or 
wconfig ath0 key <s:ASCII string of key>

that is my parsing of the instructions from 

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

combined with my previous experience (all madfi only commands arent there) but i have done this a few times now.  hope it works now mate!

---

### Post by Zargon2000 on 2007-04-03
Okay. Thanks a million for your help.  When I go to that link, there are quite a few files listed after the one you pointed me to:  "Other Packages Related to linux-image-2.6.17-10-generic".  Does this mean I need to download those packages too?

---

### Post by josephus on 2007-04-03
Probably not.  In my original post I had forgotten that the LiveCD includes all these packages, and therefore everything should already be on your system.  If you go into the System->Adminstration->Synaptic you can search for that package to make sure it's there.  Once you've confirmed that you can set up the network.

From the command line: iwconfig should show whether or not your wireless device is connected.  You should have an entry under ath0 and it should give detailed information about your network.  You can use the networking manager, uder Systems-Adminstration->Networking to fill in the details.

However, if after you type in iwconfig, it says that there are no wireless extensions, then let us know and we can work from there. nonewmsgs' post has some hints about what to do.

---

### Post by Zargon2000 on 2007-04-03
Thanks again for your help.  I tried everything and actually got some things installed -- not sure how LOL  I tried installing Network Manager from Synaptic and I get a message that it is not for this system -- not for i386.  I did get madwifi installed though!

Two things though:
While installing build-essential from the cd I get the message that some packages are missing -- libc6-dev, libc-dev and dpkg-dev (>=1.13.5)  when trying to install.

When typing in the wlanconfig command  I get the message "ioctl: no such device".  And when I type in iwconfig neither wifi0 nor ath0 show up in the list.  So no network access yet.

Also, I was trying to unmount my ntfs partition to mount it with rwd privileges, and when I type in unmount, I get a message that the command is not recognized.  I tried to do a "man unmount" and am told there is no man entry for unmount, although there is one there for mount.

Thanks again for your help!  We will get this puppy running yet!

---

### Post by josephus on 2007-04-03
OK.  It's weird that you are trying to install stuff that should already be on your system.  Network manager should be loaded up on a normal setup of Ubuntu.   Can you run through what you've done to your system so far?  As well can you give me the output of 

```
lspci 
lsmod
dmesg | grep ath_
iwconfig
```

The first command gives more info about your hardware, the second command tells me which modules are loaded up, and the third lists the messages the system has received from the madwifi drivers.

---

### Post by Zargon2000 on 2007-04-03
First off, thank all of you for all of your help.  I have decided to repartition and reinstall Ubunto.  I have learned a lot, and it doesn't take that long to do.  I have tried to install so many things I don't know whats what now!  :-)  

My question is:  can you tell me what I need that isn't on the Ubuntu cd (ubuntu-6.10-  desktop-i386)?  Or what is on the CD that doesn't get automatically installed that I need to install manually? I never did get the darn network card to work!  :-(  
 My network card is: 

DWL-G520M Wireless 108G MIMO PCI Adapter
Atheros Communications Inc.  AR5005VL 802.11bg Wireless NIC

Thanks for all your help!!

---

### Post by josephus on 2007-04-03
OK.  A quick search of your card shows that you will have problems getting it to run on Edgy Eft.  The card is not properly recognize by HAL which is used by the Madwifi drivers.  There isn't too many posts about your card so I'm not sure if running Feisty Fawn will solve your problems or not.  

The good news is that you should be able to get your card working with ndiswrapper.  Basically this takes Windows drivers for your cards and makes them useable on Linux. 

You should be able to find the drivers somewhere on your windows partition.  If you can't find them follow the links on this page (your card is listed somewhere in the middle)
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Copy the files in the drivers directory of the zip file to somewhere onto your linux partition.  Loading them up is fairly easy.

1. First remove madwifi drivers from memory
2. Attach driver to ndiswrapper
3. Load ndiswrapper

```

sudo modprobe -r ath_pci
sudo ndiswrapper -i net5513.inf
sudo modprobe ndiswrapper

```

If the second step works then it should say something like: 'driver installed, hardware present'

*edit: there was a typo in the second line*

---

### Post by nonewmsgs on 2007-04-03
ndiswrapper oh no 

*moves back and forth shuddering in the corner until he falls over and curls up in the fetal position crying*

good luck and god speed.  i never did get those stupid prism cards to work and judging from the way my drowning cries for help were responded to, i would guess some other people found it tough too... ( i did replace all my prism pcmcia cards and decided $30 is definitely worthwhile for a well supported card.)

---

### Post by josephus on 2007-04-03
no need to scare Zargon like that ;> 

ndiswrappers work without problems for many people.

---

### Post by nonewmsgs on 2007-04-03
my bad.  yeah, just follow the instructions and hopefully you can tell me everything works.  i wont be jealous just glad that the spftware helped someone.

---

### Post by Zargon2000 on 2007-04-03
Okay, thanks a million!  I will give that a try.  Do I then do these commands ---->
 
"wlanconfig ath0 create wlandev wifi0 wlanmode sta"
"ifconfig ath0 up"
"modprobe wlan_scan_sta"
"iwlist ath0 scan"
"iwconfig ath0 key <key>"
"iwpriv ath0 authmode 2"

??  Are these the correct commands to set it up after I have loaded the ndiswrapper?  I want to make sure and do this right the first time around!  Thanks!  :)

---

### Post by nonewmsgs on 2007-04-03
umm it isnt ath0 because ath is for atheros driver...im not sure really, so i am stepping away for someone who knows about this.

---

### Post by josephus on 2007-04-03
I've never had to use these commands:

wlanconfig ath0 create wlandev wifi0 wlanmode sta
modprobe wlan_scan_sta

the authmode depends on how your router/encryption configuration. 

but i think it's sufficient to
ifconfig ath0 up
iwconfig ath0 key <key>

it should automatically connect to your network from that point forward.  if all this works let us know and then we have a couple of more changes to make it work after reboots without going through the same process.

----

just a note from an earlier post:  when i wrote sudo ndiswrapper -i net5513.inf, you should be in the same directory as where the driver is stored.  if not you have to give the full path.  also be aware that this is case sensitive.  ndiswrapper seems to be pretty stupid in this regard, and if you make a mistake you'll have to unlink first using sudo ndiswrapper -e net5513  (nonewmsgs, i looked at your earlier post about your prism wireless card, and i think this is where things went wrong.)

---

### Post by josephus on 2007-04-03
i think nonewmsgs may be right about ath0.  I think typically ndiswrappers use wlan0 (for some reason on my installation it automatically remaps it to ath0).  just type iwconfig and see which name comes up.

---

### Post by Zargon2000 on 2007-04-04
Okay, thx.  I did what you said.  When I entered the command "sudo ndiswrapper -i net5513.inf"  I get an "error: ndiswrapper: command not found".

I did a search and found a folder named "ndiswrapper" in 3 places:

/usr/src/linux-headers-2.6.17-10/drivers/net
/usr/src/linux-headers-2.6.17-10-generic/include/config
/lib/modules/2.6.17-10-generic/kernel/drivers/net

I am guessing the command ndiswrapper needs to be installed somehow?  Could you give me the directions for doing this?  Remember I am a TOTAL NooB at this and have only been playing with it for about 2.5 days, so clear step by step is needed. :???: Thanks again for all your help.  I really want to get this up and running, but don't want to do anything to screw it up, as I have already re-installed Ubuntu several times :-)

---

### Post by josephus on 2007-04-04
Sorry about that.  It's hard for me to remember what is already installed from the beginning and what I've added since. If you had a wired connection this would be a lot easier, but anyway ...

I think the best way to install is to download these files and then copy them over to your ubuntu partition:

ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb
[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb)

ndiswrapper-common_1.18-1ubuntu2_all.deb
[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.18-1ubuntu2_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.18-1ubuntu2_all.deb)

in case the links don't work you can find them [http://packages.ubuntu.com](http://packages.ubuntu.com)

If you double click on these packages, a graphical package manager should pop up and ask you if you want to install them.  From the command line use :

sudo dpkg -i <package name>

I think you have to install the common one first, but it'll give you an error message if you go in the wrong order.

---

### Post by Zargon2000 on 2007-04-04
Woo-Hoo!!  :popcorn: **Zargon dances around the room**  :popcorn: 

Thank you thank you thank you!  I now have internet connection!! You said I need to do something to keep the settings after reboot?  What next?

Now what do I do?  Download updates?  

Thanks a million again!!

---

### Post by josephus on 2007-04-04
Good for you! Hope the process wasn't too painful.

I haven't done this myself before, but I think you need to do this to have things load up properly on startup:

```
sudo ndiswrapper -m
```

this adds ndiswrapper to the /etc/modules

you need to also stop ath_hal and ath_pci from loading at boot time by editing /etc/modprobe.d/blacklist

sudo gedit /etc/modprobe.d/blacklist

add

```
blacklist ath_pci
blacklist ath_hal
```

I think the easiest way to save your WEP password is to go into System->Administration->Networking and filling the info in there.  

Anyway, now that you have your internet connection, adding programs and doing updates are quite easy.  Use the Synaptic Package Manager whenever possible, and only compile stuff when you really have to.  If you haven't seen this guide, it was quite helpful to me when I first started:  [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)  . It'll tell you how to do the basic stuff like adding codecs to play movies and mp3s.

---

