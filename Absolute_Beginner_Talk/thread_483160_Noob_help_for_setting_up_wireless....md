---
title: "Noob help for setting up wireless..."
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Justin125 on 2007-06-24
D-Link DWL-G122 

(Revision A2)

I've been searching for pretty much all day yesterday and today... Step-by-step would be nice.'

If this should go in the Wireless and Networking board I'm sorry but I thought here was better because I know next to bare bones and this is BEGINNER board.

---

### Post by shifty_powers on 2007-06-24
well according to [this](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/#d), ndiswrapper, which allows the use of certain windows wireless drivers, supports your card. It's a usb dongle, yes?

Not too up on usb stuff, but you can get ndis by

```
sudo apt-get install ndiswrapper ndisgtk
```

that will then put a menu item in system>administration. You can then use ndiswrapper to install the windows drivers for your usb dongle.

Have a look [here](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) for a bit more info.

---

### Post by Justin125 on 2007-06-24
---
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ndiswrapper
---

I get that when typing that command...

---

### Post by shifty_powers on 2007-06-24
Heh oops. Sorry my mistake.

try

```
sudo apt-get install ndiswrapper-common ndisgtk ndiswrapper-utils-1.9
```

sorry, teach me for not concentrating ;)

---

### Post by Justin125 on 2007-06-24
same thing except ndiswrapper-common instead of ndiswrapper on the bottom line.
:(

---

### Post by shifty_powers on 2007-06-24
interesting.

Could you post the result of

```
cat /etc/apt/sources.list
```

Also, have you tried synaptic?

Go system>preferences>synaptic and search for ndis and install the above three.

Alternatively, you can compile it from source, which isn't as hard as it sounds ;)

Have a look [http://www.psychocats.net/ubuntu/installingsoftware#source](http://www.psychocats.net/ubuntu/installingsoftware#source) - a good site all round really ;)

---

### Post by Justin125 on 2007-06-24
Searching for ndis in Synaptic gives nothing.

Will post the results of that command in a second...

---

### Post by shifty_powers on 2007-06-24
btw, you might want to try [automatix](http://getautomatix.com/wiki/index.php?title=Installation), whcih can do all the hard work for you in this case ;)

Use it meself....

---

### Post by Justin125 on 2007-06-24
[http://i8.tinypic.com/4ys3ltz.png](http://i8.tinypic.com/4ys3ltz.png)

[http://i10.tinypic.com/6gx72go.png](http://i10.tinypic.com/6gx72go.png)

Screenshots for cat /etc/apt/sources.list.

I'll try out that automatix thing right now...

---

### Post by Justin125 on 2007-06-24
bumpity bump

---

### Post by ugm6hr on 2007-06-24
So the first question is - do you have internet access from Ubuntu without the wireless?

If so you should be able to use Synaptic to install *ndisgtk* (which should install everything necessary), which gives a GUI for ndiswrapper (open Synaptic Package Manager and search for ndis).

If not - assuming you have i386 Ubuntu - then you have to go to (and download from):
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb&md5sum=e8876c665294254b55b32c02f629ac78&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb&md5sum=e8876c665294254b55b32c02f629ac78&arch=i386&type=main)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu3_all.deb&md5sum=428a69f0cfa33b978a6ae325772f1aae&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu3_all.deb&md5sum=428a69f0cfa33b978a6ae325772f1aae&arch=all&type=main)
Then just double-click the files in the above order.

This should install a "Windows Wireless Drivers" in System Menu, where you can select the correct .inf (Windows driver).

As for which driver - the wiki linked by shift_powers suggests v3, but that doesn't seem to exist:
Maybe?  [ftp://ftp.dlink.com/Wireless/dwlg122_revA2/Drivers/dwlg122revA2_driver_102.zip](ftp://ftp.dlink.com/Wireless/dwlg122_revA2/Drivers/dwlg122revA2_driver_102.zip)
or?  [ftp://ftp.dlink.co.uk/wireless/dwl-g122/dwl-g122_drv_utility_v1-01.zip](ftp://ftp.dlink.co.uk/wireless/dwl-g122/dwl-g122_drv_utility_v1-01.zip)

---

### Post by shifty_powers on 2007-06-24
Well you seem to have a few things missing from your sources list.

This is what your source list should look like, (or something close)

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free


```

Go to [http://www.psychocats.net/ubuntu/sources#editfile](http://www.psychocats.net/ubuntu/sources#editfile) and follow the instructions from "Backing up and opening the repositories list file".  This will give you all the required repositories. If you have already installed automatix btw, which should be able to install ndiswrapper, keep the automatix repo's.

and then

```
sudo apt-get install ndiswrapper-common ndisgtk ndiswrapper-utils-1.9
```

Oh and apologies for the lateness of the reply, but went out to see me girlfriend ;)

---

### Post by Justin125 on 2007-06-25
> **ugm6hr said:**
> So the first question is - do you have internet access from Ubuntu without the wireless?

If so you should be able to use Synaptic to install *ndisgtk* (which should install everything necessary), which gives a GUI for ndiswrapper (open Synaptic Package Manager and search for ndis).

If not - assuming you have i386 Ubuntu - then you have to go to (and download from):
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb&md5sum=e8876c665294254b55b32c02f629ac78&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb&md5sum=e8876c665294254b55b32c02f629ac78&arch=i386&type=main)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu3_all.deb&md5sum=428a69f0cfa33b978a6ae325772f1aae&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu3_all.deb&md5sum=428a69f0cfa33b978a6ae325772f1aae&arch=all&type=main)
Then just double-click the files in the above order.

This should install a "Windows Wireless Drivers" in System Menu, where you can select the correct .inf (Windows driver).

As for which driver - the wiki linked by shift_powers suggests v3, but that doesn't seem to exist:
Maybe?  [ftp://ftp.dlink.com/Wireless/dwlg122_revA2/Drivers/dwlg122revA2_driver_102.zip](ftp://ftp.dlink.com/Wireless/dwlg122_revA2/Drivers/dwlg122revA2_driver_102.zip)
or?  [ftp://ftp.dlink.co.uk/wireless/dwl-g122/dwl-g122_drv_utility_v1-01.zip](ftp://ftp.dlink.co.uk/wireless/dwl-g122/dwl-g122_drv_utility_v1-01.zip)

You are correct, I have no internet on it at the moment. 

I will follow you're directions right now...

---

shifty_powers:

I'll try that if the person above's solution doesn't work.

---

### Post by Justin125 on 2007-06-25
I got the "Widnows Wireless Drivers" thing to install by downloading and then clicking those files.

I launch the "windows wireless drivers" thing and click install new driver...

I find and select the PRISMA02.inf file...

I get no message back and in the list of 'currently installed' the driver is not mentioned and interwebs is not working.

I go try to install the driver again, then it says it's already installed...

but again I see it nowhere and interwebs not work...

HELP.

---

### Post by anunn2001 on 2007-06-25
I use this device on my old laptop. It doesn't need the ndiswrapper.  Here is a copy on the note I keep to remind me how to setup this device.


linux DWL-122 Setup

Install:  linux-wlan-ng  <------ load this software instead of ndiswrapper

Add the following to /etc/network/interfaces file.

iface wlan0 inet dhcp
wireless_essid MyESSID   <---------  whatever your wireless router is set to.
wireless_key MyWirelessKey  <---------  whatever you setup on the wireless router.

---

### Post by ugm6hr on 2007-06-25
> **anunn2001 said:**
> I use this device on my old laptop. It doesn't need the ndiswrapper.  Here is a copy on the note I keep to remind me how to setup this device.

linux DWL-122 Setup

Is this for vA2 DWL-G122?  There are 4 revisions of this USB adapter - and each has a different chipset.  If it is for vA2 - that sounds easy

---

### Post by ugm6hr on 2007-06-25
> **Justin125 said:**
> I go try to install the driver again, then it says it's already installed...
From memory - ndisgtk is a bit buggy, but it does load the correct driver when selected.

You can check from Terminal:
```
sudo ndiswrapper -l
```
Also - the driver should be in /etc/ndiswrapper

**Before** doing the following - make a backup of* /etc/modprobe.d/blacklist *and [I]/etc/modules
[/I]
The problem may be the native linux prism54usb driver - not certain - but adding blacklist should work:
```
echo 'blacklist prism54usb' | sudo tee -a /etc/modprobe.d/blacklist
```

To run ndiswrapper:
```
sudo ndiswrapper -m
```

Then your computer will need to be rebooted to get those things to happen.  Hopefully it will then work.

As previously linked - this is useful for info: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by shifty_powers on 2007-06-25
ndisgtk certainly is buggy. If anything it is better to work with the cli ndiswrapper.

and the above poster is right, you will need to blacklist the non-functioning driver for your usb dongle in the linux kernel. Sounds like he's got the right command.

```
ndiswrapper -l
```

will indeed tell you which driver has been installed.

Good luck ;)

(and it can work. i had to blacklist the rt61 driver and then install the windows driver through cli but it now works like a charm ;))

---

### Post by Justin125 on 2007-06-25
I type in ndsiwrapper -l and found out that the driver was installed but is 'invaild'. I know why: I forgot to include the .sys file. 

How can I uninstall it so I can install it correctly and follow your steps?

---

### Post by shifty_powers on 2007-06-25
```
ndiswrapper -l
```

Will tell you what the driver is called.

```
sudo ndiswrapper -r driver.inf
```

Replace driver.inf with the output from the first command and that should remove the invalid driver.

Then, make sure that you have downloaded/got on cd the right driver. In the terminal go to the folder with the driver in it

```
cd /home/user/Desktop/driver
```

For example. If you get stuck, go to the folder with the driver in it, right click on a file and click on properties. Highlight and copy then paste it into the terminal after cd and that should do the trick.

Then:

```
sudo ndiswrapper -i driver.inf
```

obviously replacing driver.inf with the right file name. then:

```
ndiswrapper -l
```

To make sure it is installed. Next,

```
sudo ndiswrapper -m
```

Now you need to blacklist the native linux driver.

```
sudo gedit /etc/modprobe.d/blacklist
```

And at the bottom add the name of the native linux driver. Some investigation may be needed to find out which one it is. this will stop the linux kernel calling on the native, non-functioning driver during startup.

that should get you started. When you reboot, network manager should hopefully be able to recognise your windows driver and you'll be able to connect to your network ;)

---

### Post by Justin125 on 2007-06-25
I did everything and checked with ndiswrapper -l and said it was installed.

and rebooted...

Now what?

---

### Post by Justin125 on 2007-06-25
bump

---

### Post by kevdog on 2007-06-25
Good do the following (shouldn't this be posted in the networking forum)

sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

By default ndiswrapper works on the wlan0 interface, and not eth0,eth1, etc. This may cause a problem for you depending on what is in /etc/iftab and /etc/network/interfaces.  

After installation of above reboot.
See after rebooting if you can see your router
iwlist wlan0 scanning

and see the output of 
ifconfig

if wlan0 isnt listed in ifconfig you will need to add it to the interfaces file.  

Post if you have problems.

---

### Post by Justin125 on 2007-06-28
[http://i17.tinypic.com/4l41nro.png](http://i17.tinypic.com/4l41nro.png)

Some parts on this are blanked out because for some reason they show my password...

[http://i19.tinypic.com/4m1sugk.png](http://i19.tinypic.com/4m1sugk.png)

The top part is blanked out because I goofed up the command didn't want to confuse.

---

A picture is worth a thousand words.

Help me my friends.

---

### Post by ugm6hr on 2007-06-28
Post your /etc/modprobe.d/blacklist (you can copy and paste in the forum - just wrap in "CODE" marks - click on the "#" when typing entry.

---

