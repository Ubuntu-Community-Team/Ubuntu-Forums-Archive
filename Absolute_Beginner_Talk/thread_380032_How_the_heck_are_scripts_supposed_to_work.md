---
title: "How the heck are scripts supposed to work"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by goofeyfoot on 2007-03-09
How the heck are scrips supposed to work.

I downloaded a tar file.  Here is excerpt from the instructions.  

The driver is composed of several parts:

	1. Module source code

	  stack.tar.gz

	  drv.tar.gz

	

	2. Script ot build the modules

	  makedrv



	3. Script to load/unload modules

	  wlan0up

	  wlan0down 



	4. Script and conf
iguration for DHCP

 	  wlan0dhcp

	  ifcfg-wlan0

	4. Supplicant source code:

	  wpa_supplicant-0.4.9.tar.gz



	5. Example of supplicant configuration file:

	  wpa1.conf



< Installation >

Runing the scripts can finish all operations of building up modules 

from the source code and start the nic.

	1. Build up the drivers from the source code

	  ./makedrv



	2. load the driver module to kernel and start up nic

	  ./wlan0up

Like everything in Linux, the problems occur right off the bat.  Trying to run the mkdrv thing here is the junk that got spit out from the terminal when I cut and pasted the language in:

michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ #!/bin/sh
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ 
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ tar -zxvf stack.tar.gz
ieee80211/
ieee80211/.tmp_versions/
ieee80211/.tmp_versions/ieee80211-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
ieee80211/ieee80211.h
ieee80211/ieee80211_crypt.c
ieee80211/ieee80211_crypt.h
ieee80211/ieee80211_crypt_ccmp.c
ieee80211/ieee80211_crypt_tkip.c
ieee80211/ieee80211_crypt_wep.c
ieee80211/ieee80211_module.c
ieee80211/ieee80211_rx.c
ieee80211/ieee80211_softmac.c
ieee80211/ieee80211_softmac_wx.c
ieee80211/ieee80211_tx.c
ieee80211/ieee80211_wx.c
ieee80211/license
ieee80211/Makefile
ieee80211/Modules.symvers
ieee80211/readme
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ tar -zxvf drv.tar.gz
beta-8187/
beta-8187/r8180_hw.h
beta-8187/r8187.h~
beta-8187/r8180_rtl8225.h
beta-8187/license
beta-8187/.tmp_versions/
beta-8187/.tmp_versions/r8187.mod
beta-8187/Makefile
beta-8187/r8180_93cx6.c
beta-8187/tags
beta-8187/authors
beta-8187/r8187_core.c~
beta-8187/r8180_pm.h
beta-8187/r8180_rtl8225.c
beta-8187/copying
beta-8187/r8180_wx.h
beta-8187/Modules.symvers
beta-8187/r8180_rtl8225z2.c
beta-8187/readme
beta-8187/r8187_core.c
beta-8187/ieee80211.h
beta-8187/r8180_93cx6.h
beta-8187/changes
beta-8187/r8187.h
beta-8187/r8180_pm.c
beta-8187/install
beta-8187/ieee80211_crypt.h
beta-8187/r8180_wx.c
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ cd ieee80211
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006/ieee80211$ make clean
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /tmp/rtl8187_linux_26.1010.0622.2006/ieee80211/tmp
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006/ieee80211$ make
make -C /lib/modules/2.6.17-11-generic/build M=/tmp/rtl8187_linux_26.1010.0622.2006/ieee80211 modules
make: *** /lib/modules/2.6.17-11-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006/ieee80211$ cd ../beta-8187
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006/beta-8187$ make clean
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /tmp/rtl8187_linux_26.1010.0622.2006/beta-8187/tmp
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006/beta-8187$ make
make -C /lib/modules/2.6.17-11-generic/build M=/tmp/rtl8187_linux_26.1010.0622.2006/beta-8187 modules
make: *** /lib/modules/2.6.17-11-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006/beta-8187$ cd ..
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ 
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ 
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ 
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ 
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ 
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ 

Can someone tell me in plain English what I am doing wrong.  Jeez I have been screwing around trying to get this going for a week now.

Thanks.

Michael

---

### Post by Crooksey on 2007-03-09
What are you trying to install?

---

### Post by Xoanan on 2007-03-09
> **Crooksey said:**
> What are you trying to install?
From the sounds of it, the user is attempting to load a new kernel for a nic(ethernet card).  I h ad trouble with that on old Red Hat 6.  Unfortunatly, I do not know how to help on this one.

---

### Post by Crooksey on 2007-03-09
Its probably failing as you dont have the source/headers installed or something like that.

Are there no deb files for what you are wanting to install?

---

### Post by Famicommie on 2007-03-09
I could be wrong, but it seems to me as though he's trying to compile ndiswrapper from source. It's something that I had to do in order to get my fancy wifi card working. Deb files and the repositories weren't able to help me (and unfortunatly, I have to recompile ndiswrapper every time that there's a kernel update).

But yeah, goofeyfoot, before getting all worked up about how "nothing in Linux ever works", calmly tell us what it is that you are trying to compile.

---

### Post by goofeyfoot on 2007-03-09
This is a Realtek wifi driver which Realtek puts out on their own website.  I think the model of the wifi iis rtl8187L.  I'm at work but I think that's the number as I remember it.

The driver is for AMD64 and Realtek says on their site that the particular driver is supposed to work with Linnux.  I think the last distribution they explicitly mentioned on the site was "Dapper."  But I had to try it anyway (even though I have Ubuntu 6.10) because I couldn't find anything else close.

By the way, the system detects the card correctly and identifies it by model number.  But there is no driver showing and I verified through troubleshooting that there is no connection to the router.  The troubleshooting literature I was reading indicated that there's no driver.  When you run lshw (or whatever that's called" you see the wifi but no driver. 

The motherboard is NVidia chip and is made by Asus.

So the download comes as a zip file that I extracted.  There were .tar files included in that extraction.  The readme file said to run the scripts to do the install so I did. At least I thought I did. The relevant portion of the readme is quoted in my post.

 I started out on the desktop and went to the "terminal" thing.  I pasted the scripts in the terminal.

Like I said there were two scripts.   One script was apparently for creating the drivers and the other script was supposedly for installing the drivers on the wi-fi.  The quote you see in my post pertains to the first script which was called something like "mkdrv," or something to that effect.

As you can see from the text, nothing worked on the first script.  The errors are marked in the quotation.

I did try and run the second script and it puked out pretty much the same type of errors.  It didn't work.

So I guess the question is how the heck can I try to install these drivers?

Michael

---

### Post by Tomosaur on 2007-03-09
> **goofeyfoot said:**
> 
Like everything in Linux, the problems occur right off the bat.  Trying to run the mkdrv thing here is the junk that got spit out from the terminal when I cut and pasted the language in:

michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ #!/bin/sh
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ 
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ tar -zxvf stack.tar.gz
ieee80211/
ieee80211/.tmp_versions/
ieee80211/.tmp_versions/ieee80211-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
ieee80211/ieee80211.h
ieee80211/ieee80211_crypt.c
ieee80211/ieee80211_crypt.h
ieee80211/ieee80211_crypt_ccmp.c
ieee80211/ieee80211_crypt_tkip.c
ieee80211/ieee80211_crypt_wep.c
ieee80211/ieee80211_module.c
ieee80211/ieee80211_rx.c
ieee80211/ieee80211_softmac.c
ieee80211/ieee80211_softmac_wx.c
ieee80211/ieee80211_tx.c
ieee80211/ieee80211_wx.c
ieee80211/license
ieee80211/Makefile
ieee80211/Modules.symvers
ieee80211/readme
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ tar -zxvf drv.tar.gz
beta-8187/
beta-8187/r8180_hw.h
beta-8187/r8187.h~
beta-8187/r8180_rtl8225.h
beta-8187/license
beta-8187/.tmp_versions/
beta-8187/.tmp_versions/r8187.mod
beta-8187/Makefile
beta-8187/r8180_93cx6.c
beta-8187/tags
beta-8187/authors
beta-8187/r8187_core.c~
beta-8187/r8180_pm.h
beta-8187/r8180_rtl8225.c
beta-8187/copying
beta-8187/r8180_wx.h
beta-8187/Modules.symvers
beta-8187/r8180_rtl8225z2.c
beta-8187/readme
beta-8187/r8187_core.c
beta-8187/ieee80211.h
beta-8187/r8180_93cx6.h
beta-8187/changes
beta-8187/r8187.h
beta-8187/r8180_pm.c
beta-8187/install
beta-8187/ieee80211_crypt.h
beta-8187/r8180_wx.c
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ cd ieee80211
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006/ieee80211$ make clean
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /tmp/rtl8187_linux_26.1010.0622.2006/ieee80211/tmp
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006/ieee80211$ make
make -C /lib/modules/2.6.17-11-generic/build M=/tmp/rtl8187_linux_26.1010.0622.2006/ieee80211 modules
make: *** /lib/modules/2.6.17-11-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006/ieee80211$ cd ../beta-8187
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006/beta-8187$ make clean
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /tmp/rtl8187_linux_26.1010.0622.2006/beta-8187/tmp
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006/beta-8187$ make
make -C /lib/modules/2.6.17-11-generic/build M=/tmp/rtl8187_linux_26.1010.0622.2006/beta-8187 modules
make: *** /lib/modules/2.6.17-11-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006/beta-8187$ cd ..
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ 
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ 
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ 
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ 
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ 
michael@Michael:/tmp/rtl8187_linux_26.1010.0622.2006$ 

Can someone tell me in plain English what I am doing wrong.  Jeez I have been screwing around trying to get this going for a week now.

Thanks.

Michael

Why are you c+ping the script file? You're supposed to just run it. Open up a file browser, double click on the script file, and select 'run in terminal'.

---

### Post by goofeyfoot on 2007-03-09
Hello:

I tried to do what you said but when I did, the terminal thing flashed up quick, closed and then nothing happened.  So figured it got spit out just the same.

Suppose you do the terminal click thing that you mention.  If the terminal closes down, as it did, how could you find out if anything actually got changed?

This seems to be one of the problems getting going with Linux from scratch.  You can't learn it until you get it running, and you can't get it running without first learning it.  A chicken and egg dillemma.:)

---

### Post by jkeyes0 on 2007-03-09
Are you using dapper, or edgy? If you're using edgy, you might have to edit the script files and change that first line from #!/bin/sh to #!/bin/bash

---

### Post by aeiah on 2007-03-09
maybe the [instructions here](http://ubuntuforums.org/showthread.php?t=293072) will help you. they may be a bit clearer.

you'll need your kernel headers and whatnot. im at work also so dont really have time to look things up. the guy in the link i posted seems to have lock-up problems with his, but this was a while ago and hopefully the drivers are more compatible now

---

### Post by goofeyfoot on 2007-03-09
To answer the previous two posts I am using 6.10.  As far as the other point, I really don't know what "headers" and such are.

---

### Post by goofeyfoot on 2007-03-09
Got home from work and tried the method in the link.

No go.

I didn't do anything about headers because I don't know what that is.

Does anyone have any information about this?

Michael

---

### Post by goofeyfoot on 2007-03-10
OK I am totally baffled as to what to do next.

Plainly I cannot get this wifi card to work.

From what I have read online the best thing to do is to bring the Windows 98 drivers over to Linux.  So that is what I want to do.

Is there someone who can give me an intelligible explanation as to how to do this?

Hopefully someone can put this into a format that someone can understand.  Right now I am literally standing on about 120 pages of printouts from about a dozen sources as to how to get this done.  

Got to tell you it doesn't help when people stick links up that leave out the gory details of how to do this install.  The stuff I have read online thus far leaves out a lot of details that may seem obvious to experts but certainly not to new people.

I am pretty aggravated.  Been messing with this operating system for going on three weeks now and have not accomplished anything.

Thanks for reading.

Michael

---

### Post by Famicommie on 2007-03-10
I would suggest using ndiswrapper. There is a complete guide at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

Give that a shot, and if you encounter any errors, please post them right away.

---

### Post by goofeyfoot on 2007-03-10
No go.

I installed the windows 98 drivers twice and it does not work.

I am at the end of my wits with this thing.  Sorry but it has taken three weeks to get ubuntu to run, for unrelated reasons.  And already I have wasted a week trying to get this wireless to run.

I really need someone who has the similar equipment to tell me what to do.  Seems like if one piece of hardware is different nothing works.

Thanks.

Michael

---

### Post by Famicommie on 2007-03-10
What wireless card do you have in there?

---

### Post by goofeyfoot on 2007-03-11
Fammie Commie  See post number 6 for the details concerning my system.

Thanks for your attention.

Michael

---

### Post by Famicommie on 2007-03-12
I think that you may be trying to run the compile script as a regular user, and thusly are being denied permissions to create certain directories. Try running the compile script again, but this time use the command
```
sudo -i
```
which will give you a shell with root access.

---

### Post by goofeyfoot on 2007-03-12
Hello again:

Well let's see.

When I did my "thing" with the win 98 drivers, I do remember putting sudo before several commands to make them go in.

I also recall that when I did that, on many occasions I was asked for my password and had to put it in before I could proceed.

In addition, I read about a way, which I have since forgotten, that allows you to verify that drivers are installed.  When I did that, I saw proof that the win 98 drivers did go in.  The only thing I noted to be amiss was that, while the name of the driver appeared on the "list" there was no way to be sure that the driver was specifically assigned to the wireless adapter.  Point is though, that the driver did install some place.

To conclude, I don't disagree with your analysis except to say that I believe I got the sudo thing correct, albeit in a different way.

As a  point of interest, what is "compiling"?  Is that what I was doing?  How is the word defined?

Also, someone in a post said I was supposed to set up headers.  Don't believe I ever did that unless the procedure I followed constitutes that.

Also, what is "sudo i"?  Does that make it so that you don't have to keep writing "sudo" all the time?

Anyway, in the final analysis, I believe I installed the driver with no success.  Can't say whether the driver got to the right device though.

If you have more suggestions, I would appreciate them because I really can't use Ubunto without being able to connect wirelessly.

Thanks for reading.

Michael

Thanks again.

Michael

---

### Post by Famicommie on 2007-03-13
Well, first, let's see what you can do with ndiswrapper.

Before anything else, check the [list](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) to see what drivers have been tested for your card. Make sure that you are using drivers that've been reported with success. That list is pretty good about linking to the necessary drivers, too.

The command ```
ndiswrapper -l
``` will give you a list of any installed ndiswrapper drivers, and which devices (if any) they correspond to. You can find the address of your wireless card with two steps.

1. Enter the command ```
lspci
``` at a terminal and locate the wireless card. Make a note of the characters in the first column. The format will be XXXX:XX:XX.X
2. Enter the command ```
lspci -n
``` and look for the number you got from step 1. In the third column you will find the PCI ID (format XXXX:XXXX) Make a note of the PCI ID as well.

Now, to check and see whether or not the drivers you've installed are corresponding to your device, enter the command ```
ndiswrapper -l
```. That command will tell you which drivers are installed, and whether or not the device is presently detected. If all is looking good, then enter the command ```
ndiswrapper -a pciid driver
```, replacing the term pciid with the PCI ID number that you took a note of earlier, and the term driver with the name of the driver.

Then, set your ESSID and your WEP key (use hex), activate the device, and open up a terminal to issue the command ```
sudo dhclient
```

Now, for your other questions.

Compiling is the act of taking a "high level" programming code and converting it to a "low level" programming code. It turns the "source code" into "object code". You never really have to compile on Windows because most applications are precompiled (but if they aren't compiling on Windows is 10,000x worse than trying to set up wifi in linux).

"sudo -i" means "give me an administrator shell". That way, you don't have to precede each command with "sudo" if you plan on doing some heavy administrative work. I was suggesting that you retry compiling the linux realtek drivers (not ndiswrapper) while running as root. If you can't get ndiswrapper to work after some more tinkering around, go for the linux drivers again *as root*

---

### Post by goofeyfoot on 2007-03-13
OK, I will try this when I get home.

One question, in step 2 you have the following:

ndiswrapper -a pciid driver

To my untrained eye that looks like it might apply to a wireless card which is physically located on a pci slot.

My built in Realtek 8187 (a wireless card notorious for problems from what appears on the internet) is supposedly a "USB" port card.  Physically, I don't see it on a port because it is built in.  But somehow it must run off an internall USB bus or something.

The question is, do you still have to give the same "pciid" command, or does the "pciid" command become something else in an internal usb situation?

Parenthetically let me say that I have already seen a couple posts where the lucky user got 8187 to run using the Win 98 driver.  That apparently didn't work in my case.

Thanks for your interest in the situation and your many posts.

Michael

---

### Post by Famicommie on 2007-03-13
instead of doing the lspci/lspci -n dance, the only command that you will have to use is
```
lsusb
```

Replace any instance of the PCI ID with the USB ID.

See, I had major headaches and frustrations trying to set up my wifi card, too. The card was detected, had the appropriate drivers installed and correlated via ndiswrapper, and I was using the right ESSID and hex key. But I still couldn't connect. I knew that my card was strong enough to reach the router two floors down because I was using a laptop with a smaller wifi device to get internet access.

At the suggestion of someone in the Ubuntu irc channel, I installed a program called "gnome network manager", and noticed that the only network I could see was my neighbor's (who lived two houses away!). The helpful IRC dweller told me to change the channel of my router, correctly guessing that we were sharing the same channel number. Changed the channel of my router, and miracously saw my own wireless network. Tried to connect with the network-manager applet, and still had no success. However, after closing out the network-manager applet and using the system network settings, I finally managed to connect right up.

So, I know **exactly** how frustrating it is to try and set up wifi on linux.

---

### Post by goofeyfoot on 2007-03-15
Ok: 

Here is an update regarding the latest attempt to get this wifi going.

First, I took your advice about the ndiswrapper thing.  I ran the commands as best I could.  It is a usb setup so I guess some commands are a little different.

Anyway, when all was said and done, the 98 Windows driver was already in place.  And, as I have stated before, I can detect nothing in terms of wireless networks.

I tried the compile thing but I must have screwed that up because when I was trying to run the "makedrive" and other scripts all I got was a bunch of gobbldegook about "directory not found" and similar.  I have pages of printed out messages.  Can't send them because I don't have any way to email from Ubuntu.  The short story seems to be that I was in the wrong place at the wrong time because during compiling all I got was file not found and things like that.

So two things are clear.  The Wind 98 driver ain't ever going to work.  It is apparently already installed and it doesn't do jack.

As far as compiling the Linux drivers, I have no clue as to how to do that, how to get to the correct file in the structure, etc.  So that isn't going to work.  Unless of course I learn how to use Linux...oh that's right I can't do that until I get the wireless working within Linux...and I can't do that unless I learn Linux.  Hmmmm, sort of like going around in circles here.

Thanks for reading.

Michael

---

### Post by coffeeadikt on 2007-03-15
I don't want to pass on too much hearsay, especially since this isn't good news:

Do a little more research on your wifi card. 

A friend of mine is currently going through the same problem and he just told me that it turns out Netgear W111gv2 comes on two different chips. One is made by Realtek and the Linux drivers work. The other isn't and the drivers don't work.

I don't know how he found that out though.

He's going to end up buying a new wireless card, and that's a sucky introduction to Linux.

If I find out specifics I'll come back and post them here. 

Best of luck to you Michael.

---

### Post by goofeyfoot on 2007-03-15
Thanks for the update.  If I know that the card won't work, it certainly will be disappointing, but it is better to find out than to waste a lot of time looking for a fix that doesn't exist.

Thanks again.

Michael

---

### Post by Famicommie on 2007-03-16
Well, if you can detect the card, and the proper drivers are installed via ndiswrapper, then you are at least on the right track.

Try installing the network-manager-GNOME before you completely give up hope. See if it will even detect any wireless networks. You can find the edgy debian files here: [http://packages.ubuntu.com/edgy/net/network-manager-gnome](http://packages.ubuntu.com/edgy/net/network-manager-gnome)

To install a debian file, simply double click it and it should finish the rest on its own.

---

### Post by goofeyfoot on 2007-03-16
OK Fannie Commie I will give that a shot tonight.

Also, I read a guidebook about "using the shell" that I found on line and it looks the linux driver didn't work through the script method because in my compiling attempt I didn't use some instruction - something along the lines of "chmod" or similar.

The guide as pretty good overall in terms of giving the jargon terms in simple explanations, and hey, I ain't got a wireless card that works so there's definitely some spare time available for reading.

I had one other idea last weekend too.  It just so happens that I have an extra wireless router kicking around.  I was wondering whether it would be possible to simply work around the wireless in the Ubuntu machine this way.  My new router would remain the gateway as it is now.  The spare router, which would be a client on the network would in turn get hooked directly into the Ubunto computer.  Then, I could get my internet signal through the spare router instead of the wireless - at least until Realtek programs a new driver.  Don't know if any of this is possible or how to do it.

Lastly, I am going to write to Realtek to see whether they have any better solutions.  Seems like they would address the question just as a matter of good PR.

Thanks again for your advice.

Michael

---

### Post by goofeyfoot on 2007-03-16
Here is the update.

I put Network Manager in.  Only it doesn't do anything.  All it does is put a little network icon on the taskbar.  That icon goes to a regular wired ethernet connection - ie the cable that now runs all across the living room floor since I can't connect wirelessly.

The Network Manager must have something wrong with it.  There doesn't appear to be an application that you can run - just the icon that references the wired connection.  I have installed the Network Manager application at least three times with no different result.

The windows driver application does show that the Win 98 driver is indeed installed.  So that must be ok.   For some reason I can't sniff a network with this Realtek wireless card.

I wrote to Realtek about the problem and no word so far.

Thanks.

Michael

---

### Post by goofeyfoot on 2007-03-16
Ok to summarize:

Network Manager is a dead duck

Ndiswrapper is a dead duck.

Now for the Linux stuff.

Here are some cryptic directions as to how to configure the Realtek drivers for Linux.

I have no idea what this is trying to say.  The grammar is pretty bad on top of it.

Here goes:

"Release Date: 2006-01-13, ver 1.1

RTL8187 Linux driver version 1.1



   --This driver supports RealTek RTL8187 Wireless LAN driver for 

     Fedora Core 2/3/4/5, Debian 3.1, Mandrake 10.2/Mandriva 2006, 

     SUSE 9.3/10.1/10.2, Gentoo 3.1, etc.

   - Support Client mode for either infrastructure or adhoc mode

   - Support WEP and WPAPSK connection



< Component >

The driver is composed of several parts:

	1. Module source code

	  stack.tar.gz

	  drv.tar.gz

	

	2. Script ot build the modules

	  makedrv



	3. Script to load/unload modules

	  wlan0up

	  wlan0down 



	4. Script and configuration for DHCP

 	  wlan0dhcp

	  ifcfg-wlan0

	4. Supplicant source code:

	  wpa_supplicant-0.4.9.tar.gz



	5. Example of supplicant configuration file:

	  wpa1.conf



< Installation >

Runing the scripts can finish all operations of building up modules 

from the source code and start the nic.

	1. Build up the drivers from the source code

	  ./makedrv



	2. load the driver module to kernel and start up nic

	  ./wlan0up



< Set wireless lan MIBs >

This driver uses Wireless Extension as an interface allowing you to set

Wireless LAN specific parameters.



Current driver supports "iwlist" to show the device status of nic

        iwlist wlan0 [parameters]

where

        parameter explaination      	[parameters]    

        -----------------------     	-------------   

        Show available chan and freq	freq / channel  

        Show and Scan BSS and IBSS 	scan[ning]          

        Show supported bit-rate         rate / bit[rate]        

        Show Power Management mode      power             



For example:

	iwlist wlan0 channel

	iwlist wlan0 scan

	iwlist wlan0 rate

	iwlist wlan0 power



Driver also supports "iwconfig", manipulate driver private ioctls, to set

MIBs.



	iwconfig wlan0 [parameters] [val]

where

	parameter explaination      [parameters]        [val] constraints

        -----------------------     -------------        ------------------

        Connect to AP by address    ap              	[mac_addr]

        Set the essid, join (I)BSS  essid             	[essid]

        Set operation mode          mode                {Managed|Ad-hoc}

        Set keys and security mode  key/enc[ryption]    {N|open|restricted|off}



For example:

	iwconfig wlan0 ap XX:XX:XX:XX:XX:XX

	iwconfig wlan0 essid "ap_name"

	iwconfig wlan0 mode Ad-hoc

	iwconfig wlan0 mode essid "name" mode Ad-hoc

	iwconfig wlan0 key 0123456789 [2] open

	iwconfig wlan0 key off

	iwconfig wlan0 key restricted [3] 0123456789



< Getting IP address >

After start up the nic, the network needs to obtain an IP address before

transmit/receive data.

This can be done by setting the static IP via "ifconfig wlan0 IP_ADDRESS"

command, or using DHCP.



If using DHCP, setting steps is as below:

	(1)connect to an AP via "iwconfig" settings

		iwconfig wlan0 essid [name]	or

		iwconfig wlan0 ap XX:XX:XX:XX:XX:XX



	(2)run the script which run the dhclient

		./wlan0dhcp

           or 

		dhcpcd wlan0

              	(Some network admins require that you use the

              	hostname and domainname provided by the DHCP server.

              	In that case, use 

		dhcpcd -HD wlan0)

		

< WPAPSK >

WPA_SUPPLICANT help the network to communicate under the protection of WPAPSK

mechanism

	

	(1)Unpack source code of WPA supplicant:

	  tar -zxvf wpa_supplicant-0.4.9.tar.gz

	  cd wpa_supplicant-0.4.9

	

	(2)Create .config file:

	  cp defconfig .config

	

	(3)Edit .config file, uncomment the following line:

	  #CONFIG_DRIVER_IPW=y.

		

	(4)Build WPA supplicant:

	  make

	If make error for lack of <include/md5.h>, install the openssl lib(two ways):

	 1. Install the openssl lib from corresponding installation disc:

	    Fedora Core 2/3/4/5(openssl-0.9.71x-xx), Mandrake10.2/Mandriva10.2(openssl-0.9.7x-xmdk),

	    Debian 3.1(libssl-dev), Suse 9.3/10.0/10.1(openssl_devl), Gentoo(dev-libs/openssl), etc.

	 2. Download the openssl open source package from [www.openssl.org](www.openssl.org), build and install it.

	 

	(5)Edit wpa_supplicant.conf to set up SSID and its passphrase.

	  For example, the following setting in "wpa1.conf" means SSID 

          to join is "BufAG54_Ch6" and its passphrase is "87654321".

	  network={

			ssid="BufAG54_Ch6"

			proto=WPA

			key_mgmt=WPA-PSK

			pairwise=CCMP TKIP

			group=CCMP TKIP WEP104 WEP40

			psk="87654321"

			priority=2

		  }



	(6)Execute WPA supplicant (Assume 8187 and related modules had been

           loaded):

	  ./wpa_supplicant -D ipw -c wpa1.conf -i wlan0 &"

Like I said, I don't know what this is trying to say.  All I can tell you is the  business about the scripts  doing anything automatically is  way overstated.  I pasted the  scripts into the terminal and nothing but junk go t  spit out.

Does any one know how this works?

Thanks.

Michael

---

### Post by goofeyfoot on 2007-03-19
Here is a possible avenue of escape from the Realtek 8187 internal wireless debacle.

I did write to Realtek and I got back a letter that reads as follows from the support guy.

"Dear Sir,

Thanks for your e-mail.

Attached file please find 8187 latest linux package which able to support Ubuntu 6.06.

If you have any questions, please let us know.

Regards,

Fred"

The file the guy sent me looked pretty new.  It was called rtl8187_linux_26.1024.0209.2007.  So I would assume that the thing was made in February 2007.

Anyway, I tried to set up the driver, but I couldn't set it up right because I don't know very much about Linux and I don't know how to run scripts etc. Thus the name of this thread.

So, hopefully there is someone out with a 8187 Realtek card  who can check out this new driver and let me know if you are lucky enough to get it working.

Take care.

Michael

---

