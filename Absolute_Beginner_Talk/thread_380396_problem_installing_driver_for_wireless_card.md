---
title: "problem installing driver for wireless card"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Griffiss on 2007-03-09
hey

my driver doesn't seem to want to install properly.

My wireless card is an ASUS WL-138G.

I've installed the following packages:

ndiswrapper-common (1.18-1ubuntu2)
ndiswrapper-utils-1.8 (1.18-1ubuntu2)

Then I copied the following files from my driver cd to the desktop:

mrv8k51.inf
MRV8K51.sys

Then in the terminal I typed:

sudo ndiswrapper -i mrv8k51.inf

Then I got this message:

Installing mrv8k51
couldn't copy mrv8k51.inf at usr/sbin/ndiswrapper-1.8 line 144

And now when I type:

ndiswrapper -l

into the terminal, it says this:

Installed drivers:
mrv8k51 Invalid driver!

which is not too cool. help please!!!

---

### Post by honns on 2007-03-09
first thing, your version of ndiswrapper is old, 1.38 is what i have (someone correct me if im out of line) although im not sure if it matters

second, type in lspci and find your wireless card

I had the same problem, but it turns out that the drivers given by the manufacturer dont work.  You have to find driver based on the card information by what lspci tells you.  Ex.  my Airnet awn154 uses a Marvell driver, go figure.  once i figured that out there was a tutorial online for my driver which helped a bunch

---

### Post by Griffiss on 2007-03-09
hey thanks for your reply honns

lspci gives this (it gives a lot of stuff but i think this is the relevant part):

00:10.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)

A problem for me is that I can't find other drivers because the pc I've installed ubuntu onto is not on the net - I'm using a windows laptop to send these posts.

---

### Post by honns on 2007-03-09
[http://www.ubuntuforums.org/showthread.php?t=288341&highlight=Marvell+W8300+install](http://www.ubuntuforums.org/showthread.php?t=288341&highlight=Marvell+W8300+install)

there you go, a how to on installing the marvell w8300 driver for the asus wi-138g card :)

---

### Post by Griffiss on 2007-03-09
thanks for your help honns, i really appreciate the support.

but these were the instructions i used in the first place :(

I haven't gone to the site mentioned, but then the computer that has the problem can't connect to anything, so I don't see what I can do

---

### Post by honns on 2007-03-09
not even through an ethernet cord?

---

### Post by Griffiss on 2007-03-09
don't have one unfortunately

---

### Post by honns on 2007-03-09
oi i forgot about this, what does it say when you put

ndiswrapper -v

in the console?

also i found another thread that might be helpful: [http://ubuntuforums.org/showthread.php?t=190726&highlight=marvell+w8300+ndiswrapper](http://ubuntuforums.org/showthread.php?t=190726&highlight=marvell+w8300+ndiswrapper)

---

### Post by Griffiss on 2007-03-09
hey sorry got distracted

when i type in ndiswrapper -v, i get this:

utils Error: no version specified!
driver version: 1.22
vermagic: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1

I'll try some of the things on that thread too.

---

### Post by honns on 2007-03-09
i would try unsintalling ndiswrapper through the Synaptic in Administration and downloading and installing the new ndiswrapper, use [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)
for a guide.  If this doesnt help then I hope you can find somehting in some other threads

---

### Post by Griffiss on 2007-03-09
i used a mixture of the methods in the threads you mentioned and i think i've got it now. it's now saying 'mrv8k51 driver present, hardware present' so i'm going to reboot and see what happens. fingers crossed! thanks a lot!

---

### Post by RomeReactor on 2007-03-09
Hi. I have the exact same chipset in my wireless card and use those same drivers, and use the same version of NdisWrapper as you; if you're still having problems, i'll try to help.

---

### Post by honns on 2007-03-09
from the lack of a post im guessing it worked?

---

### Post by jonesofboise on 2007-05-09
I also have an IBM T23 Thinkpad and an Airnet AWN154. Do you have a link to the page with the instructions on how to install the Marvell driver?

Thank you so much for any help you can give me. 

Ubuntu 6.06

---

### Post by RomeReactor on 2007-05-09
Hi If you're running 32-bit Dapper? and is Marvell w8300 your chipset? if you're unsure, please post the output of

```
lspci
```

---

### Post by jonesofboise on 2007-05-09
> **RomeReactor said:**
> Hi If you're running 32-bit Dapper? and is Marvell w8300 your chipset? if you're unsure, please post the output of

```
lspci

0000:00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 0 2)
0000:00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Au dio Controller (rev 01)
0000:01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
0000:02:00.0 CardBus bridge: Texas Instruments PCI1420
0000:02:00.1 CardBus bridge: Texas Instruments PCI1420
0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE ( LOM) Ethernet Controller (rev 41)
0000:07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Liberta s] 802.11b/g Wireless (rev 03)

```

Here is the lspci. Thank you so much for the pending help. I'm a newbie, but I love linux and want to grow. Thanks for the help again.

---

### Post by RomeReactor on 2007-05-10
This is what I found on the [NdisWrapper]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/")  site regarding your card:

> Card: Airnet AWD154/AWN154

    *      Chipset: Marvell Technology Group Ltd.: Unknown device 1faa

    *      PCI ID: 11ab:1faa (rev 03)

    *      Driver: [**Here.**]("http://www.airnetusa.com/downloads/driver/DRXP_AWD_AWN154_v11.zip")

    *      Other: Used ndiswrapper on Kubuntu 5.10 (Breezy) CD. kernel updated to 2.6.12 added                          stability. Also **works fine with WindowsXP drive from the CD, download not nescessary**.

So if you have the cd with the windows drivers, no need to get them elsewhere, but for now, we'll use the ones you [download]("http://www.airnetusa.com/downloads/driver/DRXP_AWD_AWN154_v11.zip"). 

To do this, the easiest way is to have a wired connection (since the wireless obviously doesn't work at the moment). Open Synaptic (System-->Administration-->Synaptic Package Manager) and search for **ndiswrapper**; Three packages must show up: **ndiswrapper-common** should already be installed (I think), so mark **ndiswrapper-utils-1.9** for installation. You won't need **ndiswrapper-source**.

Now, on with the drivers: Once you have the .zip file, extract it (it should extract as a folder named "DRXP_AWD_AWN154_v11"), open a terminal (Applications-->Accessories-->Terminal) and navigate to the location of the folder you just extracted:

```
cd Desktop
```

Or replace "Desktop" with the location you extracted it to. Now enter the following in the terminal:

```
sudo chmod 777 -R DRXP_AWD_AWN154_v11
```

Where **DRXP_AWD_AWN154_v11** is the name of the folder you extracted from the downloaded .zip file (this is done to give the folder and the files inside it permissions to be used by anyone). Next, in the terminal, go inside that folder:

```
cd DRXP_AWD_AWN154_v11
```

Inside you'll find three files: **Mrv8000c.cat, Mrv8000c.inf,** and **Mrv8000c.sys**. Now let's tell NdisWrapper to install them:

```
sudo ndiswrapper -i Mrv8000c.inf
```

Now to check if they installed correctly

```
ndiswrapper -l
```

It has to show: Installed ndis drivers: DRIVER_NAME driver present, hardware present. Next:

```
sudo depmod -a
```

depmod  creates  a  list of module dependencies;

```
sudo modprobe ndiswrapper
```

modprobe intelligently adds or removes a module from the Linux  kernel;

```
sudo ndiswrapper -m
```

loads ndiswrapper automatically when the wlan0 interface is used;

```
gksudo gedit /boot/grub/menu.lst
```

and when Gedit pops up, write:

```
acpi=off
```

between "### BEGIN AUTOMAGIC KERNELS LIST" and "## DO NOT UNCOMMENT THEM, Just edit them to your needs"; save and close Gedit. Next:

```
gksudo gedit /etc/modules
```

and write **ndiswrapper** at the end of the file (to load ndiswrapper automatically at boot time); and finally, reboot your computer. When it boots up again, you should have your wireless card working, and it should be a matter of configuring it (if you use static ip), but first things first: please post back with how it went, and if you found any roadblocks along the way.

**NOTE**: If you can't get a wired connection, you can download the drivers in another computer (or use the ones from the cd), and i think the **ndiswrapper-utils-1.9** should be in the Ubuntu cd. Also, sorry for the convoluted post and the delayed reply.

---

