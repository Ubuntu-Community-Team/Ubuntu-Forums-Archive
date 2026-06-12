---
title: "Help getting my wireless card to work!"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by viciouscapulet on 2007-11-05
Hello : )



I have an HP Pavilion ze2135us and have been trying to get the wireless card to work. I've used the Raven's guide for this type of card that is located in the forums but I get stopped at where I open ./ndiswrapper_setup and once I do it says close other package management software before continuing and then press enter. So I do and press enter and it just hangs up right there and does nothing. I've got the drivers, I got ndiswrapper waiting to be installed, just needed a little more help. Any ideas? Thank you for your time.

-vC.

---

### Post by viciouscapulet on 2007-11-05
BTW i'm using Kubuntu Gutsy 7.10

---

### Post by NullHead on 2007-11-05
please open a terminal and type ```
lspci
``` for me and past all of that into a post her ;)

---

### Post by viciouscapulet on 2007-11-05
Sorry, it's an Hp Pavilion ze 2315us and here is the lspci:


00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

---

### Post by kmac on 2007-11-05
I have the same wireless card in my compaq. If you haven't already, install ndiswrapper and copy the driver files from the windows driver cd that came with your hp. (which also may be backed up on your HD as "swsetup"). There are plenty of tutorials here on using ndiswrapper to get you up and going. Make sure to install wifi-radar as well, otherwise the card tends to get "confused" when there are multiple routers using the same name (such as in a college, that's where i noticed mine).

Good luck and email me if you need help -- [email]feistyfawn1249@gmail.com[/email]

--Kyle

---

### Post by kmac on 2007-11-05
sorry i missed the part where you're having trouble with installing ndiswrapper 

try installing it in recovery mode through the terminal.

--Kyle

---

### Post by viciouscapulet on 2007-11-05
how do i get into recovery mode?

---

### Post by NullHead on 2007-11-05
Please use [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) for a very nice gui to take care of everything ... it will ask you to install the bcm43xx firmware ... you don't want to there is problems with it and your card working together ... soo use ndiswrapper.

---

### Post by magiceraser06 on 2007-11-05
What problem are you having while installing ndiswrapper?  make sure to get the latest version, I believe it up to 1.49.   The older versions are sorta buggy and don't always work with all the cards.

Ndiswrapper is pretty easy to install and set up.  should only take like 10 mins to be cruisin the net.  

which guide did you follow?  There are some that have extraneous steps.  You DO NOT have to edit your interfaces file with the newer version of ndiswrapper.  that part always screwed me up.  I have a Trendnet wireless card, which is notoriously hard to set up in older versions.

All you would really need to do is download ndiswrapper from here:   [http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=550075](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=550075)

Then, 
 ```

sudo apt-get update
sudo apt-get install build-essential linux-headers-$(uname -r)
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

```

That should get you set up with what you'll need to be able to compile from sources.

Next , extract the contents of the file into a folder in your /HOME directory.  then in Terminal browse to the folder you just made and key in:

```

sudo make
sudo make install

```

That should get you installed and ready for use.

Then, get the driver files for your card from your CD or where Kmac suggested, since you two have the same card.

Then, browse to that folder in TERMINAL.   Once there, code in:

```

sudo ndiswrapper -i NAME_OF_FILE.INF
sudo ndiswrapper -l

```

if everything went well, you should see your card listed.

Then, you'll need to do:

```

sudo depmod -a
sudo modprobe ndiswrapper

```

Then to make it permanently load on startup:

```

sudo ndiswrapper -m

```

At which point your wireless card should light up and start looking for networks.  You can then use WiFi radar to connect to your favorite network.

Hope that helps.  let me know if you have any problems.

---

### Post by viciouscapulet on 2007-11-06
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build



When I do this, it says no such file or directory, did you miss a step? :) And thank you for such good help!


vC

---

### Post by magiceraser06 on 2007-11-06
hmm, wierd.   
 Try this :
```

sudo apt-get install linux-headers-`uname -r` 
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build 

```

you might not need it.  did everything else work?  i will double check and get back to you,

-cheers-

---

### Post by magiceraser06 on 2007-11-10
hey vC,
just checking to see if you got your card set up n all?  gives us all an update.

---

