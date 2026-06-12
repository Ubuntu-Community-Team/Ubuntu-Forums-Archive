---
title: "Averatec 2300 Series Wireless problem"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by Ru$$i@N on 2007-09-05
Hi everyone.

I've recently bought an Averatec 2300 Series laptop, and everything seems to work fine, except for the built-in wireless card. :mad:

I've searched the forum over and over again, but couldn't find a solution. The "Averatec Guide" didn't help either. 

The thing is, I used to be able to "see" wifi networks (before I messed with drivers and such), but I couldn't connect to them. WEP, WPA, no protection at all - no connection.

The default driver that Ubuntu was using was rt73usb. I'm running 7.04 x64.

ANY help is appreciated.

---

### Post by SpiritIsReality on 2007-09-05
howdy

until someone who knows shows up, you could maybe post here,
[http://ubuntuforums.org/showthread.php?t=538357](http://ubuntuforums.org/showthread.php?t=538357)
seems to be on the right track.
edit:another thread here
[http://ubuntuforums.org/showthread.php?t=436673](http://ubuntuforums.org/showthread.php?t=436673)

some searches used to find the above post, you might find something
more here, linuxquestions.org...
[http://www.google.ca/search?hl=en&q=linux+Averatec+2300+wireless+chip&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+Averatec+2300+wireless+chip&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+Averatec+2300+wireless&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+Averatec+2300+wireless&btnG=Google+Search&meta=)
[http://www.google.com/custom?hl=en&client=pub-7825705102693166&channel=3833691868&cof=FORID%3A1%3BAH%3Aleft%3BCX%3ALinux%2520search%2520Engine%3BL%3Ahttp%3A%2F%2Fwww.google.com%2Fcoop%2Fimages%2Fgoogle_custom_search_sm.gif%3BLH%3A55%3BLP%3A1%3BGFNT%3A%23666666%3BDIV%3A%23cccccc%3B&adkw=AELymgWCYihOXCCUgdgRIebUghRaXzNpx7S9kwmEK6alBc2xg85Ws3WyL-c2WYa7B5Qy37jWMbdUDGeklJ50sQBJGn9erkF4ipDYtuIiqXI5NBRw4SQlk2mN0ngAcwBrg1IY2ejGx8yXIiHbYdePrFjaNqrtgy3OX_v41eVDZHylMD_8FUo4pt1V_XWYrYjHSWslLySxhfzQXa0ub_Rp3yzyoEPxcVK6xg&q=linux+Averatec+2300+wireless+card&btnG=Search&cx=002165917076592449621%3Ay8jmiivon3o](http://www.google.com/custom?hl=en&client=pub-7825705102693166&channel=3833691868&cof=FORID%3A1%3BAH%3Aleft%3BCX%3ALinux%2520search%2520Engine%3BL%3Ahttp%3A%2F%2Fwww.google.com%2Fcoop%2Fimages%2Fgoogle_custom_search_sm.gif%3BLH%3A55%3BLP%3A1%3BGFNT%3A%23666666%3BDIV%3A%23cccccc%3B&adkw=AELymgWCYihOXCCUgdgRIebUghRaXzNpx7S9kwmEK6alBc2xg85Ws3WyL-c2WYa7B5Qy37jWMbdUDGeklJ50sQBJGn9erkF4ipDYtuIiqXI5NBRw4SQlk2mN0ngAcwBrg1IY2ejGx8yXIiHbYdePrFjaNqrtgy3OX_v41eVDZHylMD_8FUo4pt1V_XWYrYjHSWslLySxhfzQXa0ub_Rp3yzyoEPxcVK6xg&q=linux+Averatec+2300+wireless+card&btnG=Search&cx=002165917076592449621%3Ay8jmiivon3o)

my experience with laptops and linux is limited to a toshiba satellite 2140xcds
and a blacklist of the kernel drivers and using ndiswrapper got the linksys 
wireless card working for it.
ndiswrapper home here, and article at wikipedia.org
[http://www.google.ca/search?hl=en&q=ndiswrapper&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=ndiswrapper&btnG=Google+Search&meta=)
edit: blacklist
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=blacklist&fullsearch=Text](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=blacklist&fullsearch=Text)

trails

---

### Post by Ru$$i@N on 2007-09-05
Thanks, it seems like that one guy got his wireless working (somewhat) through ndiswrapper. But I still don't understand how to get mine working.

Thanks for the reply.

---

### Post by Ru$$i@N on 2007-09-05
I tried the Averatec 2370/2300 Guide again, AND GOT THE UNPROTECTED WIRELESS WORKING!!! Don't know about WEP and WPA yet. 

So here's how I got it:

Well, first, I'm using Ubuntu 7.04 Feisty Fawn x64. I have Averatec 2300 series, AMD Turion 64 X2, built-in wireless (original), i think the chipset is rt73 (not sure).

**THANKS to dragonfyre13 and his guide!!! dragonfyre13, you're the man.**
All credits to dragonfyre13, i just changed the driver, and it worked for me.

**Step 1 - Disable Competing Driver**

You need to blacklist the existing rt73 module which is not working:
```
sudo gedit /etc/modprobe.d/blacklist
```

add the following three lines to the end of the file:
> # Added when rt73 module was installed
blacklist rt73usb
blacklist rt2570
Save the file. The blacklisted module will not be loaded from now on.

**Step 2 - Prepare the Linux build environment**

You will need to install the essential build files to compile the driver:
```
sudo apt-get update  
sudo apt-get install build-essential
```

Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.)
```
sudo apt-get install linux-headers-`uname -r`  
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
```

**Step 3 - Download the rt73 driver**

********* here's what I've changed a bit, I changed RT73_Linux_STA_Drv**1.0.3.6**.tar.gz to RT73_Linux_STA_Drv**1.0.4.0**.tar.gz
```
wget http://www.ralinktech.com.tw/data/RT73_Linux_STA_Drv1.0.4.0.tar.gz
```

**Step 4 - Extract and prepare the archive**

Using tar extract the archived driver and change directories into the build area.
```
tar xvzf RT73_Linux_STA_Drv1.0.4.0.tar.gz  
cd RT73_Linux_STA_Drv1.0.4.0/Module
```

The permissions are not correct on the files, so change them to 755 using chmod:
```
chmod -R 775 *
```

Copy the Makefile.6 file into the Makefile to prepare for a 2.6 Linux kernel build:
```
cp Makefile.6 Makefile
```

**Step 5 - Create and install the driver using make**

Make the driver with the make command:
```
make clean
make
```

This will take several minutes. There will be warnings, but there can be **no errors** or the build will not complete.

Using sudo make install we install the complete driver into the "extra" directory of your kernel modules:
```
sudo make install
```

Verify that the driver was installed correctly using the list short command:
```
ls /lib/modules/`uname -r`/extra
```

You should see the file rt73.ko

Create the directories necessary for storing the firmware for the driver:
```
sudo mkdir /etc/Wireless 
sudo mkdir /etc/Wireless/RT73STA
```

Copy the rt73.bin file into the newly created firmware directory:
```
sudo cp rt73.bin /etc/Wireless/RT73STA
```

Now, create the new rt73sta.dat file. No, you are not copying over the one in the source directory. (This solves the issues I was having with WEP Keys)
```
sudo gedit /etc/Wireless/RT73STA/rt73sta.dat
```

Now, paste the following into the open window:
> [Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
NetworkType=Infra

**Step 6 - Configure the network settings for the rt73 device**

Using the Text Editor (gedit) we need to modify the interfaces file to get the device started correctly:
```
sudo gedit /etc/network/interfaces
```

And put this in:
> auto rausb0
iface rausb0 inet dhcp
********* I also did this:
> #auto wlan0
#iface wlan0 inet dhcp
Don't know if I was supposed to
 do that, or even if it does anything. ***********

**Step 7 - Reboot your system**

Do a system reboot.

**Step 8 - Testing the device**

In a terminal window run iwconfig and you should see the device as rausb0.
```
iwconfig
```

Your output should contain a line that has a record for the device rausb0, similar to this one:
> rausb0 RT73 WLAN ESSID:"MY_ESSID"
Mode:Managed Frequency=1 MHz Access Point: 00:08:74:02:01:FC
Bit Rate=54 Mb/s
RTS thr: off Fragment thr: off
Link Quality=100/100 Signal level:-28 dBm Noise level:-79 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
In this example we know that the access point with the ESSID "MY_ESSID" has been found, because we can see that the "Access Point:" field has been filled in with the access point's MAC identifier. Don't worry if this isn't in there yet, because it means it didn't find an unsecured network to connect to.

Note that the Frequency may be listed as 1 MHz, but this is actually the channel number, this is a feature of the present driver implementation.

If your network essid isn't showing up, skip to step 10, and come back. Run iwconfig again, and it should show the correct essid, and an associated access point.

Run a "netstat -rn" command, and you should see that the correct routing is setup:
```
netstat -rn
```

The output should be similar to this example:
> Kernel IP routing table
Destination Gateway Genmask Flags MSS Window irtt Iface
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 rausb0
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 rausb0
In this case 192.168.1.1 is the gateway address to an Internet router.

**Step 9 - Controlling the device**

You can now control the device with ifup and ifdown:
```
sudo ifdown rausb0 
sudo ifup rausb0
```

**Step 10 - Using a Graphical Tool To Manage The Network**

****** The "Connection Manager" is now "Wicd". You can easily find the information you need at [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")  *********

PS. So far I'm still using **network manager**, and my wireless card shows up as **Wired Network (Unknown USB Vendor Specific Interface)**....... but it works with unprotected wireless networks, takes a minute to connect though... :)

---

### Post by SpiritIsReality on 2007-09-05
howdy

good to see.
maybe check if you could post in tips&tutorials, and maybe the wiki
[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)
[http://ubuntuforums.org/showthread.php?t=81999](http://ubuntuforums.org/showthread.php?t=81999)
[http://ubuntuforums.org/showthread.php?t=316820](http://ubuntuforums.org/showthread.php?t=316820)

trails

---

### Post by borahshadow on 2007-09-08
I just booted into a gutsy tribe5 live cd and I could connect to my wep network with NO tweaking :)

---

