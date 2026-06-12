---
title: "HOWTO: Installing Madwifi drivers"
date: 2007-06-27
forum: Apple Intel Users
---

### Post by ~joe~ on 2007-06-27
Hello, I noticed some users were saying that the madwifi install guides we have aren't that good/easy. I found these instructions at the [Debian MacBook Wiki]("http://wiki.debian.org/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688") (which, by the way, is an excellent resource), and I modified these instructions to work on Ubuntu. This is for everyone on Feisty Fawn (7.04) that is installing the madwifi set of drivers (unfortunately these instructions don't work in Dapper).

**[COLOR="Red"]Warning[/COLOR]**: **These instructions don't seem to do any good because newer MacBooks and other laptops with related wireless chipsets require madwifi-hal, so this guide shouldn't be followed anymore! Instead, use these instructions:**
[http://ubuntuforums.org/showpost.php?p=2731459&postcount=25](http://ubuntuforums.org/showpost.php?p=2731459&postcount=25)

[SIZE="5"]**Intro**
[/SIZE]
What is madwifi you may ask? Madwifi is actually a special driver that will allow Ubuntu or another Linux recognize your wireless cards that refuse to be recognized by Ubuntu already. But wait -- madwifi isn't for everyone! madwifi only supports certain chipsets, and if yours isn't supported, it's quite probable that following this installation guide will make no difference on your ability to use your wireless card under Linux. So, if you aren't sure whether your card is supported by this driver, visit the following page:
[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

Once you've verified your chipset and model are supported by madwifi, carry on below.

[SIZE="5"]**Preparation for the module: downloading**
[/SIZE]

First of all, you need to download the required .deb files. Open up a web browser, and visit the following links:
[http://packages.debian.org/testing/devel/module-assistant](http://packages.debian.org/testing/devel/module-assistant)
[http://packages.debian.org/unstable/net/madwifi-source](http://packages.debian.org/unstable/net/madwifi-source)

For both pages, scroll down to the section where it says "Download module-assistant" or "Download madwifi-source". Then beneath the heading "Architecture", you'll see **All**. Click it, and it will bring you to a list of mirrors. Pick a location that's nearby you, and right-click the link. Choose "Save As...", and choose your home folder.

There's one more package you need to download:

[http://packages.debian.org/unstable/net/madwifi-tools](http://packages.debian.org/unstable/net/madwifi-tools)

For this one, scroll down to where it says "Download madwifi-tools", but you'll notice that there's a whole list of architectures. Make sure you click on **i386**. Then pick a mirror like you did before, and download the resulting .deb to your home folder as well.

[SIZE="5"]**Compiling and installing**
[/SIZE]

Good, you're still following? Now here's where we get our hands dirty. Open up a new terminal window by opening the Gnome menu, choosing **Accessories**->**Terminal**. (On Kubuntu, it would be **System**->**Konsole**.) But before you can begin installing, you need administrator access. At the shell, type
```
sudo su
```
And hit return. Enter your password as prompted, and hit return again. Now you're ready to begin installing. To start off, install some pre-requisites first by entering the following command:
```
apt-get install debhelper dpkg-dev html2text po-debconf gettext intltool-debian
```

Now you need to install the packages you just downloaded. Enter the following 3 commands, one after the other:
```

dpkg -i module-assistant*.deb
dpkg -i madwifi-source*.deb
dpkg -i madwifi-tools*.deb
```

If that completed without any errors, you are now ready to build! Enter these 3 commands to finish off the installation:
```
m-a prepare
m-a a-i madwifi
depmod -a
```

[SIZE="5"]**Finishing up**
[/SIZE]

You can now test your wireless card. First, load the driver:
```
modprobe ath_pci
```
After completing this, any wireless software you have running right now should recognize the card. Everything should be working! Pat yourself on the back. If you want to test this out at the command line, just run this:
```
iwlist ath0 scan
```
One last thing though, you probably want this thing to be recognized at boot time. Enter this command:
```
gedit /etc/modules
```
You'll be presented with a text editor. Create a new line at the end of the file:
```
ath_pci
```
Save the file and quit gedit. Restart the computer, and your wireless card will be detected at boot.

[SIZE="5"]**Conclusion**
[/SIZE]

Through a number of recent revisions, I've done my best to make this guide as clear and easy-to-understand for newbies as possible. If you have any difficulty understanding something, please ask! I'm happy to explain, and I'll edit things if it becomes apparent that something wasn't written clear enough. And do please let me know if this works (or doesn't! post any errors here). Any comments are appreciated.

---

### Post by ronocdh on 2007-06-27
This is great, thanks for posting it. I'm considering reinstalling this weekend, and I'll use this guide for MadWiFi installation. My sole complaint is that it isn't phrased delicately enough for total newbies; keep in mind that a lot of the people who come here asking for help are straight-off-the-boat Apple users, and you really have to hold their hand. I would try to be more explicit in explaining the necessary steps.

---

### Post by ~joe~ on 2007-06-27
I'm sorry, I was in a bit of a rush when I wrote that. I think I'll edit it and add some improvements to make it a bit clearer. (By the way, is there any editing limit timeout thing? Like, most forums cut you off after 24 hours.)

---

### Post by maluka on 2007-06-27
these instructions definitely went over my head ;) 

i recently installed a Dell n enabled card that worked fine on my os x partition. how do i go about configuring it correctly?

---

### Post by ~joe~ on 2007-06-27
> **maluka said:**
> these instructions definitely went over my head ;) 

i recently installed a Dell n enabled card that worked fine on my os x partition. how do i go about configuring it correctly?
Sorry... I've rewritten the instructions. Let me know if it makes any more sense ;-)

---

### Post by ronocdh on 2007-06-28
> **~joe~ said:**
> Sorry... I've rewritten the instructions. Let me know if it makes any more sense ;-)
I personally really like the corrections! I know nothing about the timeout on editing... I think it's significantly longer than 24 hours, though. Awesome guide, I hope maluka likes them, too. ;)

---

### Post by maluka on 2007-06-28
after this step:

dpkg -i module-assistant*.deb
dpkg -i madwifi-source*.deb
dpkg -i madwifi-tools*.deb


i get an error message:

dpkg -i madwifi-tools*.deb
dpkg: error processing madwifi-tools*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 madwifi-tools*.deb

---

### Post by ~joe~ on 2007-06-28
> **maluka said:**
> after this step:

dpkg -i module-assistant*.deb
dpkg -i madwifi-source*.deb
dpkg -i madwifi-tools*.deb


i get an error message:

dpkg -i madwifi-tools*.deb
dpkg: error processing madwifi-tools*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 madwifi-tools*.deb
Hmm... it seems like the file doesn't exist. What is the result of this when you type it into the terminal:
```
ls
```

(anyway, it's getting late here. I'll have to log off now...)

---

### Post by cyberdork33 on 2007-06-28
> **maluka said:**
> these instructions definitely went over my head ;) 

i recently installed a Dell n enabled card that worked fine on my os x partition. how do i go about configuring it correctly?

I don't think this will work for you anyway. Most of the Dell cards I have used are broadcom based which means you need to use bcm43xx module or ndiswrapper. I may be wrong though. what does your lspci say?

```
$ lspci
```

---

### Post by maluka on 2007-06-28
after $ lspci  i get:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
03:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)
0c:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)

---

### Post by ~joe~ on 2007-06-28
Yep... you've got a Broadcom wireless card. madwifi is the wrong driver, you'll need bcm43xx module instead like cyberdork suggested. Or, if that doesn't work, resort to ndiswrapper.

---

### Post by maluka on 2007-06-28
thank you. the quest continues :)

---

### Post by Gen2ly on 2007-06-29
Nice job.  Just a friendly nit-pick.

> You can now test out your wireless card by entering these commands:

```
modprobe ath_pci
iwlist ath0 scan
```

modprobe loads the driver making it kernel-aware, while iwlist scans the network.

---

### Post by asch246 on 2007-06-29
hi joe,

thanks for putting up instructions like this. I tried the madwifi newbie instructions and I got lost quickly. 
Everything went well for me, until ¨iwlist ath0 scan¨
the response was:
```
ath0         Interface doesn´t support scanning : Network is down


```

I don´t understand because other computers are on the network fine. I´m using xubuntu 7.04 and WEP (hex)
My card is a DLink DWL-G510 hardware version: b1 firmware: 4.10

Thanks

Ps: I´m fairly new to this so, be gentle.

---

### Post by ~joe~ on 2007-06-29
> **Dirk.R.Gently said:**
> Nice job.  Just a friendly nit-pick.

modprobe loads the driver making it kernel-aware, while iwlist scans the network.
I was, as before my rewrite of this, trying to over-simplify things by packing several commands into one code block. For lack of anything else to say, I said that. I'll go fix it.

---

### Post by ~joe~ on 2007-06-29
> **asch246 said:**
> hi joe,

thanks for putting up instructions like this. I tried the madwifi newbie instructions and I got lost quickly. 
Everything went well for me, until ¨iwlist ath0 scan¨
the response was:
```
ath0         Interface doesn´t support scanning : Network is down


```
Hmm... well it seems like you followed the instructions correctly. What is the result of running this command?
```
ifconfig ath0
```

I've read that that command might be required to activate the card. Another thing you may want to try is connecting to the network without scanning. Try using this on an open network:
```
iwconfig ath0 essid "your network name"
dhclient ath0
```

Then see if you can access the internet. Hope that works for ya.

---

### Post by asch246 on 2007-06-29
```

root@xubuntu:/home/admin# ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:11:95:E5:45:2C  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3330 (3.2 KiB)  TX bytes:8407 (8.2 KiB)

root@xubuntu:/home/admin# iwconfig ath0 essid ¨dlink¨
root@xubuntu:/home/admin# dhclient ath0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:95:e5:45:2c
Sending on   LPF/ath0/00:11:95:e5:45:2c
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@xubuntu:/home/admin# 

```

thanks for the help- but no success. still no connection through wireless card. (currently using ethernet card)

---

### Post by asch246 on 2007-06-29
well, 
I still cant get a connection. Reading through various bit + pieces, the trouble seems to be getting dhcp to work. everything else appears to be in order. still getting this response from dhclient:


```
root@xubuntu:/home/admin# dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 5297
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:95:e5:45:2c
Sending on   LPF/ath0/00:11:95:e5:45:2c
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@xubuntu:/home/admin# 

```

---

### Post by cyberdork33 on 2007-06-30
it is not necessarily dhcp... although that is not getting an address. Are you using network-manager? it handles things a bit differently than the normal interface.

---

### Post by asch246 on 2007-06-30
I have used network manager to turn the ethernet card off in order to test the wireless connection. and to re-establish the ethernet card's connection when needed. I'd skip it if i knew how. 
What do you mean by "the normal interface"? Terminal?

---

### Post by cyberdork33 on 2007-06-30
yes that is what I was referring to. Instead of operating with the card directly, let network-manager handle it. use the networking init script to bring the network up and down.

```
$ sudo /etc/init.d/networking stop
$ sudo /etc/init.d/networking start
```

---

### Post by IFailAtLinux on 2007-07-01
I can't go trough this point:
```
m-a prepare
m-a a-i madwifi
depmod -a
```
because it tries to connect to internet, while I won't have net until I install madwifi... Is there any other way I could go about installing it?

---

### Post by Katjum on 2007-07-01
I have a relatively new (I ordered it 5 days after the model refresh this May) Macbook (not pro) C2D 2.16 Ghz, and I haven't been able to get the wireless to work from the instructions in this thread. I'm using Ubuntu 7.04 i386 on a 32GB ext3 partition (using rEIFit 0.10 to sync the hybrid partition tables for MacOSX). I ran the Update Manager before trying to install Madwifi (got all 72 updates, including a kernel one, though a wired connection to my Airport Extreme Base).

There were no reported errors (in building or installing) except at the end when I got:

```

ath0         Interface doesn´t support scanning

```

in response to:

```

iwlist ath0 scan

```

The wireless device then never appears in any of the gui network utilities, even after a reboot. :(

I'm new to Linux (though I do have some experience with the command line from OSX), so I don't really know what to try next. 
I reinstalled Ubuntu from the disc since I didn't know how to remove the driver before trying something new.

Device Manager tells me that the PCI card is a (Vender: Atheros Communication, Inc., Device: Unknown (0x0024), OEM Product (0x0087)).

Any help would be greatly appreciated!

Thanks

---

### Post by Chrisj303 on 2007-07-02
^^ I have just done a complete re-install, in hope of using these instructions to get my WIFI to finally work.

I'm getting EXACTLY the same response as the poster above me. I followed the guide to the T.

Worse still, my WIRED connection, while it is shown in network manager to be connected - WON'T actually connect to the net. It was fine before.



Deeply p***** off,

chrisj303

---

### Post by kzm. on 2007-07-02
different approach but works fine for me:

```
   sudo apt-get install gcc g++ libc6-dev linux-headers-2.6.20-16-generic build-essential debhelper
    tip: uname -r > kernel versio
    wget http://snapshots.madwifi.org/madwifi-hal-0.9.30.13-current.tar.gz
    tar -zxvf madwifi-hal-0.9.30.13-current.tar.gz
    cd madwifi <tab>
    make
    sudo make install
    sudo make clean
    reboot
```

---

### Post by Katjum on 2007-07-02
> Worse still, my WIRED connection, while it is shown in network manager to be connected - WON'T actually connect to the net. It was fine before.

Chrisj303, do you mean it was fine before you tried to install Madwifi or before you installed Ubuntu (i.e., it worked in MacOSX)?

My wired connnection continued to work after I tried to install Madwifi and always has worked under Ubuntu, but I'm connected to my Airport Base router. I couldn't connect to the Internet by just connecting my cable modem into the Ethernet. I had the same error you did.

Somewhere in this thread (or maybe another about wireless) someone suggested Ubuntu might play nicer through a router, and that has worked for me.

If you have a router, maybe you could give that a try.

Do you have the same model macbook?

Best of luck to you! :)

P.S. I tried the method suggested by kzm (It was on a macbook pro thread), and I still couldn't get wireless to work. :( 
(Of course, I did try it after I had already tried the one on this thread, so they might have somehow "prevented" each other.  I might try again soon. I didn't try this way exactly. Doesn't this just use a newer version?)

What model you you have, kzm?

---

### Post by kzm. on 2007-07-03
@Katjum: i have the macbook c2d 2.16 ghz. 

the first time i installed the wifi it wasnt working for me. at least i thought.. but i tried so many things at the same time that in the end my keyboard, mouse, wifi, screenbrightness etc was out of control. :)

after my second clean install i noticed that the wifi works fine with above mentioned procedure AFTER rebooting. i also noticed that when ever i update my system, i might loose wifi again (i believe every time some kernel headers get updated). also it seems that i loose once in a while wifi just like that (happened yesterday), mostly when i reboot its back. in any case if i do a new make & make install of the wifi its back. 

this sounds properly to you, that it works like ****. and it is definitely not the smoothest solution, but it works quite well, i have problems not much more than max once a week... i can live with that, opening my terminal typing cd mad<tab> and make & make install.

looking forward to gutsy though! still didnt tried its kernels yet... system stable, scared to touch it.

---

### Post by Katjum on 2007-07-03
@kzm.: I guess I'll have to reinstall again since I already applied some updates. :(

I haven't had a chance to try everything again, but when I do I'll post my results!

Hope it works this time! :)

---

### Post by kzm. on 2007-07-03
@Katjum: word! there are probably more having it running here than dont.. so why shouldnt you?

---

### Post by Katjum on 2007-07-07
Sorry it's been a while.  I haven't had much time lately. :(

I got the wireless to work! :p

I had to play with the settings on my AirPort router, so I might have some questions later.

For now though:

[CENTER]***HAPPY!***[/CENTER]

---

### Post by asch246 on 2007-07-07
Just to update ya'll, I still cant get the w'less card to work, but a more exp. friend is going to come over and have a go at it this week (hopefully!).

---

### Post by mikk on 2007-07-08
Hey guys, im very new to the whole linux thing, 

I've been following the instructions for installing madwifi on my acer 5100 (dual boot) It has the 5005g wireless athos card so i figured madwifi would be ok..

I followed the instructions but had one variation im obv not using a mac so i dled a diferent version on madwifi tools.

Anyway, im stuck here:

```
dpkg -i module-assistant*.deb
dpkg -i madwifi-source*.deb
dpkg -i madwifi-tools*.deb
```


i get an error message:

```
dpkg -i madwifi-tools*.deb
dpkg: error processing madwifi-tools*.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
madwifi-tools*.deb
```


This is the same as the user maluka

from 'ls' command i get

```
0000:06:02.0 Ethernet Controller: Atheros Communications, Inc.:Unknown Device 001a ( rev 01) 
```

I think thats the important part (wirless card)

Can anybody help??

Thanks Mikk

---

### Post by mikk on 2007-07-08
ok...
os i tried 

```
iwlist ath0 scan
```

And got all the wireless networks available in my area, (all the networks that were found on this desktop)

So that means that the laptop wireless card must be working in some way?!

HELP!

---

### Post by revertex on 2007-07-08
> **mikk said:**
> 
```
dpkg -i madwifi-tools*.deb
dpkg: error processing madwifi-tools*.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
madwifi-tools*.deb
```
Can anybody help??

sure.

issue the command in the same dir were debs  are.

---

### Post by mikk on 2007-07-08
I dled the files to the desktop and unpacked them there, and i'm pretty sure i was in the desktop whilst in kernal, I'll try again in a few hours after if finished outside.

Any ideas on why the card finds APs in the area even though its not showing up as working??

---

### Post by pbesing on 2007-07-08
Thanks for the instructions.  I was able successfully install the packages, no errors, etc.  I'm running Feisty.  Still, with this process gone over and over again to be sure, my atheros card does not show up on the network settings screen.  

LSPCI gives me this info re: my atheros card.
03:00.0 Network Controller: Ahteros Communications, Inc Unknown Device 0024 (rev 01)

Any ideas?  thanks!

---

### Post by exoren22 on 2007-07-10
I recently compiled the new 2.6.22 kernel,and I used this guide to try to install the madwifi driver for the new kernel. I installed the .deb's with no problem, but when I ran 
```
m-a a-i madwifi
```
I got an error. I thought it might be a problem with the debs, so i tried to install from source, but it also failed on the make with the same error. 
```
$ sudo make
Password:
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-unique/build SUBDIRS=/home/david/Desktop/madwifi-0.9.3.1 modules
make[1]: Entering directory `/usr/src/linux-2.6.22'
  CC [M]  /home/david/Desktop/madwifi-0.9.3.1/ath/if_ath_pci.o
cc1: warnings being treated as errors
/home/david/Desktop/madwifi-0.9.3.1/ath/if_ath_pci.c: In function 'ath_pci_probe':
**/home/david/Desktop/madwifi-0.9.3.1/ath/if_ath_pci.c:210: warning: 'deprecated_irq_flag' is deprecated (declared at include/linux/interrupt.h:66)**
make[3]: *** [/home/david/Desktop/madwifi-0.9.3.1/ath/if_ath_pci.o] Error 1
make[2]: *** [/home/david/Desktop/madwifi-0.9.3.1/ath] Error 2
make[1]: *** [_module_/home/david/Desktop/madwifi-0.9.3.1] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.22'
make: *** [modules] Error 2
```
That seems to be the problematic line. 
Help is really appreciated. 

ps, the make worked just fine for the 2.6.20-16 kernel, which is the latest ubuntu distributed kernel in feisty.

---

### Post by Gen2ly on 2007-07-11
I've heard about new irq settings in the new kernel version.  Apparently madwifi hasn't gotten around to updating their drivers to accomadate for it.  You'll probably have to try that once more when they update them.  2.6.21 is a real stable and very well running kernel for me.  Since the updated kernel has a number of new features I think I'll wait a little bit.

---

### Post by exoren22 on 2007-07-12
Ah, I thought that might be the case, but I was hoping someone might know a workaround. I'll wait for madwifi to make use of the new wireless stack, anyway. Thanks for the help.

---

### Post by Wittiga on 2007-07-13
Thanx very much for the how to. But ive experienced some problems. Instead of manually downloading the *.debs i added these lines to mey sources.list:
# Stable
deb [ftp://ftp.au.debian.org/debian](ftp://ftp.au.debian.org/debian) stable main contrib non-free
deb-src [ftp://ftp.au.debian.org/debian](ftp://ftp.au.debian.org/debian) stable main contrib non-free

from [http://madwifi.org/wiki/UserDocs/Distro/Debian/MadWifi](http://madwifi.org/wiki/UserDocs/Distro/Debian/MadWifi)

And then everything went all right until i did:
$ sudo iwlist ath0 scan
ath0      Interface doesn't support scanning.

How can i know what failed?

---

### Post by samtaylor on 2007-07-17
I followed the guide up to:

```
root@sam-laptop:/home/sam# dpkg -i madwifi-tools*.deb
```

Then I get:

```
Selecting previously deselected package madwifi-tools.
(Reading database ... 112902 files and directories currently installed.)
Unpacking madwifi-tools (from madwifi-tools_0.9.3+dfsg-2_i386.deb) ...
dpkg: dependency problems prevent configuration of madwifi-tools:
 madwifi-tools depends on libc6 (>= 2.5-5); however:
  Version of libc6 on system is 2.5-0ubuntu14.
dpkg: error processing madwifi-tools (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 madwifi-tools
```
I was just wondering what I should/could do to actually get this to work?

---

### Post by cyberdork33 on 2007-07-17
It is a dependency problem. You need a version of libc6 that is newer than what you have.

---

### Post by primetime on 2007-07-17
> **cyberdork33 said:**
> It is a dependency problem. You need a version of libc6 that is newer than what you have.

I have the same problem as samtaylor.  The libc6 version installed default on Feisty 7.04 is  2.5-0ubuntu14.  
How can I update it to a newer version?

---

### Post by Chrisj303 on 2007-07-19
I've been having a nightmare getting Wi-Fi to work on my 2nd gen Macbook. Both of the MadWIFI guides on the stickys didn't work - wireless card wasn't even detected in network manager.

Made a breakthrough today though! - by using the SVN mentioned by Benanzo in this post : [ubuntuforums.org/showpost.php?p=2731459&postcount=25]("ubuntuforums.org/showpost.php?p=2731459&postcount=25")

My Wi - Fi works a treat!

Here is my lspci :
chris@chris-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications, Inc. Unknown device 0024 (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
chris@chris-laptop:~$

---

### Post by ~joe~ on 2007-07-19
Sorry, I've been out and about for a while. Now when I come back I see that this guide seems to be causing more problems than solving them. Dependancy issues are widespread, and the biggest problem of all is that iwlist doesn't work -- it says something about "Interface doesn't support scanning" (and doesn't show up in the network manager).

From what I can tell, the ath0 scanning problems come from the problem that newer MacBooks and other wireless cards require the madwifi-hal package, whereas this guide downloads the madwifi-ng package. To make matters worse, it appears that the madwifi-ng package is already installed on Ubuntu (for example, I can load up the Ubuntu LiveCD and type 'iwconfig ath0 essid "my network"' followed by a DHCP request and have my card work perfectly). If I'm wrong in my statements here, someone provide clarification, but it appears that this guide is completely useless. It should just be removed from the sticky and benzano's post should be the primary way of doing it (through the snapshot). I'm sorry guys.

> **exoren22 said:**
> I recently compiled the new 2.6.22 kernel,and I used this guide to try to install the madwifi driver for the new kernel. I installed the .deb's with no problem, but when I ran 
```
m-a a-i madwifi
```
I got an error. I thought it might be a problem with the debs, so i tried to install from source, but it also failed on the make with the same error. 
```
$ sudo make
Password:
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-unique/build SUBDIRS=/home/david/Desktop/madwifi-0.9.3.1 modules
make[1]: Entering directory `/usr/src/linux-2.6.22'
  CC [M]  /home/david/Desktop/madwifi-0.9.3.1/ath/if_ath_pci.o
cc1: warnings being treated as errors
/home/david/Desktop/madwifi-0.9.3.1/ath/if_ath_pci.c: In function 'ath_pci_probe':
**/home/david/Desktop/madwifi-0.9.3.1/ath/if_ath_pci.c:210: warning: 'deprecated_irq_flag' is deprecated (declared at include/linux/interrupt.h:66)**
make[3]: *** [/home/david/Desktop/madwifi-0.9.3.1/ath/if_ath_pci.o] Error 1
make[2]: *** [/home/david/Desktop/madwifi-0.9.3.1/ath] Error 2
make[1]: *** [_module_/home/david/Desktop/madwifi-0.9.3.1] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.22'
make: *** [modules] Error 2
```
That seems to be the problematic line. 
Help is really appreciated. 

ps, the make worked just fine for the 2.6.20-16 kernel, which is the latest ubuntu distributed kernel in feisty.
Before you try to compile the source code, first try doing this: (and yes, this is a problem with the latest kernel)
[http://ubuntuforums.org/showpost.php?p=599682&postcount=5](http://ubuntuforums.org/showpost.php?p=599682&postcount=5)

---

### Post by cyberdork33 on 2007-07-19
> **~joe~ said:**
>  Before you try to compile the source code, first try doing this: (and yes, this is a problem with the latest kernel)
[http://ubuntuforums.org/showpost.php?p=599682&postcount=5](http://ubuntuforums.org/showpost.php?p=599682&postcount=5)

Might want to edit the opening post since there are probably those that don't read through the entire thread before trying.

---

### Post by ~joe~ on 2007-07-20
Done. I was going to do that this morning, but then ugh, work...

---

### Post by mnewsom on 2007-07-23
these instructions worked perfectly for me. i'm on a macbook core duo (yes, i did need to replace the heat sink) that is successfully triple booting. i'm on the wireless as we speak and its great but my update manager keeps telling me the software index is broken. synaptic identifies the new madwifi drivers as the problem and suggests i uninstall them but that would defeat the purpose of ... well, installing them. so does anyone have any suggestions on how to get update manager to look the other way. and yes, i'm a longtime mac user so i'm not yet comfortable on the command line.

edit- I just uninstalled and everything's fine. I don't think a core duo machine needs these drivers.

---

### Post by Wittiga on 2007-07-23
What exactly is the error message about the broken index?

---

### Post by Paris Heng on 2007-07-26
HOW-TO] Master Mode + Madwifi + Bridging
Dear all,

I have installed Madwifi + Atheroes Wifi in the **laptop A**, and it work well.

I have made the Wifi card into Master Mode (access Point)**(laptop A**).
My another **laptop B** use to connect to it, but cannot!! It just able to scan and detect the availability of the access point where i created in **laptop A**.

Problems:

How I to enable **laptop B** to connect to **laptop A**? What i miss?

(1) Routing ?
(2) NAT ?
(3) DHCP ?
(4) Port Fowarding ?
(5) WPA ?


Please assist.

---

### Post by fizz on 2007-08-17
anyone have any ideas on the libc6 errors that some of us are getting?

```
dpkg -i madwifi-tools_0.9.3+dfsg-2_i386.deb Selecting previously deselected package madwifi-tools.
(Reading database ... 131031 files and directories currently installed.)
Unpacking madwifi-tools (from madwifi-tools_0.9.3+dfsg-2_i386.deb) ...
dpkg: dependency problems prevent configuration of madwifi-tools:
 madwifi-tools depends on libc6 (>= 2.5-5); however:
  Version of libc6 on system is 2.5-0ubuntu14.
dpkg: error processing madwifi-tools (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 madwifi-tools

```

---

### Post by Paris Heng on 2007-08-17
> **fizz said:**
> anyone have any ideas on the libc6 errors that some of us are getting?

```
dpkg -i madwifi-tools_0.9.3+dfsg-2_i386.deb Selecting previously deselected package madwifi-tools.
(Reading database ... 131031 files and directories currently installed.)
Unpacking madwifi-tools (from madwifi-tools_0.9.3+dfsg-2_i386.deb) ...
dpkg: dependency problems prevent configuration of madwifi-tools:
 madwifi-tools depends on libc6 (>= 2.5-5); however:
  Version of libc6 on system is 2.5-0ubuntu14.
dpkg: error processing madwifi-tools (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 madwifi-tools

```


Yes, how to solve the dependency problem? OR you can try Ubuntu 7.04, i successfully installed the Madwifi in there, and it works great.

---

### Post by Paris Heng on 2007-08-17
Dear joe,

I have follow your Madwifi How-To in the forum. I installed in Ubuntu 7.04, and i can connect to internet, I mean it works great!! I able to change mode to like Ad-hoc and AP. 

And when i add a route to **ath0 **:-

**route add -net 192.168.1.1 netmask 255.255.244.0 dev ath0**

**it give unrecognized interface for ath0!!!**


So, it is wrong in installing the Madwifi for your guide that you have post previously?


Thank you.

---

### Post by tehkain on 2007-09-03
> **asch246 said:**
> ```

root@xubuntu:/home/admin# ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:11:95:E5:45:2C  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3330 (3.2 KiB)  TX bytes:8407 (8.2 KiB)

root@xubuntu:/home/admin# iwconfig ath0 essid ¨dlink¨
root@xubuntu:/home/admin# dhclient ath0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:95:e5:45:2c
Sending on   LPF/ath0/00:11:95:e5:45:2c
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@xubuntu:/home/admin# 

```

thanks for the help- but no success. still no connection through wireless card. (currently using ethernet card)

Anyone find a solution for this issue?

---

### Post by mrbash on 2007-09-04
> **Katjum said:**
> I have a relatively new (I ordered it 5 days after the model refresh this May) Macbook (not pro) C2D 2.16 Ghz, and I haven't been able to get the wireless to work from the instructions in this thread. I'm using Ubuntu 7.04 i386 on a 32GB ext3 partition (using rEIFit 0.10 to sync the hybrid partition tables for MacOSX). I ran the Update Manager before trying to install Madwifi (got all 72 updates, including a kernel one, though a wired connection to my Airport Extreme Base).

There were no reported errors (in building or installing) except at the end when I got:

```

ath0         Interface doesn´t support scanning

```

in response to:

```

iwlist ath0 scan

```

The wireless device then never appears in any of the gui network utilities, even after a reboot. :(

I'm new to Linux (though I do have some experience with the command line from OSX), so I don't really know what to try next. 
I reinstalled Ubuntu from the disc since I didn't know how to remove the driver before trying something new.

Device Manager tells me that the PCI card is a (Vender: Atheros Communication, Inc., Device: Unknown (0x0024), OEM Product (0x0087)).

Any help would be greatly appreciated!

Thanks

Have you tried to wake up the interface before run the scan command?

```

ifconfig ath0 up
iwlist ath0 scan

```

---

### Post by mari0- on 2007-09-11
Whenever I run 


m-a prepare
m-a a-i madwifi
depmod -a

It starts to build then gets a dependancy error. o.O

No errors prior to this.

---

### Post by zmjjmz on 2007-09-30
I've had the same problems with the dependencies...
it says I have libc6 2.6.1-5 installed, but is that the right one?

---

### Post by Loki1989 on 2007-11-20
iwlist ath0 scan
ath0      Interface doesn't support scanning.


I got that error after following several instructions

---

### Post by cyberdork33 on 2007-11-20
> **Loki1989 said:**
> iwlist ath0 scan
ath0      Interface doesn't support scanning.


I got that error after following several instructions
Just look in network manager to see if it is working. You can also do ```
sudo iwconfig
``` to see all the wireless network interfaces that your system recognizes.

---

### Post by mabovo on 2008-01-03
mabovo@macbook:~$ sudo iwconfig
[sudo] password for mabovo: 
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

mabovo@macbook:~$

---

### Post by echo6 on 2008-01-06
I came here after searching for the following errors
```
wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
```
I'm using a MacBookPro which also uses the madwifi drivers ```
03:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
```
I noted that dhcp won't work with NetworkManager, I have to manually associate with my Access Point using e.g.```
iwconfig ath0 ap 00:0A:BA:EF:22:3D:99
```before using dhclient ath0 to get an IP address.
Looking for a solution to automate this.

---

### Post by cyberdork33 on 2008-01-07
> **echo6 said:**
> I noted that dhcp won't work with NetworkManager, 
network-manager is not working because you have tried to configure manually. You have to set it to roaming mode for it to work correctly.

---

### Post by echo6 on 2008-01-07
Darn,  thanks I missed that one :-)

---

