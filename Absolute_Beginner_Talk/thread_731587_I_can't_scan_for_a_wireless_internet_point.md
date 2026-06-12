---
title: "I can't scan for a wireless internet point"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by dajohnster on 2008-03-22
I sure hope not because I'm stumped. I guess I'm new to this, but I'm not really new to computers. The problem is I can't access the internet when I'm logged in on my Linux part of my partition. Before all that though I'd like to say, thank you. I'm very glad to become part of the Linux community. Moving on I guess the real problem is that I can't scan for a wireless internet point. Any help would be really nice. If you could shoot me an e-mail at [email]Dummygonuts@yahoo.com[/email], or my IM name is [email]Dummygonuts@hotmail.com[/email]

---

### Post by uDanimal on 2008-03-22
What type of wireless adapter are you using?  I don't have a LOT of experience with Wireless in linux, but I am learning (thanks to my other Ubuntu PC) that wireless can be quite tricky to set up in Linux.  I usually involves using NDISwrapper (I dont remember the address for their site, but Google does, lol)

Maybe if you post your hardware specs some of the other old trolls around here can help you out more than I can.

---

### Post by cisforcojo on 2008-03-22
Well said. We need to know what kind of wireless card you're using before we can help you out. :)

---

### Post by hums07 on 2008-03-22
> **dajohnster said:**
> I sure hope not because I'm stumped. I guess I'm new to this, but I'm not really new to computers. The problem is I can't access the internet when I'm logged in on my Linux part of my partition. Before all that though I'd like to say, thank you. I'm very glad to become part of the Linux community. Moving on I guess the real problem is that I can't scan for a wireless internet point. Any help would be really nice. If you could shoot me an e-mail at [email]Dummygonuts@yahoo.com[/email], or my IM name is [email]Dummygonuts@hotmail.com[/email]
Welcome to Linux, Ubuntu, and Ubuntu community :).
We need more detailed info before we can help you solve your own problem.
Regarding email, you can subscribe to a thread so you can automatically receive a message when your thread gets a response.

---

### Post by dajohnster on 2008-03-22
Well I suppose this problem complicates itself due to my own ignorance. I'm running the 64 bit version of Ubuntu 7.10. I'm fairly certain I have a 64 bit computer, but I honestly don't know how to find detailed information about my computers hardware.

---

### Post by which_chick on 2008-03-22
Go into a terminal window (applications->accessories->terminal)
Type

> lspci  

and hit enter.  This will give you a big list of stuff.
(that first is an L and not a 1)

In the list of stuff will be your wireless, assuming it's detecting at all.

Mine says

0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

so I have a Broadcom BCM94311MCG wireless card.

Note that this will be buried in a pretty big list.  Take your time and read carefully -- look for "wlan" or "wireless".  Good luck.

To exit the terminal window, you can type

> exit

and press enter.

---

### Post by dajohnster on 2008-03-22
Alright great that was painless! Here's what I think is the right info:
04:08.0 Ethernet controller: Broad Corporation BCM4401-B0 100Base-TX (rev 02)
That's the exact line.

---

### Post by which_chick on 2008-03-22
Okay, That LOOKS like one that Dell puts in for linux, so probably there are drivers somewhere.  (Information from [http://hardware4linux.info/component/14166/](http://hardware4linux.info/component/14166/) )  On a guess, though, I'd say it was an ethernet card rather than a wireless connector.

Could you post the entire list?  Maybe we're missing something, here.

---

### Post by dajohnster on 2008-03-22
Alright here the entire entry:
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
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
04:08.0 Communication controller: Conexant HSF 56k Data/Fax Modem

---

### Post by which_chick on 2008-03-22
Okay.  That was part of the problem.  I think that this

> 01:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

is your wireless card.

I have a 

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
AND a 

0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

but you do not.  I expect your wireless card is the Atheros thing that says "Wireless PCI Express Adapter".  Okay.  I'm looking for some stuff, so hang in there.

---

### Post by which_chick on 2008-03-22
Next thing -- there are supposedly drivers for this Atheros wifi thing.  

*IF* your card is identifying itself correctly (some don't -- "There is a chance you really have a 5007EG that is misidentified as a 5006EG, which is not supported unless you are running the SVN version of Madwifi with a patch. Not saying this is definitely your issue, but I ran into this, and other people have too." as noted at [http://www.linuxquestions.org/questions/linux-hardware-18/using-the-atheros-wireless-driver-593047/](http://www.linuxquestions.org/questions/linux-hardware-18/using-the-atheros-wireless-driver-593047/) ) but for now we are going to assume that the card IS identifying itself correctly... then there are drivers and we should be able to install them.

First thing to check:  System->Administration->Restricted Drivers Manager.  See if there is anything in there about Atheros.  If it's there, is it checked?  (If not there, report that.  If there and not checked, put check in, see if that helps.  If already checked, report that.)

Let me know.

---

### Post by teryowen on 2008-03-22
i think what you need is here:

[http://www.aircrack-ng.org/doku.php?id=madwifi-ng](http://www.aircrack-ng.org/doku.php?id=madwifi-ng)

```

ifconfig ath0 down
ifconfig wifi0 down
svn checkout http://svn.madwifi.org/madwifi/trunk/madwifi-ng
cd madwifi-ng
./scripts/madwifi-unload
make
make install
depmod -ae
modprobe ath_pci

```
edit: for some of the commands you will need to use sudo


i did this earlier and it worked make sure you're connected to the internet by cable though

---

### Post by dajohnster on 2008-03-22
It's checked, enabled and inuse.

I'm not connected to the internet by anything

---

### Post by cisforcojo on 2008-03-22
Ok then you'll want to go to System -> Administration -> Network and first try connecting to your wireless network via a 'manual' setup, ie. not roaming (it really doesn't matter though).
What sort of wireless encryption is on your wireless network? WEP or WPA or NONE (no password)?

---

### Post by dajohnster on 2008-03-22
Well I've never had to give a password before so I assume none.

---

### Post by fela on 2008-03-22
> **which_chick said:**
> 

Note that this will be buried in a pretty big list.  Take your time and read carefully -- look for "wlan" or "wireless".  Good luck.

Just saying, but you could run this: ```
lspci | grep insert_what_you_want_to_find_here
```

to find exactly what you want in that big list.

---

### Post by ugm6hr on 2008-03-22
More info is useful:

Can you connect in your non-linux partition?
Presumably you also have Windows?  What version?  Do you know how to find out your hardware configuration from Windows?  It is usually in somewhere in Control Panel.

As mentioned, linux detects the AR5007 as AR5006.

If yours is a genuine AR5006, it should already work, with minimal fuss.

The output from the following commands may help clarify, but it would be easiest for you to look in Windows.

```
lshw -C network
iwlist scan
```

---

### Post by dajohnster on 2008-03-22
I can get on the internet when I use my Windows log in. It's Windows XP Home Edition Version 2002. Unfortunately my windows log in is super infected and my virus scanner can't even keep up. Also I don't know how to find how my hardware is configured in windows.

---

### Post by teryowen on 2008-03-22
have you tried from ubuntu what i posted earlier? about the madwifi-ng

---

### Post by dajohnster on 2008-03-22
I did and it didn't work (I assume because I'm not connected to the internet in anyway).

---

### Post by which_chick on 2008-03-22
If it's a 5007EG, there's a patch for 32-bit systems but not 64-bit.  See here:
[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

I'm pretty sure that this is the madwifi-ng that terowyn suggested.

The Madwifi compatibility list says that this card will also work via the ndiswrapper and old-driver route, a solution that might work an amd64 system.

Further card identification (seeing if it's really a 5006 or not):

In a terminal window, type

```
lspci -v
```

Read the list until you get to the "Atheros Wireless" entry.  It should look *something* like this

0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
        Subsystem: Dell Unknown device 0007
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f9ffc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

except that the first line will be 
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

In the correct entry, look at the line that starts "Memory at"

The thing you want, the memory address, is right where the "f9ffc000" is on mine.  Write the one for your card down.  It may contain numbers or letters or both.

Next, type 

```
ath_info 0xf9ffc000
```

EXCEPT put YOUR memory address in there instead of my f9ffc000  Make sure you have the 0x in front (no spaces) of your memory address, as is shown.

Let's see how that works.  Post the output here, please.

---

### Post by baracuda68 on 2008-03-22
So, maybe this is a stupid question...Can you connect to the internet in Linux, hardwired to the router..CAT5 style?

---

### Post by which_chick on 2008-03-22
Alternatively, if you have Windows XP, you can find your wifi card by the following steps:

1.  Start
2.  Control Panel
3.  Network

Inside network, look for your wireless icon.

RIGHT CLICK the wireless icon.  You should get a drop-down menu.  LEFT CLICK properties in the drop-down menu.  Next, look at the top.  It should tell you your wireless card in the "Connect using" part.

---

### Post by dajohnster on 2008-03-22
AR5007EG Wireless Network Adapter

That's what it says on Windows. On a completely different note if I delete my Temp file in the C:\Documents and Settings\Owner\Local Settings directory will it hurt my computer?

---

### Post by which_chick on 2008-03-22
Okay.  Now we know for real what the problem is.  You have a AR5007EG Wireless Network Adapter that is mis-identifying itself as a AR5006EG.

This adapter is NOT SUPPORTED under AMD64 Ubuntu.  The linux drivers that come with it from madwifi will not work and there is no way to make them work that I can find.

I'm really sorry about that.  However, all is not lost.  You have a couple of choices here, for what you would like to do to fix the problem.  I'll go over the options and you can pick one.

1.  Reinstall Ubuntu using i386 (32-bit) Ubuntu on your 64-bit system.  There *is* a fix for your wireless network card on the 32-bit system but you'll still have to download the patch and stuff, which will be another problem.  We'll worry about it if you pick this option because there *are* ways to get what you need without an active internet connection.

2.  Try using the ndis-wrapper stuff and the old drivers to get your network card to work.  This is apparently successful for some people on a 64-bit system.  Again, this may involve downloading stuff but there are ways to get what you need in windows and then boot to linux (on the same machine) and retrieve the files.  It won't be pretty, but it can be done.

3.  Buy a new, supported wireless card and install it.

As far as the Temp directory in your Windows OS, it *should* not contain anything important.  However, since your computer has been compromised by assorted viruses and things (according to what you have said), I can offer no guarantees as to what resides in there.

---

### Post by dajohnster on 2008-03-22
Well in a perfect world I would get a new card and install it myself, but seeing as I'm broke I think I'll have to go with option 1. and I got rid of the viruses without deleting the temp file, so that's good. I'm worried about installing Ubuntu again though. Will I have to cut my hard drive up even more?

---

### Post by which_chick on 2008-03-22
I would just tell it to install right over the AMD64 installation.  It should be able to re-use that part.  (You'll need to download and burn the iso for i386, obviously.)  Before starting, open a terminal window and type the following:

```
sudo fdisk -l
```

At the end, there is a space between "fdisk" and the hyphen but there is NO space between the hyphen and the l, which is a lowercase L.

The output will give you your hard drive partitions, something like the following. 

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5       23031   184964377+   7  HPFS/NTFS
/dev/sda3           23032       38403   123475590    f  W95 Ext'd (LBA)
/dev/sda4           38404       38913     4096575   db  CP/M / CTOS / ...
/dev/sda5           38078       38403     2618563+  dd  Unknown
/dev/sda6   *       23032       37460   115900879+  83  Linux
/dev/sda7           37461       38077     4956021   82  Linux swap / Solaris

```

Look at your list.  You're going to want to note down where the HPFS/NTFS stuff is (that's your XP partition).  On my list, that would be /dev/sda2.  Also note where the Linux stuff is.  On mine, that is /dev/sda6, but yours could be different.  

What you want to note, before you go do any re-installing:

1.  Where is my XP that I want to save?  

On the list you get (and yours is going to be different from mine) look for the HPFS/NTFS part.  That's your XP.  Write down the /dev/blah blah part of it.  On MY example, you'd write down /dev/sda2

2.  Where is my linux that I want to write over?

On the list, look for where it says just plain Linux.  On my list, this would be /dev/sda6.  That's where I would want to reinstall.  (The swap will probably take care of itself.)  Make sure you have noted these things down before you start to install.  If you have any other linux BESIDES the linux swap / Solaris (which is the swap space) you will want to note it down but hopefully you won't have any of that.

ALSO note which of the partitions above have little stars * after their names.  THESE are the bootable ones.  You should have ONE bootable "Linux" and ONE bootable "NTFS".  The NTFS one is your Windows XP.  The Linux one is your Ubuntu.  This is a double-check for you to make sure you don't mess up and pick the incorrect things.

I have not done a "live CD install b/c it won't work on my laptop.  I used the alternate install and that worked fine.  Even though I have not seen the "live CD" install, it should, at some point, ask you where you want to install the linux.  (It does.  This is under the "Prepare Disk Space" part of the install.)

When you get to Prepare Disk Space, pick "manually partition the disk" 

You should get a list of partititions - choose the one which corresponds to your existing installation, (Remember, you should have it written down as the answer to #2, above.)  Highlight it and click the 'edit partition' button - you'll get a new screen with mountpoint option - choose / and save or close that screen. Now you'll be back in the first screen - pick the same partition (your linux partition) again and put a tick in the 'format' box - DO NOT MARK ANY OTHER BOXES.

Then just tell it OK because it is already manually partitioned properly.

Hope that this helps.

---

### Post by cisforcojo on 2008-03-23
For a new user, I'd recommend using the 32bit system anyway. From what I've seen, the 64bit system can really be a headache and you might run into some software problems. Once you become more familiar with linux, you can could then consider making the switch. I think starting with a 64bit system is just too much to take on when you're getting started. Keep it simple. :)

You'll be fine with the reinstall. Actually you shouldn't change ANY of your partitions. Leave them. The only operation you should do is reformat them (not the windows one obviously).

EDIT: By the way, great job which_chick. Great attitude. :) You're really going out of your way to help. Gave you a 'thanks' for your efforts.

---

### Post by dajohnster on 2008-03-24
Alright it's reinstalled and all taken care of, but I'm still having the same problem. Also it's not reading my video card, and during installation I got and error massage that said Security files could not be accessed, or something like that.

---

### Post by which_chick on 2008-03-24
Reinstalling onto i386 architecture is the first part of what we have to do to get this working.

From what I remember, we're working on option 1, here.

> 1. Reinstall Ubuntu using i386 (32-bit) Ubuntu on your 64-bit system. There *is* a fix for your wireless network card on the 32-bit system but you'll still have to download the patch and stuff, which will be another problem. We'll worry about it if you pick this option because there *are* ways to get what you need without an active internet connection.

You are now at the point where you need to get and install the patch for the wireless network card to make it work.  If I recall correctly, you have a working Windows Vista installation *with internet* on the same machine as your Ubuntu-without-wireless.

You're going to use your Windows installation to go online and get the patch discussed here: [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679) -- the direct link to the file you need is below:

[http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)

Save that file to your desktop in Windows (don't try to open it or anything, just "save to desktop").

Then, boot into Ubuntu.  Go to "Places" at the top.  Select "Computer" -- this brings up the File Browser, where you can look at stuff.  You will get some boxes there.  Each box is a hard drive or a USB flash drive or a CD ROM drive.  It's drives, basically.  Assuming that you aren't mounting your windows partition as an NTFS directory on your main linux partition (so that you can play your mp3 files), your windows computer stuff will show up in here as one of the drives.

Eliminate the obvious not-your-windows-disk items... for example, "CD-ROM" is not your windows disk.  "USB Flash 2.0 GB" is a USB flash drive, not your windows disk.  

Once you have narrowed things down to the likely suspects, you are going to double-click on each one, in turn, until you find your windows disk.  (The windows disk is the one that has a folder labled "Windows" in it.  There will be other stuff, lots of folders, so make sure you scroll down to see everything.)

Once you have found your windows disk, you are going to hunt for the file you downloaded.  You will need to browse to your desktop.  USUALLY the desktop is located in C;\Documents_and_Settings\Your_Username\Desktop.  (At least, it is in XP.  I have no idea where it is in Vista but I'd be surprised if they moved it.)  You can pre-test this in your Windows OS by going in to My Computer and hunting around for where your desktop is.  (Take notes if needed.)  

Hopefully, you will be able to find the madwifi file from the Ubuntu file browser.  Once you have found the madwifi-nr-blah blah blah file, you are going to right-click it and select "copy".  Then, go to your Ubuntu desktop.  Right click on a blank space and then left-click "paste".  This should paste the file you need to your desktop.

If you get that far, post back here and we'll proceed.  If something goes wrong, let me know that too.

Hang in there -- we'll beat this thing yet.  :)

---

