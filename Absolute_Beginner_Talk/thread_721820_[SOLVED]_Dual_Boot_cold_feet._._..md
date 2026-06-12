---
title: "[SOLVED] Dual Boot cold feet. . ."
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Helios1276 on 2008-03-11
Ok, so I have played with the ubuntu live cd and I'm ready to make the jump to a dual boot( hopefully).
I'm a complete noob by the way, I shouldn't be allowed smell the beans let alone have any. My question is concerning my laptop and how i go about setting it up for a dual boot and what i should be doing in prep.
I've started clearing stuff up on the hd to make room for ubuntu and a few de-frags before the big jump and i have run into problems. I'll take any advice or tips gratefully and with the utmost glee!

1) My hd is already partitoned= 80gb - acer c:35gb - acer d: 35gb, im guessing the other ten is system restore which ive no idea around or if i should keep?? I dnt have an xp cd...

2) While playing with the Ubuntu live cd i noticed i couldnt play with the graphics/effects settings or connect to the internet, does this mean i have work ahead of me with the relevant hardware?

3) with a dual boot ill be able to save stuff to a partition that both os can access ( e.g. email,pics,music,video) ??

4)As an extra it would be nice to hear from other ppl who set theirs up and their experiences, I'm a student ( english not electronics sadly lol ) so my comp is used for net,wprocessing,music,video,downloading etc 

Cheers for listening and for any help you can give!:)

MY System: Acer Aspire 5672 wlmi , core duo t2300 1.66ghz, ATI x1400, 1 gb ddr2

---

### Post by neurostu on 2008-03-11
So here is my advise:

Create 3 partitions.
1 for windows system files
1 for ubuntu system files
1 to share files between the systems

While ubuntu can read the windows file system occassionally windows can freak out when linux starts writing to its file system.  This is the way that I have things set up.

I'm not surprised that you couldn't mess with the graphics, that is common on the live cd.

How did you try to connect to the internert, LAN, WIFI?

I personally don't really like the OpenOffice suite and a good word processor replacement is AbiWord.  Also if you want to use the MS Office suite you can run it natively in linux if you have CrossOver Linux, I think you can get it to run on Wine but I'm not sure.

Congrats on decided to make the jump. Good luck and have fun. If you have any questions post back here!

---

### Post by jonnywombat on 2008-03-11
Hi there..

First off you should see if you are able to make a set of recovery or restore disks in windows.. this is normally an option that you are offered when the machine comes with a restore partition. If you can make these disks you can then delete the restore partition without any issues.... If not and you intend to continue to use windows then best hang on to it.

The next job is to remove all the clutter on your windows partitions.. and as you have done defrag 2 or 3 times...

Then I prefer to use the alternate install cd, but the live cd will work fine... Start in the install process and when you get to the partitioning options you are going to select the manual option..

resize the your windows partitions down to create at least 10 gb of space.... 

Format the free space to ext3 and create a new partition.. select the mount point as "/" and install ubuntu to that partition.

You will be able to access both your windows partitions from ubuntu but not your ubuntu partition from windows. So store your data in your D: partition (note ubuntu will not call it D: and you may have to mount it manually in the first instance.

You might have some work to do to get your graphics and wireless etc up and running but there are loads of threads here about that already.. just search for your specific chipset.

Jonny

---

### Post by handydan918 on 2008-03-11
> **Helios1276 said:**
> Ok, so I have played with the ubuntu live cd and I'm ready to make the jump to a dual boot( hopefully).
I'm a complete noob by the way, I shouldn't be allowed smell the beans let alone have any. My question is concerning my laptop and how i go about setting it up for a dual boot and what i should be doing in prep.
I've started clearing stuff up on the hd to make room for ubuntu and a few de-frags before the big jump and i have run into problems. I'll take any advice or tips gratefully and with the utmost glee!

1) My hd is already partitoned= 80gb - acer c:35gb - acer d: 35gb, im guessing the other ten is system restore which ive no idea around or if i should keep?? I dnt have an xp cd...

I'm assuming you don't have anything stored on the D drive? And if you don't have a xp cd, you should call acer and order one. Those restore partitions are about stupid. If you get a virus, that's the first place most of them go to replicate themselves.> 
2) While playing with the Ubuntu live cd i noticed i couldnt play with the graphics/effects settings or connect to the internet, does this mean i have work ahead of me with the relevant hardware?Maybe. A good thing to do is boot the live sc and post the output of lspci (run from a terminal).
> 
3) with a dual boot ill be able to save stuff to a partition that both os can access ( e.g. email,pics,music,video) ??
not exactly, since Windows can't natively read ext2 or ext3 partitions.If you want to set up a partion that both can read/write to and from, I still like vfat/fat32.> 
4)As an extra it would be nice to hear from other ppl who set theirs up and their experiences, I'm a student ( english not electronics sadly lol ) so my comp is used for net,wprocessing,music,video,downloading etc 
Since I've been running linux most of this millennium, I prolly can't give you a newbies impressions. I will say that even when I have to use Windows, I prefer OpenOffice to Word. As a previous poster noted, some prefer Abiword, but with your system specs, OpenOffice should be quite snappy.> 
Cheers for listening and for any help you can give!:)

MY System: Acer Aspire 5672 wlmi , core duo t2300 1.66ghz, ATI x1400, 1 gb ddr2

Enjoy!

---

### Post by bumanie on 2008-03-11
Answers as best I can
1. c: I assume is windows. What is on d:? You are probably correct in assuming that the 10g partition is a rescue of some sort.
2. From a live cd you cannot alter graphics as the live cd unpacks off your hard drive iand runs from ram. I suspect your inability to get on the internet will be due to a problem with ipv6. It can be fixed if you install. It could be caused by other issues though.
3. The latest ubuntu's have a program by default that reds/writes to ntfs, there is also an open source program for windows that allows read/write to ext3 file systems. An alternative is to create a fat 32 partition for sharing files as both ntfs and ext3 can read/write to fat 32.
4. Office apps. are installed by default in the form of open office. 
I would suggest you create a / (mandatory) for the OS system files a  swap (mandatory) partition as well as a separate /home. This way if something happens to your system you will be able to reinstall the file system and still have your saved files safe in /home.

---

### Post by Laser Dude on 2008-03-11
1.  I don't think you need to keep system restore, but it's probably a good idea to keep around.  That way, if you happen to do something that screws your system up beyond repair, you can restore it to how it was when you purchased it.

If you need to do any additional partitioning, and need to change the size of the Windows partition, you should do it with Windows partitioner.  I'm not sure about XP, but I know that Vista has files at various points in the hard drive like at the end that it needs to always be at the end, which it needs to move around for itself.  You can just use it to leave some free space, and use the Ubuntu partitioner to fill up that free space with your Ubuntu partition and any others you need.

2.  When I used the live CD I wasn't able to edit the graphics settings either, and they work fine now that I have the full system installed.

3.  This is probably of importance.  It's something I didn't realise I had to do, and now I find myself using a thumb drive to transfer data.  (oops!)

4.  I installed Ubuntu a few weeks ago, and besides partitioning everything was surprisingly easy.  It sets Grub up automatically, so dual booting is simple.  A big releif when getting Ubuntu is realising that things are done like they should be.  Updates are handled by the OS (you don't have every program running a checker on startup to check for updates), the Synaptic Package Manager is really easy to use, and it's nice to be able to edit your panels however you wish.  And the desktop cube is waay more entertaining then it should be.  :P

---

### Post by JoshuaRL on 2008-03-11
Welcome to Ubuntu!  There's a lot of really good info out there for dual booting, and it is a pretty common thing to do.  iTunes, Office, games;  theres some software that just flat runs better in Windows.  That said, there are some great alternatives for free in Ubuntu, and you might give them a try.

[Windows Dual Boot.](https://help.ubuntu.com/community/WindowsDualBoot?highlight=%28boot%29%7C%28dual%29)  [url=
https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows]Switching From Windows.[/url]  [Ubuntu Equivalents to Windows Applications.](https://help.ubuntu.com/community/WindowsApplicationsEquivalents)

Now for your questions.

> 1) My hd is already partitoned= 80gb - acer c:35gb - acer d: 35gb, im guessing the other ten is system restore which ive no idea around or if i should keep?? I dnt have an xp cd...
Its always a great idea to defrag right before install, it will negate almost all overwriting issues.  But if you already know the partition you want to use for Ubuntu, you're doing great.

> 2) While playing with the Ubuntu live cd i noticed i couldnt play with the graphics/effects settings or connect to the internet, does this mean i have work ahead of me with the relevant hardware?
If you were using any other way to connect than an ethernet port, then there might have been issues.  Some wifi cards are supported, some need to use the windows driver with a program called ndiswrapper.  If you post your wifi card and chipset we can help with that.  

> 3) with a dual boot ill be able to save stuff to a partition that both os can access ( e.g. email,pics,music,video) ??
Linux wil be able to read Windows partitions, but not the other way around.  I have a dual boot with windows where I left all my music on the Windows Partition.  I just pointed the Media Player there, and it works great.  Not sure how well email will be though.

> 4)As an extra it would be nice to hear from other ppl who set theirs up and their experiences, I'm a student ( english not electronics sadly lol ) so my comp is used for net,wprocessing,music,video,downloading etc
I really like Ubuntu.  I converted my laptop over in late November and love it. Almost all the programs are free and really good.  Ubuntu is by far more secure than any Windows varient, and has security holes patched within hours or days usually instead of months for Microsoft.  For security in Ubuntu, read the definitive [Security Post by bodhi_zazen.](http://ubuntuforums.org/showthread.php?t=694198)  I had some problems with the ATI video card (thats a common complaint, the drivers for them aren't as good as for Nvidia in Linux).  So I looked up your card and found [HOWTO on the forums.](http://ubuntuforums.org/showthread.php?t=574302)

Hope all that helps, and again Welcome!

---

### Post by Victormd on 2008-03-11
> **Helios1276 said:**
> 
1) My hd is already partitoned= 80gb - acer c:35gb - acer d: 35gb, im guessing the other ten is system restore which ive no idea around or if i should keep?? I dnt have an xp cd...
You should create system restore DVDs and get rid of that partition. That's the only reason why it's there.

> **Helios1276 said:**
> 
2) While playing with the Ubuntu live cd i noticed i couldnt play with the graphics/effects settings or connect to the internet, does this mean i have work ahead of me with the relevant hardware?
It's normal that the graphics/effects settings don't work. Don't worry. You might have some minor problems if your graphics card is an ATI but that's easy to fix.

> **Helios1276 said:**
> 
3) with a dual boot ill be able to save stuff to a partition that both os can access ( e.g. email,pics,music,video) ??
Ubuntu can read/write to your windows partitions but this is not reciprocal. You'll have to install a software under Windows to read the ubuntu partition.

> **Helios1276 said:**
> 
4)As an extra it would be nice to hear from other ppl who set theirs up and their experiences, I'm a student ( english not electronics sadly lol ) so my comp is used for net,wprocessing,music,video,downloading etc 


Net uses: *****
word processing: ****
music: *****
video *** (if you want youtube videos you'll need some minor work arounds)
downloading *****

---

### Post by Helios1276 on 2008-03-11
just read all the replies there and wanna say thanks to you guys , the friendliness of the community alone is a big push towards Ubuntu/Linux.

ok to clarify a few points you guys rasied.

1. will i be able to get rid of the annoying 'hidden' 'security' part of my hd when i begin partitioning as i have no diea how to do it as it stands.

2. Im not overly worried about not having a backup xp cd ..i can acquire one as needed lol ;)

3. I connect to the net wireless to a belkin router at home, the light was flashing like crazy on it so i assum e ( with no credentials lol) it's a driver porblem?

4. The partition that came pre loaded ( acer c:/d:), it does have stuff on both:( ..im currently wrestling with clearing space and what to do with what i want to keep. do i 'break' this partition now before i get to the scary part of actually doing 3 partitions for the dual boot ??

Again , a massive thanks to all who are helping me, if you ever need something proof read or your guitar tuned im there! lol

---

### Post by bumanie on 2008-03-11
1. As far as I know you can format the 'hidden' (aka rescue) partition if you wish to. It frees up 10g extra, which never hurts.
2. That one is entirely up to you - no comment. lol.!!!
3. Ubuntu has most drivers that are necessary - could be a driver could be ipv6, could be something different. Can't tell until you install and try a few things.
4. To get the three partitions as I suggested, when you get to the partitioning stage, you will need to choose manual (last choice on the list). 5-6g is enough for / swap is usually 1.5-2x more than your physical ram ie if you have 512mb, use a 1g swap and then it is up to you how much to dedicate to /home. I personally don't use ntfs-3g as I have no need for windows, have it for the kids - they deserve everything they get (viruses, spyware etc) by wanting to use an inferior OS.
By the way I have the alpha 6 of hardy heron better than gutsy.

---

### Post by louieb on 2008-03-11
One thing you might try search the internet and see if there are any Linux nerds in your area. They often meet in what called a LUG ([Linux User Group]("http://www.linuxquestions.org/questions/linux-user-groups-lug-51/")). There is a  [Ubuntu LoCo Team ]("http://ubuntuforums.org/forumdisplay.php?f=183") section in this forum.

---

### Post by weezy8802 on 2008-03-11
As far as the partitioning, ubuntu comes with gpart which allows you to modify your partitions as needed.There are several threads about partitioning drives. And it is a bit different in terms of installing applications. The internet issues may be solved with the install if not than search for a driver for your particular wireless card.

---

### Post by Helios1276 on 2008-03-11
I'm still wondering if / how i go about getting rid of the pre-existing partition on my xp before adding ubuntu to the mix and how i RECLAIM the 10 gb restore part . Cheers for the heads up on the local linux group..my housemates are officialy disgusted with my ubuntu excitement now lol

---

### Post by neurostu on 2008-03-11
You can use GParted on the ubuntu live CD to reclaim your partitions
I think its found under Applications --> System Tools --> Gparted.

Its a partition editor like Partition Magic

---

### Post by Helios1276 on 2008-03-11
So I finish cleaning up my xp and defragging and then install ubuntu and at that point ill be able to have just one partition for xp, one for /home, swap etc and ill get my xp restore 10 gb back?? sorry if you have answered this and i havent gotten it ..its late and im running on pure enthusiasm fumes lol

---

### Post by bumanie on 2008-03-11
It would be prudent to defrag you windows partition prior to installing ubuntu. As far as your question goes about how to get rid of the rescue partition, the ubuntu partitioner will do that for you. All you have to do is ensure you don't overwrite your windows information. An alternate approach is to download gparted live cd and boot off that. It gives you a graphical view of your hard drive. It has sliders etc that you can use to shrink your windows partition to the size you want and then make the rest a) unallocated or b) you could format the unallocated part to ext3 or 3) you could format the unallocated part to ext3 and set up a / swap and /home with gparted. When you then boot form the ubuntu live cd, the ubuntu partitioner should be able to recognise those partitions. Personally, if using gparted I would choose b) and manually set up the / swap and /home at that point of the install. Hope this helps.

---

### Post by neurostu on 2008-03-11
Before you install you should open up GParted on the live cd and set up the partitions the way you want them

You are going to have to manually delete the restore partition that is present.
You are going to have to manually resize the partitions to what you want them to be.

When you create your ubuntu partition set the mount point as "/"

---

### Post by Helios1276 on 2008-03-11
Thanks again Bumanie, I think I have sufficient info now to go ahead and start. I just wanted to be uber cautious at this point. Im gonna finish the xp cleanup and start the install in the morning.

---

### Post by bumanie on 2008-03-11
Yes, it is always a good policy to be cautious. Good luck in the morning. Hope it all goes well.

---

### Post by JoshuaRL on 2008-03-11
And I would suggest the Parted Magic Live CD.  Its a fork off of the GPartEd CD, and it has a full Xwindow session on it with a browser so you can check the web for help if you need it.

[Parted Magic](http://partedmagic.com/wiki/PartedMagic.php)

---

### Post by Victormd on 2008-03-12
> **Helios1276 said:**
> 1. will i be able to get rid of the annoying 'hidden' 'security' part of my hd when i begin partitioning as i have no diea how to do it as it stands.
Yes. You can delete it directly from XP using the disk manager or you can delete it during the instalation. As I mentioned before, you might want to back it up on DVDs before doing that because of the drivers - if you need them... (companies usually ship a software pre-installed, to do the backup)

> **Helios1276 said:**
> 3. I connect to the net wireless to a belkin router at home, the light was flashing like crazy on it so i assum e ( with no credentials lol) it's a driver porblem?
Gutsy is known for not being very friendly with wireless. I had to struggle a bit to ge wireless working on my wife's laptop (it's an HP), but now it works fine! Though it doesn't apply to your laptop, this will give you an idea of some of the issues others are having.
[https://wiki.ubuntu.com/HP_dv6000_Series#head-ddee0d7bdf81f47c61e7086e193c9620d026541a](https://wiki.ubuntu.com/HP_dv6000_Series#head-ddee0d7bdf81f47c61e7086e193c9620d026541a)

> **Helios1276 said:**
> 4. The partition that came pre loaded ( acer c:/d:), it does have stuff on both:( ..im currently wrestling with clearing space and what to do with what i want to keep. do i 'break' this partition now before i get to the scary part of actually doing 3 partitions for the dual boot ??
my honest opinion... if you're going to get rid of the "recovery partition" do it now (using XPs disk manager), format it using NTFS and use it to back up all your data... That way, you don't have to worry about losing anything...

---

### Post by Helios1276 on 2008-03-13
i decided to just go ubuntu all the way..having problems lol

Mainly the graphics card and wireless, im not a tech head more an enthusiast so stormy waters ahead :(

---

### Post by alphaniner on 2008-03-13
I didn't read all the posts but I thought I'd chime in about the networking issue.  I don't use wireless, but I have run the live CD with 5 different mobo onboard NICs and they all worked with a little help of the terminal.  For starters, can you fun ```
ifconfig -a
``` in the terminal please? Also, do you know if you use DHCP (get an IP address automatically) or static IP (enter numbers manually) in windows?

---

### Post by Victormd on 2008-03-13
> **Helios1276 said:**
> Mainly the graphics card and wireless, im not a tech head more an enthusiast so stormy waters ahead :(

What is your wireless card model?

Just saw that you have an ATI. What issues are you having? Resolution issues? speed? getting the desktop effects to work?

---

### Post by Helios1276 on 2008-03-14
hey guys , excuse the delay! 

1) its dhcp, the card finds the network but i cant connect

2)802.11a/b/g

---

### Post by Helios1276 on 2008-03-14
..with the ATI its low resolution, no 3d effects etc, i cant change the desktop effects level for example

---

### Post by bumanie on 2008-03-14
Hi there, it's me again. I believe your problem with connecting to the internet is due to the ipv6 issue I mentioned the other day.
Open firefox. In the address bar type
about:config
then in the filter type ipv6
Right click on the line that appears and left click on toggle to change the value to true.
You should now be able to connect to the internet.

---

### Post by Helios1276 on 2008-03-14
hey bumanie, good to see ya back,I tried that and had no luck, though it could be something i did earlier ? i think im stuck in 'maual configuration' as opposed to the simple 'wireless connection ' i had earlier:confused:

---

### Post by bumanie on 2008-03-14
I'm no expert on internet connections, however, I have had to use the ipv6 trick a number of times. Another thing that often works is to blacklist ipv6. You could try that, but may be what you have tired before may interfere or may be it is a pure wireless issue. I am aware that wireless comes up often on this forum and as I use a wired connection with a wifi router, I've never needed to worry about the issue. Anyway, if you would like to try the blacklist ipv6 method here's what you do
sudo gedit /etc/modprobe.d/blacklist
At the bottom of the list type
blacklist ipv6
Save, reboot and see if that works (I know of many instances when it has worked, but there are no guarantees!)
You can reverse it by getting the gedit list back and deleting what you've added and saving again.
If this doesn't work, you will have to wait for someone is knowledgeable about wireless.

---

### Post by doorknob60 on 2008-03-14
Type this in the terminal and post the output so we know what wireless card you have:
```
lspci
```

---

### Post by Helios1276 on 2008-03-14
My wired connection to the modem works fine( I'm on it now).

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 21)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by Victormd on 2008-03-14
> **Helios1276 said:**
> ..with the ATI its low resolution, no 3d effects etc, i cant change the desktop effects level for example

Have you installed the restricted drivers? You will only be able to set the 3d effects through the restricted drivers. Furthermore, you'll have to install the fgrlx driver:

```
sudo apt-get update
sudo apt-get install linux-restricted-modules-generic restricted-manager
```

Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver".

```
sudo apt-get install xserver-xgl
```

then you'll need to install the Compiz Fusion effects manager

```
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0
```

reboot and you should be set to go...

---

### Post by Helios1276 on 2008-03-15
ok, I used Envy and everything seems to be working so I'm gonna try compiz now and see how I get on, thanks to everyone who dragged me to this point! :popcorn:

---

### Post by Helios1276 on 2008-03-15
Compiz working great!! yaaay! ..though if someone can explain how to do stuff ..i.e the cube ???

---

### Post by bumanie on 2008-03-15
This site will help
[http://www.stumbleupon.com/demo/?review=1#url=http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://www.stumbleupon.com/demo/?review=1#url=http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

---

### Post by Helios1276 on 2008-03-15
Ok , everything going smooth bar the wireless but i'd say that belongs in a new thread. Cheers guys for all the help!

---

