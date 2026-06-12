---
title: "Big time oops"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Incite on 2008-02-22
Ok i deleted everything on my computer while installing ubuntu, (at least i think so) my computer was a vista until now and i have no idea what to do. If i did lost all my stuff then so be it but, can anyone tell me how to view my drive space and how to install some of my old programs like my zune software. limewire and other apps. i have no idea what to do.

I dont know how to get the wireless to work.

---

### Post by seventhc on 2008-02-22
could you please post the output of this
*Applications>Accessories>Terminal*
```
sudo fdisk -l
```

---

### Post by spiderbatdad on 2008-02-22
```
df -h
``` will show you how much space avaialble in your file system.

---

### Post by Incite on 2008-02-22
will1337@WILL:~$ 


where is this code thing?

---

### Post by seventhc on 2008-02-22
wow nice command there....
I like it
```
df -h
```

---

### Post by Incite on 2008-02-22
Help Help

Sos

---

### Post by seventhc on 2008-02-22
we are helping, but you will have to post the output of one of those commands....
Please do so. :)

---

### Post by Incite on 2008-02-22
code: df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             145G  2.1G  135G   2% /
varrun                474M   96K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
udev                  474M   68K  474M   1% /dev
devshm                474M     0  474M   0% /dev/shm
lrm                   474M   34M  440M   8% /lib/modules/2.6.22-14-generic/volatile

code: sudo fdisk -l
[sudo] password for will1337:

---

### Post by seventhc on 2008-02-22
yikes...sorry but it looks like windows is gone...:(
to double check run the other one...
```
sudo fdisk -l
```
but to me it looks like it's gone :(

---

### Post by Incite on 2008-02-22
I thought so. Can anyone tell me some of the apps that wont be compatible can i get my zune software back, or my dvd to mp4 converter.

What is my equivulant (sp) to Microsoft word?

---

### Post by DingsBumps on 2008-02-22
MS Word <-> Open Office Word Proccessor

---

### Post by Duck2006 on 2008-02-22
> What is my equivulant (sp) to Microsoft word?

Openoffice.

---

### Post by zabien1970 on 2008-02-22
Look under  Applications>Office  for Open office apps

for your wireless post the output of  lspci

---

### Post by Incite on 2008-02-23
Wireless output:
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0531 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

What does that mean?

I cant get the screen size/ resolution correct.

I have a compaq presario v6000

---

### Post by zabien1970 on 2008-02-23
Try this link for your wireless [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/")

Do you happen to know what video card you have

---

### Post by Incite on 2008-02-23
I dont know what card i have.

Is there an app to install zune software by microsoft?
And to open word documents from my flash drive or can i just plug it in?

Powerpoint equivilant(sp)

---

### Post by sayakb on 2008-02-23
> **Incite said:**
> I dont know what card i have.

Is there an app to install zune software by microsoft?
And to open word documents from my flash drive or can i just plug it in?

To install any Windows app, you need to install Wine

Open a terminal and type:

```
sudo apt-get install wine
```

---

### Post by sayakb on 2008-02-23
@OP
Btw, there is no assurance that all Windows apps would work on Ubuntu. There are separate apps for linux. To check whether your app is compatible with Wine (Windows emulator) goto appdb.winehq.org

---

### Post by Incite on 2008-02-23
What would i be looking for to install the zune software.

sry for the dumb questions but im learning how to use an os that i have never seen before.

Btw i was trying to duel boot linux but i ended up with only linux and i dont have a copy of vista or xp.

---

### Post by billgoldberg on 2008-02-23
Zune media player (I believe this is what you mean by zune software) won't work under wine.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9801&iTestingId=17571](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9801&iTestingId=17571)

---

### Post by philinux on 2008-02-23
Wow the thread title says it all. Welcome to the club. You took a mighty plunge but there's plenty of help here. 

Advice:
Dont panic. Ask here first if your unsure about anything.
Read the sticky threads.
Post a separate thread with each problem.

Have fun. :)


edit: Found this for Zune. [http://www.zuneboards.com/forums/zune-hacks-mods/2772-zune-linux-progress.html](http://www.zuneboards.com/forums/zune-hacks-mods/2772-zune-linux-progress.html)

---

### Post by sayakb on 2008-02-23
@OP
Did you somehow select the Guided (Use the entire disc) option at the partitioner during Ubuntu installation? Also, if you are dependent on Windows softwares, you may install Windows by making a virtual machine:

```
sudo apt-get install virtualbox
```

But not all USB devices, plug n play devices, games (that need higher GPUs or graphics processors) since VBoxes dont offer good graphics.

---

### Post by Incite on 2008-02-23
I really wish i had any idea what this means:

Since I haven't heard much from anyone here on this front I will post my current progress. I have in no way created any mentioned programs or contributed any amazing code, this is just what I have learned/accomplished by doing everything I can on Linux to get into my Zune.

Important Software:
Amarok 1.4.5 (compiled with libmtp support)
libmtp 0.1.3
VMWare-Player with Windows XP SP2 installed

What I can Do:
View songs on Zune
Delete Songs from Zune
Sync songs from Zune to Linux PC

How:

View Songs on Zune:
All you need for this are Amarok compiled for libmtp and libmtp (only tested with 0.1.3)
In Amarok go to Settings>Configure Amarok>Media Devices
Now add an MTP Device and name it Zune
In the main Amarok window select the Media Devices tab to the left on the bottom.
Now go to the dropdown list just below where it says connect and disconnect.
Choose the Zune MTP device.
Now click the connect button.
Give it some time and your music list should populate.


Lets just PRETEND that i have no idea what the commands are and that every app install i have ever done only required yes or cancel chooses.Lets just pretend. Where would i find the steps to install apps like this on any others and how?

---

### Post by Incite on 2008-02-23
i think i did partition the entire disk. i tried to do one of the drives in my system but i could not. 

There is (i think) a 8 gb hd that was used for system recovery that i tried to put linux on but it didnt work. i have no idea really.

---

### Post by forestpixie on 2008-02-23
if you do 
```

sudo fdisk -l
```

you can see what partitions you have, it's likely that the partition you're talking about is the vista recovery partition

---

### Post by matchstich on 2008-02-23
What is my equivulant (sp) to Microsoft word?[/QUOTE]


i use abiword

---

### Post by Incite on 2008-02-23
> **forestpixie said:**
> if you do 
```

sudo fdisk -l
```

you can see what partitions you have, it's likely that the partition you're talking about is the vista recovery partition

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93f73831

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19104   153452848+  83  Linux
/dev/sda2           19105       19457     2835472+   5  Extended
/dev/sda5           19105       19457     2835441   82  Linux swap / Solaris

---

### Post by forestpixie on 2008-02-23
I think you did what you thought you didn't - it's just linux on there

as far as your post 23 - what is it you're actually after there?

---

### Post by Incite on 2008-02-23
> **forestpixie said:**
> I think you did what you thought you didn't - it's just linux on there

as far as your post 23 - what is it you're actually after there?

I want to be able to install this:[http://www.zune.net/en-us/products/zunesoftware/download.htm](http://www.zune.net/en-us/products/zunesoftware/download.htm)

and limewire

---

### Post by seventhc on 2008-02-23
frostwire is better, it's like limewire but no pop ups trying to get you to buy it.
Need to have java installed.
if you want to try it, open a terminal and paste this in
```
sudo aptitude install frostwire
```

---

### Post by Incite on 2008-02-23
Were is it after u install it. I cant find it in the comp. same with the limewire i installed i cant  find things. 

and i kind of need the zune software at least to take the music off of the zune device.

---

### Post by Incite on 2008-02-23
How do i play dvds? i put one in and i didnt work.

---

### Post by forestpixie on 2008-02-23
sorry - no idea about the zune thing :) - it appears to be a bit of a problem from waht I can see, although you might be able to get it going through one of the virtual machines, vmware or virtualbox - if you've got a win disc you can set up in a virtual

---

### Post by sayakb on 2008-02-23
@OP
You can play the DVDs on VLC player. 

```
sudo apt-get install vlc
```

---

### Post by AvgUser on 2008-02-23
Incite:  Your best bet could be to start from scratch.  Your choice, but you have a little learning curve to adjust to and Dual Boot is very helpful in overcoming this on your own timeline.

Do a system recovery for your Vista (Give Compaq a call & see if they have a DVD restore solution as it appears you have clobbered your restore partition).. Then boot to and install Ubuntu ensuring you do not destroy these again with the new install.

I would recommend having a second hard disk in your system to dedicate (An older 10+Gb is perfect) as this minimizes the possibilty of complications with Dual Booting. Bonus: If you go nuts trying, you can just pull that drive and your Vista is still intact.

PS:  Frostwire is similar to Limewire, without all the Spam/Nags/Pops.  I've only used this on Hardy, but my experience using this was a bit challenging at first due to Java.  Once I installed IcedTea it seems to work fairly good, I stay away from using the player feature as it hangs with Totem occasionally on my system.

---

### Post by Incite on 2008-02-23
After the install then what? 
The dvd is not playing. i feel like a diot.(idiot)

---

### Post by Incite on 2008-02-23
I really dont want to start over again. I have plenty of time i just need some apps to work now. while i learn the system. What are some of the capibalities of the virtual box.

The apps i need to work are limewire or frostwire (i think i installed it) and a dvd player and recorder. to copy the dvds that i just deleted from my harddrive.

---

