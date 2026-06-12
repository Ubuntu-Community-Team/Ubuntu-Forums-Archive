---
title: "another ndiswrapper question"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by paker on 2007-07-27
I want to install a US Robotics wireless pci card (USR5417). US Robotics web says it is supported by Linux and had a link to ndiswrapper.

1) I installed ndiswrapper through Automatix. (I don't know any other way)
2) I now need to run in terminal "ndiswrapper -i xxxxx.inf" But the driver is xxxx.exe. How do I get .inf from .exe?
3) US Robotics web has 2 drivers, one for Windows 2kxp and the other for Windows Me (?). I downloaded the one for 2kxp. Did I get the right one?
4) Does it matter if I run "ndiswrapper -i xxxx.inf" with or without the wireless card?

Thanks.

---

### Post by tomcheng76 on 2007-07-27
Try using ndiswrapper; [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

From; [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Card: US ROBOTICS USR805417 802.11g MaxG PC Card

* Chipset: Broadcom Corporation BCM4318 (rev 02)
* pciid: 14e4:4318
* Driver: You have to unshield the file Data.exe and then the file data2.cab. These files are on the install CD, or can be downloaded[58]. Tested with the driver USRMAXGa.inf on Slackware 10.1, kernel 2.4.29, ndiswrapper 1.5


sure u have to "extract" the exe file

---

### Post by paker on 2007-07-27
Sir,
Please be patient with me. How do I extract inf file from exe file?
Thank you.

---

### Post by tomcheng76 on 2007-07-27
may be you can try file-roller if you are using Gnome
let me confirm it first

---

### Post by tomcheng76 on 2007-07-27
i can extract it using 7zip
here is the command 
7z e 5417a-2.00.004.exe
and
cabextract Data2.cab

---

### Post by tomcheng76 on 2007-07-27
sudo apt-get install p7zip-full cabextract unshield
mkdir temp
cd temp
7z e 5417a-2.00.004.exe                     <---- ensure 5417a-2.00.004.exe is inside ~/temp
unshield -d . x data2.cab                       <---this unshield data2.cab to current directory (~/temp)

---

### Post by RomeReactor on 2007-07-27
Hi. Do you have a wired connection on your Ubuntu computer?

---

### Post by paker on 2007-07-28
Thanks. I didn't have 7zip so I had to install it first. I ran "7z e xxxx.exe" and I got a whole bunch of files on desktop, one of which is data2.cab. Again, I had to install cabextract and ran "cabextract data2.cab" Here is the output:

rust@rust-desktop:~$ cabextract '/home/rust/data2.cab' 
/home/rust/data2.cab: WARNING; found InstallShield header. This is probably an InstallShield file. Use UNSHIELD ([http://synce.sf.net](http://synce.sf.net)) to unpack it.
/home/rust/data2.cab: no valid cabinets found

All done, errors in processing 1 file(s)
rust@rust-desktop:~$ 


Do you suggest that I install UNSHIELD and use it?
Thanks.

---

### Post by tomcheng76 on 2007-07-28
you need connection to dl the p7zip-full cabextract unshield ( or using Ubuntu CD ?)
if u use USR5417-1.00.022.exe, here is the new procedure

sudo apt-get install p7zip-full cabextract unshield
mkdir temp
cd temp
wget [http://www.usr.com/support/5417/5417-files/USR5417-1.00.022.exe](http://www.usr.com/support/5417/5417-files/USR5417-1.00.022.exe)
7z e USR5417-1.00.022.exe  <---- ensure USR5417-1.00.022.exe is inside ~/temp if you dont use wget
cabextract Data.exe
cd Disk1
unshield -d . x data2.cab <---this unshield data2.cab to current directory (~/temp)
cd Installer_Files_Win2kXp
look for USRMAXGa.inf


#
Card: US ROBOTICS USR805417 802.11g MaxG PC Card

    *
      Chipset: Broadcom Corporation BCM4318 (rev 02)
    *
      pciid: 14e4:4318
    *
      Driver: You have unzip the file downloaded from USR then use cabextract on the file Data.exe and then unshield on the file data2.cab. These files are on the install CD, or can be downloadedhttp://www.usr.com/support/product-template.asp?prod=5417. Tested with the driver USRMAXGa.inf on Slackware 10.1, kernel 2.4.29, ndiswrapper 1.5

---

### Post by paker on 2007-07-28
> sudo apt-get install p7zip-full cabextract unshield
mkdir temp
cd temp
7z e 5417a-2.00.004.exe <---- ensure 5417a-2.00.004.exe is inside ~/temp
unshield -d . x data2.cab <---this unshield data2.cab to current directory (~/temp)
I posted reply before reading this. I will install unshield first and run it. 

> Hi. Do you have a wired connection on your Ubuntu computer?
Yes, that's how I am accessing internet now. Eventually, I want to switch over to wireless. If you have suggestions, please let me know. Thanks.

---

### Post by tomcheng76 on 2007-07-28
yes, u need unshield
will generate tones of files on your Desktop if you dont make a temporary directory ( so as my Desktop too :()

---

### Post by RomeReactor on 2007-07-28
If you already have the driver (which you can get [here]("http://www.usr.com/support/5417a/5417a-files/5417a-2.00.004.exe")), I recommend making a folder called **driver** in your home folder, and putting the driver there, as after extraction, there will be many files to deal with.

You need to install unshield and cabextract:
```
sudo apt-get install unshield cabextract
```
then, still in the terminal, change to the **driver** directory:
```
cd driver
```
next, to extract with cabextract:
```
cabextract 5417a-2.00.004.exe
```
then change to the newly created directory:
```
cd Disk1
```
and use unshield:
```
unshield x data2.cab
```
change to the Bradcom directory:
```
cd Broadcom
```
and use ndiswrapper:
```
ndiswrapper -i USRMAXG.inf
```

Please not that I don't have a Broadcom card, and can't guarantee this will work.

---

### Post by paker on 2007-07-28
Thank you for guiding me step by step. I think I got all right. I ran ndiswrapper and here is the output:


rust@rust-desktop:~/temp/Disk1$ ndiswrapper -i '/home/rust/temp/Disk1/Installer_Files_Win2kXp/USRMAXGa.inf' 
couldn't create /etc/ndiswrapper/usrmaxga: Permission denied at /usr/sbin/ndiswrapper-1.9 line 146.
rust@rust-desktop:~/temp/Disk1$ 


By the way, I also found USRMAXG.inf (in addition to USRMAXGa.inf). Will that do any good? Thanks.

---

### Post by paker on 2007-07-28
> and use unshield:
Code:

unshield x data2.cab

By the way, I made a mistake here. I actually entered " unshield -d . x data2.cab" I thought the dot was there on purpose. Does it make any difference?

I am still rough on making directories and changing directories. So I copy and paste files, and by now I have no idea which files are where. Sigh!

PS: I tried "ndiswrapper -i USRMAXG.inf" Same error message.

---

### Post by RomeReactor on 2007-07-28
The [NdisWrapper]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/#u") page for your card (scroll down to # 5) mentions **USRMAXGa.inf** as the tested driver, so you probably should use that.

And run ndiswrapper as root (sorry, forgot about that!):
```
sudo ndiswrapper -i USRMAXGa.inf
```

---

### Post by tomcheng76 on 2007-07-28
" unshield -d . x data2.cab"
. means current directory (the directory u are currently located)
so it has no different with unshield x data2.cab (sorry , i use unshield first time, should write the simplest method)
just try what RomeReactor said,  use sudo

---

### Post by paker on 2007-07-28
Used "sudo ndiswrapper ......." It went all right. But I still don't have wireless connection. I will do more seaerch of this forum. In the meantime if you have suggstions pls let me know. Thanks.

---

### Post by RomeReactor on 2007-07-28
Enter this in the terminal to check if the driver is correctly installed:
```
ndiswrapper -l
```

---

### Post by paker on 2007-07-28
rust@rust-desktop:~$ ndiswrapper -l
usrmaxg : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
usrmaxga : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
rust@rust-desktop:~$


[B]
I also read about lspci. Here is the output:[/B]


rust@rust-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
04:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
rust@rust-desktop:~$

**I also did iwconfig:**

rust@rust-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rust@rust-desktop:~$

---

### Post by paker on 2007-07-28
What about these commands that I found in another thread? I am hesitant to type all these not knowing what I am doing. Please advise. Thanks.

> sudo ndiswrapper -i bcmwl5a.inf [COLOR="DarkRed"](I did this)[/COLOR]
ndiswrapper -l [COLOR="DarkRed"](I did this, too)[/COLOR]
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto loniface lo inet loopbackn' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules

Reboot after last command above.

and if you want to try WPA (i did not run this as I run WEP):

echo 'ENABLED=0 | sudo tee -a /etc/default/wpasupplicant

Reboot.

Source: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/func,view/id,362/catid,2/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/func,view/id,362/catid,2/)

---

### Post by RomeReactor on 2007-07-28
This [Ubuntu documentation]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d?highlight=%28WifiDocs%2FDevice%29") page explains how to enable your wireless card. According to the instructions given, you need to uninstall Network Manager in order to install WICD, since NM doesn't work with your card and conflicts with WICD.

---

### Post by anewguy on 2007-07-28
Since your lspci showed a bcm4318, I would suggest you follow the instructions you found in my other post.  You can even download the file from Gateway if you want to following the instructions and extract the 2 files needed.  I would think that would work on your 4318 as well.  As far as network manager goes, I have no problem using network manager, but prefer network-manager-gnome.  It is very easy to use.  Either way, once you have the correct drivers in I would think they should be visible in network manager.

Please note that before following my other post, you should remove the driver you installed with ndiswrapper.  To do so, open a terminal and type:

sudo ndiswrapper -r usmaxga

Please try this and my other link - I think you will be glad you did!  Post back your results, so if there is a problem after following the other post we can try to work out your problem.:)

---

### Post by paker on 2007-07-28
Thank you for all the help you have been giving me. I have a different kind of issue that I need to take care of urgently.

Last night I removed Network Manager (NM). With NM gone, I lost internet connection and couldn't follow through the instruction. I should have downloaded the required files before removing NM. I am using another computer to post this.

I need to put NM back in the computer. I know I can reinstall Feisty. Is there a way around it? Somehow download NM to a thumb drive and install from it? Thanks.

ANewGuy:

Once I get internet connection back, I will try your method. I was hesitant because I was afraid of crashing the computer. With the computer crashed already, I am not as concerned now. Thanks.

PS: I only removed Network Manager. I still should have Network Manager-gnone in the computer. But I don't have internet connection.

---

### Post by RomeReactor on 2007-07-28
**network-manager-gnome** depends on **network-manager**, so if you uninstalled NM, it took NM-gnome with it. Try reinstalling them through Synaptic or the command line, as the .deb packages might still be on your system:
```
sudo apt-get install network-manager network-manager-gnome
```
or add your installation CD as a repostirory in Synaptic, so it can be fetched from there (insert your CD in your system, then go to Synaptic->Settings->Repositories->Third-Party Software->Add CD-ROM, press the **Reload** button, and try installing it again).

---

### Post by paker on 2007-07-28
Rome Reactor:

I wish I had half of your knowledge. Without knowing I could install from CD, I reinstalled Feisty fresh. It took half day basically with my "light" cable connection. Now I am ready to restart the whole process. I will write back soon. Thanks.

---

### Post by RomeReactor on 2007-07-29
> **paker said:**
> Without knowing I could install from CD, I reinstalled Feisty fresh. It took half day basically with my "light" cable connection. Now I am ready to restart the whole process. I will write back soon. Thanks.

I cannot assure you that the **network-manager** and **network-manager-gnome** packages are available in the installation CD, but I'm almost certain they are since they are part of the default installation. However, seeing as you already reinstalled Feisty  hopefully you didn't lose any important data in the process. As I said before, I don't have a Broadcom card and can't guarantee the procedure will work; while the installation of the drivers with NdisWrapper is a fairly uncomplicated thing (once you know the process), it's all really about having the correct drivers for your card. Having this experience behind you will make installing the drivers next time a less daunting task. If you have further trouble, post back. I'll try to help however I can, and perhaps someone who actually has the same card as you can provide you with more accurate instructions.

---

### Post by paker on 2007-07-29
I found several bcm4318 installation guides in this forum. Because of my inexperience, I chose the simplest procedure, and it worked. Thank you for all the help you gave to me. It was the first time I used ndiswrapper, 7zip, cabextract, shield, tar. I think I learned a lot.

---

### Post by RomeReactor on 2007-07-29
Glad you got it to work! Just for reference, you could post your card model again and which procedure you followed, so anyone reading this thread having the same problem can get it working too.

---

### Post by anewguy on 2007-07-30
For those of you looking for a step-by-step that is fairly easy to get your bcm4318 wireless card working, you may want to see my post [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=507505").

It deals with installing Ubuntu on a Gateway MX3215.  You can skip the part that says to download the Ubuntu CD image and actually install Ubuntu - what you want to pay attention to is in the first section - get a copy of the driver file as I show how and then get wireless working as I also show.  After the wireless works, everything else in that post can be ignored.  If you need things separated, just let me know.:)

---

### Post by paker on 2007-07-30
I found several threads on bcm4318, including anewguy's [http://ubuntuforums.org/showthread.php?t=507505](http://ubuntuforums.org/showthread.php?t=507505). Being  newbie, I selected a procedure that appeared to be the simplest, this thread here [http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318)

Though it's success rate is about 2/3, I decided to give it a try. Downloaded bcm4318*.tar file, untar-red it, and ndiswrap-ped it. I have no idea how it's different from other methods. I am too ignorant to know the difference.

---

